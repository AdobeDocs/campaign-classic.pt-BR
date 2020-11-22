---
solution: Campaign Classic
product: campaign
title: Introdução às atualizações de compilação
description: Saiba mais sobre as principais etapas para atualizar para uma nova compilação
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2355'
ht-degree: 3%

---


# Atualização de uma build{#performing-a-build-upgrade}

Esta seção fornecerá uma apresentação detalhada sobre o processo de atualização e as etapas para identificar e resolver conflitos.

A atualização da construção deve ser efetuada com cautela, os seus impactos devem ser devidamente considerados antes e o procedimento deve ser concluído com um elevado nível de disciplina. Para garantir uma atualização bem-sucedida, verifique se somente usuários especialistas executam as etapas descritas abaixo. Além disso, recomendamos entrar em contato com o Atendimento [ao cliente do](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) Adobe antes de iniciar qualquer atualização.

Os seguintes pré-requisitos são necessários:

* Noções básicas da arquitetura de Campanhas
* Conhecimento do lado dos sistemas e do servidor
* Direitos administrativos e permissões

Você pode encontrar mais informações nestas seções: [Atualizando o Adobe Campaign](../../production/using/upgrading.md), [migrando para uma nova versão](../../migration/using/about-migration.md).

Para instâncias hospedadas e híbridas, você deve solicitar a atualização da compilação para a equipe de Operações Técnicas do Adobe. Para obter mais informações, consulte a seção Perguntas frequentes na parte inferior se esta página estiver disponível. Consulte também as Perguntas frequentes sobre a atualização da [compilação](../../platform/using/faq-build-upgrade.md).

## Preparar a atualização

![](assets/do-not-localize/icon_planification.png)

Antes de iniciar a atualização da compilação, você deve executar uma preparação completa, conforme descrito abaixo.
Quando o sistema estiver pronto para ser atualizado, uma atualização de compilação levará **pelo menos** 2 horas.

O processo de atualização de build requer os seguintes recursos:

* um arquiteto de Adobe - para entender as estruturas de banco de dados (schemas prontos para uso e schemas adicionais que foram adicionados, designs de campanha e qualquer funcionalidade de caminho crítico que deve ser iniciada e testada em uma ordem específica).
* um gerente de projeto - Caso a atualização da compilação envolva várias instâncias diferentes (produção, armazenamento temporário, teste) e outros servidores e aplicativos de terceiros (bancos de dados, sites SFTP, provedores de serviço de mensagens), a existência de um gerente de projeto para coordenar todos os testes é considerada uma prática recomendada.
* um administrador da Adobe Campaign - seu administrador conhece a configuração do servidor, incluindo, mas não se limitando a: segurança, layout de pasta, relatórios e requisitos de importação\exportação. Não realize uma atualização de compilação sem o administrador.
* operador Adobe Campaign (usuário de marketing) - uma atualização bem-sucedida depende da capacidade do usuário de executar suas tarefas diárias com sucesso. Por esse motivo, sempre inclua pelo menos um de seus operadores diários em seus testes dos servidores atualizados.

### Planejamento

Estes são os principais pontos sobre como planejar uma atualização de compilação:

1. Reserve pelo menos 2 horas para a atualização.
1. Distribua os detalhes de contato para a equipe de Adobe e clientes.
1. Para instâncias hospedadas: A equipe de Adobe e de clientes coordenará o tempo da atualização e quem será executado.
1. Para instâncias locais: a equipe do cliente gerencia todo o processo - se for necessário assistência em testes de workflows personalizados e lógica do delivery, os serviços de consultoria devem ser fornecidos.
1. Determine e confirme para qual versão do Adobe Campaign você deseja atualizar - consulte as notas [de versão da](../../rn/using/rn-overview.md)Adobe Campaign Classic.
1. Confirme a posse dos executáveis de atualização.

### Pessoas-chave

O processo de atualização da compilação requer que as seguintes pessoas estejam envolvidas:

* arquiteto Adobe: para arquiteturas hospedadas ou híbridas, o arquiteto deve coordenar-se com o Adobe Campaign Client Care.

* Gerenciador de projetos:
   * para instalações no local: o Líder de projeto interno do cliente lidera a atualização e gerencia os testes de ciclo de vida.

   * para instalação hospedada: a equipe de hospedagem fará uma parceria com a equipe de Atendimento ao cliente da Adobe Campaign e com o cliente para coordenar a linha do tempo de atualização para todas as instâncias.

* Administrador da Adobe Campaign:
   * para instalações no local: o administrador executa a atualização.

   * para instalações hospedadas: a equipe de hospedagem realiza a atualização.

* Operador do Adobe Campaign\usuário de marketing: o operador efetua testes em instâncias de desenvolvimento, teste e produção.

### Preparar a atualização da compilação

Antes de iniciar a atualização da compilação, os clientes locais precisam executar a seguinte preparação:

1. Certifique-se de que qualquer trabalho de desenvolvimento possa ser exportado antes da atualização, exportar como pacotes.

1. Execute um backup completo dos bancos de dados para todas as instâncias dos ambientes de origem e público alvo.

1. Obtenha a versão mais recente do arquivo [de configuração do](../../installation/using/the-server-configuration-file.md)servidor.

1. Baixe a versão mais recente. [Saiba mais sobre o Centro](https://docs.adobe.com/content/help/pt-BR/experience-cloud/software-distribution/home.html)de download.

Você também precisa saber todas as linhas [de comando](../../installation/using/command-lines.md) úteis antes de iniciar uma atualização de compilação:

* **nlserver pdump**: listas executando processos
* **nlserver pdump -who**: Sessões de cliente ativas do lista
* **monitor nlserver -missing**: Propriedades ausentes do lista
* **start nlserver process@instanceName**: start um processo
* **nlserver stop process@instanceName**: interrompe um processo
* **nlserver restart process@instanceName**: reinicia um processo
* **desligamento** do nlserver: interrompe todos os processos de Campanha
* **nlserver watchdog -svc**: start o watchdog (somente UNIX)

## Executar a atualização

![](assets/do-not-localize/icon_process.png)

Os procedimentos abaixo são executados apenas por clientes **locais** . Para os clientes hospedados, é feito pela equipe de hospedagem. Para atualizar o Adobe Campaign para uma nova compilação, o procedimento detalhado é descrito abaixo.

### Duplicado do ambiente

Veja como você duplicado um ambiente Adobe Campaign para restaurar um ambiente de origem a um ambiente público alvo, resultando em dois ambientes de trabalho idênticos.

Para fazer isso, siga as etapas abaixo:

1. Crie uma cópia dos bancos de dados em todas as instâncias no ambiente de origem.

1. Restaure essas cópias em todas as instâncias do ambiente do público alvo.

1. Execute o script de cauterização **nms:congelamentoInstance.js** no ambiente do público alvo antes de iniciá-lo. Isso interromperá todos os processos interagindo com o exterior: registros, rastreamento, delivery, workflows da campanha etc.

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. Verifique a cauterização da seguinte forma:

   * Verifique se a única peça do delivery é aquela que a ID está definida como **0**:

      ```
      SELECT * FROM neolane.nmsdeliverypart;
      ```

   * Verifique se a atualização de status do delivery está correta:

      ```
      SELECT iSate, count(*) FROM neolane.nmsdeliveryGroup By iProd;
      ```

   * Verifique se a atualização do status do fluxo de trabalho está correta:

      ```
      SELECT iState, count (*) FROM neolane.xtkworkflowGROUP BY iState;
      SELECT iStatus, count (*) FROM neolane.xtkworkflowGROUP BY iStatus;
      ```

### Serviços de desligamento

Para substituir todos os arquivos pela nova versão, é necessário que todas as instâncias do nlserverservice sejam desligadas.

1. Desligue os seguintes serviços:

   * Serviços Web (IIS): **iisreset /stop**
   * Serviço Adobe Campaign: **net stop nlserver6**

   >[!NOTE]
   >
   >Certifique-se de que o servidor de redirecionamento (webmdl) esteja parado, para que o arquivo nlsrvmod.dll usado pelo IIS possa ser substituído pela nova versão.

1. Para validar se nenhum tarefa está ativo, execute o comando **nlserver pdump** . Se não houver tarefas, a saída deverá ser semelhante ao seguinte:

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. Verifique o Gerenciador de Tarefas do Windows para confirmar se todos os processos foram interrompidos.

### Atualizar o aplicativo Adobe Campaign Server

1. Execute o arquivo **Setup.exe** . Se precisar baixar esse arquivo, acesse [o Centro](https://docs.adobe.com/content/help/pt-BR/experience-cloud/software-distribution/home.html)de download.

1. Selecione o modo de instalação: **Atualizar** ou **reparar**.

1. Clique em **Next**.

1. Clique em **Concluir**: o programa de instalação copia os novos arquivos.

1. Quando a operação estiver concluída, clique em **Concluir**.

### Sincronizar recursos

1. Abra a linha de comando.

1. Execute **nlserver config -post-upgrade -allinnesse** procedimento:

   * Sincronizar recursos
   * Atualizar schemas
   * Atualizar o banco de dados

   >[!NOTE]
   >
   >Essa operação só deve ser executada uma vez e somente em um servidor de aplicativos nnnserverweb.

   Para sincronizar apenas um banco de dados, execute o seguinte comando:

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. Verifique se a sincronização gerou erros ou avisos.

### Reiniciar serviços

Os seguintes serviços precisam ser reiniciados:

* Serviços Web (IIS): **issreset /start**
* Serviço Adobe Campaign: **start net nlserver6**

### Atualização de consoles cliente

Na máquina em que o servidor de aplicativos Adobe Campaign está instalado (nlserverweb), baixe e copie o arquivo:

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```


Na próxima vez que os consoles cliente forem conectados, uma janela informará os usuários sobre a disponibilidade de uma nova atualização e oferta a possibilidade de baixá-la e instalá-la.

### Tarefas adicionais específicas

Algumas configurações exigem tarefas adicionais específicas para atualizar para uma nova compilação.

#### Mensagens transacionais

Quando a opção Mensagens transacionais (Centro de mensagens) estiver ativada na instância da Campanha, você precisará executar estas etapas adicionais para atualizar:

1. Atualize o servidor de produção do Centro de mensagens para a versão escolhida.
1. Execute os scripts pós-atualização.
1. Execute testes e verifique se os e-mails foram recebidos com êxito por meio da instância de produção do Centro de mensagens.
1. Atualize clientes e limpe o cache.
1. Exportar pacotes:
   * Exportar pacotes usando a ferramenta de exportação de pacote do cliente
   * Importar pacote de schemas
   * Desconectar e reconectar cliente
   * Atualizar banco de dados
   * Desconectar e reconectar
   * Importar pacote de administração
   * Importar pacote de conteúdo
   * Importar pacote de Gestão de conteúdo
   * Desconectar e reconectar
   * Execute uma verificação rápida de integridade dos workflows

1. Publicar modelos do Centro de mensagens para garantir que a interface entre servidores e a instância do Centro de mensagens esteja funcionando.
1. Execute testes para garantir que os e-mails sejam recebidos com êxito por meio da instância de produção do Centro de mensagens.
1. Execute testes de fluxo de trabalho na produção para garantir que os delivery sejam recebidos.

#### Mid-sourcing

No contexto de um ambiente mid-sourcing, é necessário executar estas etapas adicionais para atualizar:

1. Entre em contato com o Atendimento [ao cliente do](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) Adobe para coordenar a atualização do servidor do Mid-sourcing.
1. Valide se a versão foi atualizada executando um link de teste. Por exemplo:

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>O servidor Mid-sourcing sempre deve executar a mesma versão (ou mais recente) dos servidores de marketing.


## Em caso de conflitos

### Identificar conflitos

É necessário verificar o resultado da sincronização. Este procedimento só é executado por clientes locais. Para os clientes hospedados, é feito pela equipe de hospedagem. Há duas maneiras de visualização do resultado da sincronização:

Na interface de linha de comando, os erros são materializados por uma divisa tripla &#39;>>>&#39; e a sincronização é interrompida automaticamente. Os avisos são materializados por uma divisa de duplo &#39;>>&#39; e devem ser resolvidos assim que a sincronização for concluída. No final da pós-atualização, um resumo é exibido no prompt de comando. Pode parecer com isto:

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

Se o aviso disser respeito a um conflito de recursos, é necessário prestar atenção ao usuário para resolvê-lo.

O arquivo **pós-upgrade_ServerVersionNumber_TimeOfPostupgrade.log** contém o resultado da sincronização. Está disponível por padrão no seguinte diretório: **installationDirectory/var/instanceName/post-upgrade**. Erros e avisos são indicados pelos atributos de erro e aviso.

### Analisar conflitos

**Como se encontra um conflito?**

Os conflitos podem ser encontrados no postupgrade.log no servidor em questão ou na interface do cliente da Campanha (Administração > Configuração > Gerenciamento de pacotes > Editar conflitos).

O documento com o identificador &quot;stockOverview&quot; e o tipo &quot;nms:webApp&quot; estão em conflito com a nova versão.

Se um conflito for encontrado, verifique se as seguintes condições correspondem:

* O objeto foi modificado ou personalizado pelo cliente?
* O objeto mudou no produto?

Se nenhuma dessas condições se aplicar, isso é falso positivo. Se ambas as condições se aplicarem, foi encontrado um verdadeiro conflito.

**O objeto foi modificado pelo cliente?**

1. Identifique o objeto em conflito.
1. Pergunte ao cliente se ele modificou o objeto.
1. Há algo incomum com o objeto?
1. A última data modificada está definida no código do objeto?
1. Examine o código XML do conflito para obter os atributos &quot;_contact&quot;. Parece uma personalização?

**O objeto foi alterado na nova compilação?**

1. Algum &quot;suspeito comum&quot;? Aplicativos ou relatórios da Web incorporados (por exemplo: &#39;deliveryValidation&#39;, &#39;deliveryOverview&#39;, &#39;budget&#39;).
1. Examine os registros de alterações para verificar se há atualizações.
1. Pergunte aos especialistas da Adobe Campaign.
1. Execute um &quot;diff&quot; no código.

### Resolver um conflito

Para resolver conflitos, aplique o seguinte processo:

1. No Adobe Campaign explorer, vá até **Administração > Configuração > Gerenciamento de pacotes > Editar conflitos**.

1. Selecione o conflito que deseja resolver na lista.
Há três opções para resolver conflitos: **Aceite a nova versão**, **Mantenha a versão** atual, **Mescle o código (e declare como resolvido)**, **Ignore o conflito (não recomendado)**.

**Quando posso aceitar a nova versão?**

* Se quiser os recursos padrão.
* Se você não tiver personalizações (todas as personalizações serão removidas)

**Quando posso manter a versão atual?**

* Se você tiver personalizações
* Se você não quiser unir
* Se você não precisar de correções no objeto em conflito na atualização

**Quando realizar uma fusão?**

* Somente formulários, relatórios e aplicativos da Web podem ser mesclados.
* Algumas mesclagens secundárias podem ser resolvidas sem entender o código.
* As mesclagens mais complexas devem ser realizadas por alguém com habilidades e habilidades apropriadas.
* Consulte [Realizar uma mesclagem](#perform-a-merge).

**E se eu ignorar os conflitos?**

* O conflito continuará
* O objeto não será atualizado
* Impactos a longo prazo: incompatibilidades de versão, o cliente não se beneficiará com correções de erros.

>[!IMPORTANT]
>É altamente recomendável resolver conflitos.


### Executar uma mesclagem{#perform-a-merge}

Há diferentes tipos de mesclagem:

1. Fuga fácil: os elementos personalizados e novos são pequenos e não estão relacionados, e não há necessidade de codificação.
1. Nenhuma alteração: aceitar nova versão, somente a data da última atualização alterada, somente comentários, guias, espaços ou novas linhas. Exemplo: salvamento acidental.
1. Alterações triviais: apenas uma linha mudou. Exemplo: xpathToLoad
1. Mesclagem complexa: quando a codificação for necessária. São necessárias competências de desenvolvimento. Consulte [Mesclagens](#complex-merges)complexas.

#### Como se fundir?

1. Obtenha as três versões: a versão original, a nova versão e a versão personalizada.
1. Execute um &quot;diff&quot; entre as versões original e nova.
1. Isole as alterações.
1. Se não houver alterações, resolva mantendo a versão atual.

#### Onde encontrar o código?

1. O código incorporado é armazenado em arquivos XML na pasta datakit. Encontre o arquivo XML que corresponde ao objeto em conflito. Exemplo: installationDirectory\datakit\nms\fra\form\recipient.xml
1. Recuperar a versão original: por meio do centro [de](https://docs.adobe.com/content/help/pt-BR/experience-cloud/software-distribution/home.html) download ou de outra instalação não atualizada do produto.
1. Recuperar a nova versão: através do Centro de [download](https://docs.adobe.com/content/help/pt-BR/experience-cloud/software-distribution/home.html) ou dos arquivos instalados do cliente.
1. Recuperar a versão personalizada: recupere o código-fonte do objeto no cliente da Campanha.

### Como fazer um diferencial?

1. Instale um editor de texto ou mesclagem, por exemplo, Bloco de notas ++, AraxisMerge, WinMerge.
1. Abra o arquivo original e o novo arquivo no editor.
1. Execute o diff (compare os dois arquivos).
1. Identifique quaisquer diferenças.

### Como se fundir?

1. Start da versão personalizada.
1. Aplique as alterações.
1. Resolva o conflito declarando-o resolvido.
1. Verifique se há não regressões.

Se você optar por resolver o conflito manualmente, proceda da seguinte forma:

1. Na seção inferior da janela, procure por **_conflito_cadeia_** para localizar as entidades com conflitos. A entidade instalada com a nova versão contém o novo argumento, a entidade que corresponde à versão anterior contém o argumento personalizado.
1. Exclua a versão que não deseja manter. Exclua a sequência de caracteres de **_conflito_argumento_** da entidade que você está mantendo.
1. Vá para o conflito que você resolveu. Clique no ícone **Ações** e selecione **Declarar como resolvido**.
1. Salve as alterações: o conflito está agora resolvido.

#### Mesclagens complexas{#complex-merges}

1. Entenda o que a alteração faz: faça engenharia reversa das alterações, examine os registros de alterações e acompanhe os especialistas da Adobe Campaign.
1. Decida o que fazer com a mudança.
1. Entenda o que as personalizações fazem: engenharia reversa das alterações

Estas são as etapas para executar uma mesclagem complexa:

1. Copiar bits de código do conjunto de alterações
1. Colar na versão personalizada
1. Ensaio de não regressão da personalização
1. Teste de função das alterações
1. Executar teste de aceitação do usuário
1. Executar no ambiente de teste


>[!IMPORTANT]
>Habilidades de desenvolvimento são necessárias para realizar mesclagens complexas.


**Tópicos relacionados**

* [Perguntas frequentes de atualização de build](../../platform/using/faq-build-upgrade.md)
* [Notas de versão do Campaign Classic ](../../rn/using/rn-overview.md)
* [Opções de ajuda e suporte para Campaign Classic](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support-req)
* [Programa Gold Standard](https://helpx.adobe.com/br/campaign/kb/gold-standard.html)