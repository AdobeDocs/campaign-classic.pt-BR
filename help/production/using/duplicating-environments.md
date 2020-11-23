---
solution: Campaign Classic
product: campaign
title: Ambientes duplicados
description: Ambientes duplicados
audience: production
content-type: reference
topic-tags: data-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1289'
ht-degree: 2%

---


# Ambientes duplicados{#duplicating-environments}

## Introdução {#introduction}

### Visão geral {#overview}

>[!IMPORTANT]
>
>Se você não tiver acesso ao servidor e ao banco de dados (ambientes hospedados), não será possível executar os procedimentos descritos abaixo. Por favor, entre em contato com a Adobe.

O uso do Adobe Campaign requer a instalação e configuração de um ou mais ambientes: desenvolvimento, teste, pré-produção, produção, etc.

Cada ambiente contém uma instância do Adobe Campaign e cada instância do Adobe Campaign está vinculada a um ou mais bancos de dados. O servidor de aplicativos pode executar um ou mais processos: quase todos têm acesso direto ao banco de dados da instância.

Esta seção detalha os processos a serem aplicados ao duplicado de um ambiente Adobe Campaign, isto é, para restaurar um ambiente de origem para um ambiente de público alvo, resultando em dois ambientes de trabalho idênticos.

Para fazer isso, siga as etapas abaixo:

1. Criar uma cópia dos bancos de dados em todas as instâncias do ambiente de origem,
1. Restaure essas cópias em todas as instâncias do ambiente do público alvo,
1. Execute o script de cauterização **nms:congelamentoInstance.js** no ambiente do público alvo antes de iniciá-lo.

   Esse processo não afeta os servidores e suas configurações.

   >[!NOTE]
   >
   >No contexto do Adobe Campaign, uma **cauterização** combina ações que permitem interromper todos os processos interagindo com o exterior: registros, rastreamento, delivery, workflows da campanha etc.\
   >Essa etapa é necessária para evitar a entrega de mensagens várias vezes (uma vez do ambiente nominal e outra do ambiente duplicado).

   >[!IMPORTANT]
   >
   >Um ambiente pode conter várias instâncias. Cada instância da Adobe Campaign está sujeita a um contrato de licença. Verifique seu contrato de licença para ver quantos ambientes você pode ter.\
   >O procedimento abaixo permite que você transfira um ambiente sem afetar o número de ambientes e instâncias que você instalou.

### Antes do seu start {#before-you-start}

>[!IMPORTANT]
>
>Recomendamos executar um backup completo dos bancos de dados para todas as instâncias dos ambientes de origem e público alvo antes de iniciar o processo de transferência. Assim, se ocorrer um problema, você poderá restaurar os backups e retornar à configuração inicial.

Para que esse processo funcione, os ambientes de origem e de público alvo devem ter o mesmo número de instâncias, a mesma finalidade (instância de marketing, instância de delivery) e configurações semelhantes. A configuração técnica deve estar em conformidade com os pré-requisitos de software. Os mesmos componentes devem ser instalados em ambos os ambientes.

## Implementação {#implementation}

### Procedimento de transferência {#transfer-procedure}

Esta seção o ajudará a entender as etapas necessárias para transferir um ambiente de origem para um ambiente de público alvo por meio de um estudo de caso: nosso objetivo aqui é restaurar um ambiente de produção (instância **prod** ) para um ambiente de desenvolvimento (instância **dev** ) para trabalhar em um contexto o mais próximo possível da plataforma &#39;live&#39;.

As etapas a seguir devem ser executadas com muito cuidado: alguns processos ainda podem estar em andamento quando os bancos de dados do ambiente de origem são copiados. A cauterização (etapa 3 abaixo) impede que as mensagens sejam enviadas duas vezes e mantém a consistência dos dados.

>[!IMPORTANT]
>
>* O procedimento a seguir é válido na linguagem PostgreSQL. Se a linguagem SQL for diferente (Oracle, por exemplo), os query SQL devem ser adaptados.
>* Os comandos abaixo se aplicam no contexto de uma instância de **prod** e uma instância **dev** em PostgreSQL.
>



### Etapa 1 - Faça um backup dos dados do ambiente de origem (prod) {#step-1---make-a-backup-of-the-source-environment--prod--data}

Copiar os bancos de dados

Start copiando todos os bancos de dados de ambientes de origem. A operação depende do mecanismo de banco de dados e é da responsabilidade do administrador do banco de dados.

Em PostgreSQL, o comando é:

```
pg_dump mydatabase > mydatabase.sql
```

### Etapa 2 - Exportar a configuração do ambiente do público alvo (dev) {#step-2---export-the-target-environment-configuration--dev-}

A maioria dos elementos de configuração são diferentes para cada ambiente: conta externa (mid-sourcing, roteamento, etc.), opções técnicas (nome da plataforma, ID do banco de dados, endereços de email e URLs padrão, etc.).

Antes de salvar o banco de dados de origem no banco de dados do público alvo, é necessário exportar a configuração de ambiente do público alvo (dev). Para fazer isso, exporte o conteúdo dessas duas tabelas: **xtkoption** e **nmsextaccount**.

Essa exportação permite manter a configuração dev e atualizar apenas os dados dev (workflows, modelos, Aplicações web, recipient etc.).

Para fazer isso, execute uma exportação de pacote para os dois elementos a seguir:

* Exporte a tabela **xtk:option** para um arquivo &#39;options_dev.xml&#39;, sem os registros com os seguintes nomes internos: &#39;WdbcTimeZone&#39;, &#39;NmsServer_LastPostUpgrade&#39; e &#39;NmsBroadcast_RegexRules&#39;.
* Em um arquivo &#39;extaccount_dev.xml&#39;, exporte a tabela **nms:extAccount** para todos os registros cuja ID não seja 0 (@id &lt;> 0).

Verifique se o número de opções/contas exportadas é igual ao número de linhas a serem exportadas em cada arquivo.

>[!NOTE]
>
>O número de linhas para exportar em uma exportação de pacote é de 1000 linhas. Se o número de opções ou contas externas for superior a 1000, você deverá realizar várias exportações.
> 
>Para saber mais, consulte [esta seção](../../platform/using/working-with-data-packages.md#exporting-packages).

>[!NOTE]
>
>Quando a tabela nmsextaccount é exportada, as senhas relacionadas às contas externas (por exemplo, senhas para Mid-sourcing, Execução do centro de mensagens, SMPP, IMS e outras contas externas) não são exportadas. Verifique se você tem acesso às senhas corretas antecipadamente, pois elas podem precisar ser digitadas novamente depois que as contas externas forem importadas de volta para o ambiente.

### Etapa 3 - Parar o ambiente do público alvo (dev) {#step-3---stop-the-target-environment--dev-}

Você precisa parar os processos da Adobe Campaign em todos os servidores de ambientes de públicos alvos. Esta operação depende do seu sistema operacional.

Você pode interromper todos os processos, ou apenas aqueles que gravam no banco de dados.

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
>No Windows, o processo **webmdl** ainda pode estar ativo sem afetar outras operações.

Você também pode verificar se nenhum processo do sistema ainda está em execução.

Para fazer isso, realize o seguinte processo:

* No Windows: abra o gerenciador **de** Tarefas e verifique se não há processos **nlserver.exe** .
* No Linux: execute os **ps aux | grep nlserver** e verifique se não há processos **nlserver** .

### Etapa 4 - Restaurar os bancos de dados no ambiente do público alvo (dev) {#step-4---restore-the-databases-in-the-target-environment--dev-}

Para restaurar os bancos de dados de origem no ambiente do público alvo, use o seguinte comando:

```
psql mydatabase < mydatabase.sql
```

### Etapa 5 - Cauterizar o ambiente do público alvo (dev) {#step-5---cauterize-the-target-environment--dev-}

Para evitar disfuncionamentos, os processos vinculados ao envio do delivery e à execução do fluxo de trabalho não devem ser executados automaticamente quando o ambiente do público alvo for ativado.

Para fazer isso, execute o seguinte comando:

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### Etapa 6 - Verifique a precaução {#step-6---check-cauterization}

1. Verifique se a única peça de entrega é aquela cuja ID está definida como 0:

   ```
   SELECT * FROM neolane.nmsdeliverypart;
   ```

1. Verifique se a atualização de status do delivery está correta:

   ```
   SELECT iState, count(*) FROM neolane.nmsdelivery GROUP BY iState;
   ```

1. Verifique se a atualização do status do fluxo de trabalho está correta:

   ```
   SELECT iState, count(*) FROM neolane.xtkworkflow GROUP BY iState;
   SELECT iStatus, count(*) FROM neolane.xtkworkflow GROUP BY iStatus;
   ```

### Etapa 7 - Reiniciar o processo Web do ambiente do público alvo (dev) {#step-7---restart-the-target-environment-web-process--dev-}

No ambiente do público alvo, volte a start dos processos Adobe Campaign para todos os servidores.

>[!NOTE]
>
>Antes de reiniciar o Adobe Campaign no ambiente **dev** , você pode aplicar um procedimento de segurança adicional: start somente o módulo **da Web** .
>  
>Para fazer isso, edite o arquivo de configuração da sua instância (**config-dev.xml**) e adicione o caractere &quot;_&quot; antes das opções autoStart=&quot;true&quot; para cada módulo (mta, stat etc.).

Execute o seguinte comando para start do processo da Web:

```
nlserver start web
```

Use o seguinte comando para verificar se apenas o processo da Web foi iniciado:

```
nlserver pdump
```

Verifique esse acesso às funções do console do cliente.

### Etapa 8 - Importar opções e contas externas para o ambiente do público alvo (dev) {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!IMPORTANT]
>
>Somente o processo da Web deve ser iniciado nesta etapa. Se esse não for o caso, pare outros processos em execução antes de continuar

Acima de tudo, verifique os valores de várias linhas dos arquivos antes de importá-los (por exemplo: &#39;NmsTracking_Pointer&#39; para a tabela de opções e as contas de delivery ou mid-sourcing para a tabela de conta externa)

Para importar a configuração do banco de dados do ambiente do público alvo (dev):

1. Abra o console de administração do banco de dados e expurgue as contas externas (table nms:extAccount) cuja ID não seja 0 (@id &lt;> 0).
1. No console do Adobe Campaign, importe o pacote options_dev.xml criado anteriormente pela funcionalidade do pacote de importação.

   Verifique se as opções foram atualizadas no **[!UICONTROL Administration > Platform > Options]** nó.

1. No console do Adobe Campaign, importe o extaccount_dev.xml criado anteriormente pela funcionalidade do pacote de importação

   Verifique se as bases de dados externas foram realmente importadas no **[!UICONTROL Administration > Platform > External accounts]** .

### Etapa 9 - Reiniciar todos os processos e alterar usuários (dev) {#step-9---restart-all-processes-and-change-users--dev-}

Para start dos processos do Adobe Campaign, use os seguintes comandos:

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

Altere os usuários para localizar os usuários que já existiam na plataforma dev.
