---
product: campaign
title: Ambientes duplicados
description: Ambientes duplicados
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 2c933fc5-1c0a-4c2f-9ff2-90d09a79c55a
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1289'
ht-degree: 2%

---

# Ambientes duplicados{#duplicating-environments}



## Introdução {#introduction}

### Visão geral {#overview}

>[!IMPORTANT]
>
>Se você não tiver acesso ao servidor e ao banco de dados (ambientes hospedados), não será possível executar os procedimentos descritos abaixo. Entre em contato com o Adobe.

O uso do Adobe Campaign requer a instalação e a configuração de um ou mais ambientes: desenvolvimento, teste, pré-produção, produção etc.

Cada ambiente contém uma instância do Adobe Campaign e cada instância do Adobe Campaign está vinculada a um ou mais bancos de dados. O servidor de aplicativos pode executar um ou mais processos: quase todos eles têm acesso direto ao banco de dados da instância.

Esta seção detalha os processos a serem aplicados para duplicar um ambiente Adobe Campaign, ou seja, restaurar um ambiente de origem para um ambiente de destino, resultando em dois ambientes de trabalho idênticos.

Para fazer isso, siga as etapas abaixo:

1. Criar uma cópia dos bancos de dados em todas as instâncias no ambiente de origem,
1. Restaurar essas cópias em todas as instâncias do ambiente de destino,
1. Execute o **nms:freezeInstance.js** script de cauterização no ambiente do target antes de iniciá-lo.

   Esse processo não afeta os servidores e suas configurações.

   >[!NOTE]
   >
   >No contexto do Adobe Campaign, uma **cauterização** O combina ações que permitem interromper a interação de todos os processos com o exterior: logs, rastreamento, deliveries, workflows da campanha etc.\
   >Essa etapa é necessária para evitar a entrega de mensagens várias vezes (uma vez do ambiente nominal e outra do ambiente duplicado).

   >[!IMPORTANT]
   >
   >Um ambiente pode conter várias instâncias. Cada instância do Adobe Campaign está sujeita a um contrato de licença. Verifique o contrato de licença para ver quantos ambientes você pode ter.\
   >O procedimento abaixo permite transferir um ambiente sem afetar o número de ambientes e instâncias instalados.

### Antes de começar {#before-you-start}

>[!IMPORTANT]
>
>É altamente recomendável executar um backup completo dos bancos de dados para todas as instâncias dos ambientes de origem e de destino antes de iniciar o processo de transferência. Dessa forma, se ocorrer um problema, você poderá restaurar os backups e retornar à configuração inicial.

Para que esse processo funcione, os ambientes de origem e de destino devem ter o mesmo número de instâncias, a mesma finalidade (instância de marketing, instância de delivery) e configurações semelhantes. A configuração técnica deve estar em conformidade com os pré-requisitos de software. Os mesmos componentes devem ser instalados em ambos os ambientes.

## Implementação {#implementation}

### Procedimento de transferência {#transfer-procedure}

Esta seção ajudará você a entender as etapas necessárias para transferir um ambiente de origem para um ambiente de destino por meio de um estudo de caso: nosso objetivo aqui é restaurar um ambiente de produção (**prod** instância) para um ambiente de desenvolvimento (**dev** instância) para trabalhar em um contexto o mais próximo possível da plataforma &quot;live&quot;.

As etapas a seguir devem ser executadas com muito cuidado: alguns processos ainda podem estar em andamento quando os bancos de dados do ambiente de origem forem copiados. A precaução (etapa 3 abaixo) impede que as mensagens sejam enviadas duas vezes e mantém a consistência dos dados.

>[!IMPORTANT]
>
>* O procedimento a seguir é válido na linguagem PostgreSQL. Se a linguagem SQL for diferente (Oracle, por exemplo), as queries SQL devem ser adaptadas.
>* Os comandos abaixo se aplicam no contexto de um **prod** instância e um **dev** instância no PostgreSQL.
>


### Etapa 1 — fazer backup dos dados do ambiente de origem (prod) {#step-1---make-a-backup-of-the-source-environment--prod--data}

Copiar os bancos de dados

Comece copiando todos os bancos de dados do ambiente de origem. A operação depende do mecanismo de banco de dados e é responsabilidade do administrador do banco de dados.

No PostgreSQL, o comando é:

```
pg_dump mydatabase > mydatabase.sql
```

### Etapa 2 - Exportar a configuração do ambiente de destino (dev) {#step-2---export-the-target-environment-configuration--dev-}

A maioria dos elementos de configuração é diferente para cada ambiente: contas externas (mid-sourcing, roteamento etc.), opções técnicas (nome da plataforma, DatabaseId, endereços de email e URLs padrão etc.).

Antes de salvar o banco de dados de origem no banco de dados de destino, é necessário exportar a configuração do ambiente de destino (dev). Para fazer isso, exporte o conteúdo dessas duas tabelas: **xtkoption** e **nmsextaccount**.

Essa exportação permite manter a configuração de desenvolvimento e atualizar apenas os dados de desenvolvimento (workflows, modelos, aplicativos web, destinatários, etc.).

Para fazer isso, execute uma exportação de pacote para os dois elementos a seguir:

* Exportar o **xtk:option** em um arquivo &#39;options_dev.xml&#39;, sem os registros com os seguintes nomes internos: &#39;WdbcTimeZone&#39;, &#39;NmsServer_LastPostUpgrade&#39; e &#39;NmsBroadcast_RegexRules&#39;.
* Em um arquivo &#39;extaccount_dev.xml&#39;, exporte o **nms:extAccount** tabela para todos os registros cuja ID não é 0 (@id &lt;> 0).

Verifique se o número de opções/contas exportadas é igual ao número de linhas que serão exportadas em cada arquivo.

>[!NOTE]
>
>O número de linhas a serem exportadas em uma exportação de pacote é 1000 linhas. Se o número de opções ou contas externas for superior a 1000, você deverá realizar várias exportações.
> 
>Para obter mais informações, consulte [esta seção](../../platform/using/working-with-data-packages.md#exporting-packages).

>[!NOTE]
>
>Quando a tabela nmsextaccount é exportada, as senhas relacionadas às contas externas (por exemplo, senhas para Mid-sourcing, Message Center Execution, SMPP, IMS e outras contas externas) não são exportadas. Verifique se você tem acesso antecipado às senhas corretas, pois elas podem precisar ser inseridas novamente depois que as contas externas forem importadas de volta para o ambiente.

### Etapa 3 - Parar o ambiente de destino (dev) {#step-3---stop-the-target-environment--dev-}

Você precisa interromper os processos do Adobe Campaign em todos os servidores do ambiente de destino. Essa operação depende do seu sistema operacional.

Você pode interromper todos os processos ou somente aqueles que gravam no banco de dados.

Para interromper todos os processos, use os seguintes comandos:

* No Windows:

   ```
   net stop nlserver6
   ```

* No Linux:

   ```
   /etc/init.d/nlserver6 stop
   ```

Use o seguinte comando para verificar se todos os processos foram interrompidos:

```
nlserver pdump
```

>[!NOTE]
>
>No Windows, a variável **webmdl** O processo ainda pode estar ativo sem afetar outras operações.

Você também pode verificar se nenhum processo do sistema ainda está em execução.

Para fazer isso, realize o seguinte processo:

* No Windows: abra o **Gerenciador de tarefas** e verifique se não há **nlserver.exe** processos.
* No Linux: execute o **ps aux | grep nlserver** e verifique se não há **nlserver** processos.

### Etapa 4 - Restaurar os bancos de dados no ambiente de destino (dev) {#step-4---restore-the-databases-in-the-target-environment--dev-}

Para restaurar os bancos de dados de origem no ambiente de destino, use o seguinte comando:

```
psql mydatabase < mydatabase.sql
```

### Etapa 5 - Preservar o ambiente de destino (dev) {#step-5---cauterize-the-target-environment--dev-}

Para evitar mau funcionamento, os processos vinculados ao envio de delivery e à execução de workflow não devem ser executados automaticamente quando o ambiente de destino é ativado.

Para fazer isso, execute o seguinte comando:

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### Etapa 6 - Verificar cauterização {#step-6---check-cauterization}

1. Verifique se a única parte do delivery é aquela cuja ID está definida como 0:

   ```
   SELECT * FROM neolane.nmsdeliverypart;
   ```

1. Verifique se a atualização do status do delivery está correta:

   ```
   SELECT iState, count(*) FROM neolane.nmsdelivery GROUP BY iState;
   ```

1. Verifique se a atualização do status do workflow está correta:

   ```
   SELECT iState, count(*) FROM neolane.xtkworkflow GROUP BY iState;
   SELECT iStatus, count(*) FROM neolane.xtkworkflow GROUP BY iStatus;
   ```

### Etapa 7 - Reiniciar o processo da Web do ambiente de destino (dev) {#step-7---restart-the-target-environment-web-process--dev-}

No ambiente de destino, reinicie os processos do Adobe Campaign para todos os servidores.

>[!NOTE]
>
>Antes de reiniciar o Adobe Campaign no **dev** ambiente, você pode aplicar um procedimento de segurança adicional: inicie o **web** somente o módulo.
>  
>Para fazer isso, edite o arquivo de configuração da sua instância (**config-dev.xml**), em seguida, adicione o caractere &quot;_&quot; antes das opções autoStart=&quot;true&quot; para cada módulo (mta, stat, etc.).

Execute o seguinte comando para iniciar o processo da Web:

```
nlserver start web
```

Use o comando a seguir para verificar se somente o processo da Web foi iniciado:

```
nlserver pdump
```

Verifique se o acesso às funções do console do cliente está ativado.

### Etapa 8 - Importar opções e contas externas para o ambiente de destino (dev) {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!IMPORTANT]
>
>Somente o processo da Web deve ser iniciado nesta etapa. Se esse não for o caso, pare outros processos em execução antes de continuar

Acima de tudo, verifique os valores de várias linhas dos arquivos antes de importar (por exemplo: &#39;NmsTracking_Pointer&#39; para a tabela de opções e as contas de delivery ou mid-sourcing para a tabela de conta externa)

Para importar a configuração do banco de dados do ambiente de destino (dev):

1. Abra o Admin Console do banco de dados e limpe as contas externas (tabela nms:extAccount) cuja ID não é 0 (@id &lt;> 0).
1. No console do Adobe Campaign, importe o pacote options_dev.xml criado anteriormente por meio da funcionalidade de importação de pacotes.

   Verifique se as opções foram de fato atualizadas no **[!UICONTROL Administration > Platform > Options]** nó.

1. No console do Adobe Campaign, importe o extaccount_dev.xml criado anteriormente por meio da funcionalidade de importação de pacote

   Verifique se os bancos de dados externos foram importados na **[!UICONTROL Administration > Platform > External accounts]** .

### Etapa 9 - Reiniciar todos os processos e alterar usuários (dev) {#step-9---restart-all-processes-and-change-users--dev-}

Para iniciar os processos do Adobe Campaign, use os seguintes comandos:

* No Windows:

   ```
   net start nlserver6
   ```

* No Linux:

   ```
   /etc/init.d/nlserver6 start
   ```

Use o seguinte comando para verificar se os processos foram iniciados:

```
nlserver pdump
```

Altere os usuários para encontrar os usuários que já existiam na plataforma de desenvolvimento.
