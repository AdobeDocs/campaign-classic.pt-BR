---
title: Importação de dados
seo-title: Importação de dados
description: Importação de dados
seo-description: null
page-status-flag: never-activated
uuid: ca2269ad-7cfd-4f27-88be-469445a468bf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: c886bd02-c484-443c-93ca-ca244adbf893
translation-type: tm+mt
source-git-commit: c2c0609619e0cc81444d089850add6dec5de93fd
workflow-type: tm+mt
source-wordcount: '4138'
ht-degree: 87%

---


# Importação de dados{#importing-data}

O Adobe Campaign permite importar dados para o banco de dados de um ou mais arquivos no texto, no formato CSV, TAB ou XML. Esses arquivos são associados a uma tabela (principal ou vinculada) e cada campo do arquivo de origem é associado a um campo do banco de dados. A configuração de importação pode ser salva para reutilização de modo que você possa agendar tarefas de importação que automatizam suas operações de replicação.

>[!NOTE]
>
>É possível importar dados sem mapeá-los com os dados do banco de dados usando a função **[!UICONTROL Import a list]**.
>
>Os dados podem ser usados exclusivamente em workflows por meio do objeto **[!UICONTROL Read list]**. Para obter mais informações, consulte [esta página](../../workflow/using/read-list.md).

![](assets/do-not-localize/how-to-video.png) [Descubra este recurso no vídeo](https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/profile-management/importing-profiles.html)

## Estrutura dos dados a importar {#structure-of-the-data-to-import}

No arquivo de origem, cada linha coincide com um registro. Os dados em registros são separados por delimitadores (espaço, tabulação, caractere etc.). Isso significa que os dados são recuperados no formulário de colunas e cada coluna é associada a um campo do banco de dados.

## Assistente de Importação {#import-wizard}

O assistente de importação permite configurar a importação, definir suas opções (como transformação de dados) e iniciar a execução. É uma série de telas cujo conteúdo depende do tipo de importação (simples ou múltipla) e dos direitos do operador.

>[!NOTE]
>
>Se você utilizar um servidor da Web IIS, uma configuração pode ser necessária para autorizar o upload de arquivos grandes (>28 MB).
>
>Para obter mais informações, consulte [esta seção](../../installation/using/integration-into-a-web-server-for-windows.md#changing-the-upload-file-size-limit).

### Etapa 1 - Escolha do template de importação {#step-1---choosing-the-import-template}

Ao iniciar o assistente de importação, primeiro é necessário selecionar um template. Como exemplo, para configurar a importação de destinatários que receberam um boletim informativo, siga as etapas abaixo:

1. Selecione a pasta **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]**.
1. Clique em **New** e em **Import** para criar o template de importação.

   ![](assets/s_ncs_user_import_wizard01_1.png)

1. Clique na seta à direita do campo **[!UICONTROL Import template]** para selecionar o modelo ou clique em **[!UICONTROL Select link]** para navegar na árvore.

   O modelo nativo é **[!UICONTROL New text import]**. Este template não deve ser modificado, mas você pode duplicá-lo para configurar um novo template dependendo de suas necessidades. By default, import templates are saved in the **[!UICONTROL Profiles and targets > Templates > Job templates]** node.

1. Insira um nome para essa importação no campo **[!UICONTROL Label]**. Você pode adicionar uma descrição.
1. Selecione o tipo de importação no campo apropriado. Há dois tipos possíveis de importação: **[!UICONTROL Simple import]** para importar apenas um arquivo e **[!UICONTROL Multiple import]** para importar vários arquivos em uma única execução.

   For a multiple import, select **[!UICONTROL Multiple import]** from the **[!UICONTROL Import type]** drop-down list in the first screen of the import wizard.

   ![](assets/s_ncs_user_import_wizard01_2.png)

1. Especifique os campos que deseja importar clicando em **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_import_wizard01_3.png)

   Toda vez que um arquivo é adicionado, a tela do assistente **[!UICONTROL File to import]** é exibida. Consulte a seção [Step 2 - Source file selection](#step-2---source-file-selection) e siga as etapas do assistente para definir as opções de importação como para uma importação simples.

   >[!NOTE]
   >
   >Importações múltiplas só devem atender às necessidades específicas e não são recomendadas.

#### Parâmetros avançados {#advanced-parameters}

O link **[!UICONTROL Advanced parameters]** permite acessar as seguintes opções:

* **[!UICONTROL General]** guia

   * **[!UICONTROL Stop execution if there are too many rejects]**

      Essa opção é selecionada por padrão. Você pode desmarcá-la se quiser continuar a executar a importação independentemente do número de rejeições. Por padrão, a execução é interrompida se as primeiras 100 linhas forem rejeitadas.

   * **[!UICONTROL Trace mode]**

      Selecione essa opção para controlar a execução da importação para cada linha.

   * **[!UICONTROL Start the job in a detached process]**

      Essa opção é selecionada por padrão. Permite desanexar a execução da importação para que não afete outras tarefas em andamento no banco de dados.

   * **[!UICONTROL Do not update enumerations]**

      Selecione essa opção para evitar o enriquecimento da lista de valores enumerados no banco de dados. Consulte [Gerenciamento de listas discriminadas](../../platform/using/managing-enumerations.md).

* **[!UICONTROL Variables]** guia

   É possível definir variáveis associadas à tarefa que será acessível nos editores de consulta e campos calculados. Para criar uma variável, clique em **[!UICONTROL Add]** e utilize o editor de variáveis.

   >[!CAUTION]
   >
   >A guia **[!UICONTROL Variables]** é somente para uso de programação do tipo fluxo de trabalho e deve ser configurada apenas por usuários especialistas.

### Etapa 2 - Seleção de arquivo de origem {#step-2---source-file-selection}

O arquivo de origem pode estar no formato de texto (txt, csv, guia, colunas fixas) ou xml.

By default, **[!UICONTROL Upload file on the server]** is selected. Clique na pasta à direita do campo **[!UICONTROL Local file]** para navegar no disco local e selecione o arquivo a ser importado. É possível desmarcar essa opção para inserir o caminho de acesso e o nome do arquivo a ser importado se ele estiver no servidor.

![](assets/s_ncs_user_import_wizard02_1.png)

Quando o arquivo tiver sido especificado, você poderá exibir os respectivos dados na seção inferior da janela clicando em **[!UICONTROL Auto-detect format]**. Essa visualização exibe as 200 primeiras linhas do arquivo de origem.

![](assets/s_ncs_user_import_wizard02_2.png)

Use as opções oferecidas acima desta exibição para configurar a importação. Os parâmetros definidos por meio dessas opções são transferidos para a visualização. As seguintes opções estão disponíveis:

* **[!UICONTROL Click here to change the file format...]** permite que você verifique o formato do arquivo e ajuste a configuração.
* **[!UICONTROL Update on server...]** permite que você transfira o arquivo local para o servidor. This option is available only if **[!UICONTROL Upload file on the server]** is selected.
* **[!UICONTROL Download]** está disponível somente se o arquivo foi carregado no servidor.
* **[!UICONTROL Auto-detect format]** é utilizado para reinicializar o formato da fonte de dados. This option lets you reapply the original formats to data that has been formatted via the **[!UICONTROL Click here to change the file format...]** option.
* O link **[!UICONTROL Advanced parameters]** permite filtrar os dados de origem e acessar as opções avançadas. Nessa tela, é possível importar apenas parte do arquivo. É possível definir um filtro, por exemplo, para importar usuários do tipo ‘Prospecto’ ou &#39;Cliente&#39; de acordo com o valor da linha correspondente. Essas opções devem ser usadas somente por usuários especialistas do JavaScript.

#### Alteração do formato de arquivo {#changing-the-file-format}

The **[!UICONTROL Click here to change the file format...]** option lets you format the data of the source file, and in particular to specify the column separator and the type of data for each field. Essa configuração é executada por meio da seguinte janela:

![](assets/s_ncs_user_import_wizard02_3.png)

Esta etapa permite descrever como os valores dos campos de arquivo devem ser lidos. Por exemplo, as informações de uma data, a Data ou Data + Hora podem ser associadas a um formato (dd/mm/aaaa, mm/dd/aa etc.). Se não correspondem ao formato esperado, os dados de entrada são rejeitados durante a importação.

É possível ver o resultado da configuração na zona de visualização na parte inferior da janela.

Clique em **[!UICONTROL OK]** para salvar a formatação e em **[!UICONTROL Next]** para exibir a próxima etapa.

### Etapa 3 - Mapeamento de campo {#step-3---field-mapping}

Em seguida, você deve selecionar o esquema de destino e mapear os dados de cada coluna em campos no banco de dados.

![](assets/s_ncs_user_import_wizard03_1.png)

* O campo **[!UICONTROL Destination schema]** permite selecionar o esquema no qual os dados serão importados. Essas informações são obrigatórias. Clique no ícone **[!UICONTROL Select link]** para selecionar um dos esquemas existentes. Clique em **[!UICONTROL Edit link]** para exibir o conteúdo da tabela selecionada.
* A tabela central mostra todos os campos definidos no arquivo de origem. Selecione os campos a serem importados para associar um arquivo de destino a eles. Esses campos podem ser mapeados manual ou automaticamente.

   Para mapear um campo manualmente, clique na caixa de seleção para selecionar o campo de origem e clique na segunda coluna para ativar a célula correspondente ao campo selecionado. Em seguida, clique no ícone **[!UICONTROL Edit expression]** para exibir todos os campos da tabela atual. Selecione o campo de destino e clique em **[!UICONTROL OK]** para validar o mapeamento.

   Para associar os campos de origem e de destino automaticamente, clique no ícone **[!UICONTROL Guess the destination fields]** à direita da lista de campos. Os campos propostos podem ser modificados se necessário.

   >[!CAUTION]
   >
   >O resultado desta operação deve sempre ser validado antes de você prosseguir para a próxima etapa.

* É possível aplicar uma transformação aos campos importados. Para fazer isso, clique na célula da coluna **[!UICONTROL Transformation]** relacionada ao campo e selecione a transformação a ser aplicada.

   ![](assets/s_ncs_user_import_wizard03_2.png)

   >[!CAUTION]
   >
   >A transformação é aplicada no momento da importação. Se as restrições no campo de destino tiverem sido definidas, no entanto (no exemplo acima, no campo @lastname), essas restrições terão prioridade.

* Pode-se adicionar campos calculados usando o ícone apropriado, localizado à direita da tabela central. Os campos calculados permitem executar transformações complexas, adicionar colunas virtuais ou mesclar os dados de várias colunas. Consulte as seções a seguir para obter detalhes sobre as diversas possibilidades.

#### Campos calculados {#calculated-fields}

Os campos calculados são novas colunas adicionadas ao arquivo de origem e calculadas de outras colunas. Os campos calculados podem então ser associados a campos do banco de dados do Adobe Campaign. As operações de reconciliação, no entanto, não são possíveis em campos calculados.

Existem quatro tipos de campos calculados:

* **[!UICONTROL Fixed string]**: o valor do campo calculado é o mesmo para todas as linhas do arquivo de origem. Permite definir o valor de um campo dos registros inseridos ou atualizados. Por exemplo, você pode definir um marcador para &quot;sim&quot; para todos os registros importados.
* **[!UICONTROL String with JavaScript tags]**: o valor do campo calculado é uma string de caracteres que contém comandos JavaScript.
* **[!UICONTROL JavaScript expression]**: o valor do campo calculado é o resultado da avaliação de uma função JavaScript. O valor retornado pode ser um número, uma data etc.
* **[!UICONTROL Enumeration]**: o valor do campo é atribuído de acordo com um valor contido no arquivo de origem. O editor permite especificar a coluna de origem e inserir a lista de valores de enumeração, como no exemplo a seguir:

   ![](assets/s_ncs_user_import_wizard03_3.png)

   A guia **[!UICONTROL Preview]** permite visualizar o resultado da configuração definida. Aqui, a coluna **[!UICONTROL Subscription]** foi adicionada. O valor é calculado a partir do campo **Status**.

   ![](assets/s_ncs_user_import_wizard03_4.png)

### Etapa 4 - Reconciliação {#step-4---reconciliation}

A etapa de reconciliação do assistente de importação permite definir o modo de reconciliação dos dados do arquivo com os dados existentes no banco de dados e definir as regras de prioridade entre os dados do arquivo e os dados do banco de dados. A janela de configuração tem esta aparência:

![](assets/s_ncs_user_import_wizard04_1.png)

A seção central da tela contém uma árvore com os campos e as tabelas do banco de dados do Adobe Campaign ao qual os dados serão importados.

As opções especiais estão disponíveis para cada nó (tabela ou campo). Quando você clica no nó relacionado na lista, seus parâmetros e uma breve descrição aparecem abaixo. O comportamento definido para cada elemento é exibido na coluna **[!UICONTROL Behavior]** correspondente.

![](assets/s_ncs_user_import_wizard04_2.png)

#### Tipos de operação {#types-of-operation}

Para cada tabela relacionada à importação, deve-se definir o tipo de operação. As seguintes operações estão disponíveis para o elemento principal do banco de dados:

* **[!UICONTROL Update or insertion]**: atualiza o registro se ele existir no banco de dados, caso contrário, o criará.
* **[!UICONTROL Insertion]**: insere registros no banco de dados.
* **[!UICONTROL Update]**: atualiza somente registros existentes (ignora outros registros).
* **[!UICONTROL Reconciliation only]**: procura o registro no banco de dados, mas não executa uma atualização. Por exemplo, permite associar a pasta de destinatários a ser importada de acordo com uma coluna do arquivo sem atualizar os dados nas pastas.
* **[!UICONTROL Deletion]**: permite destruir registros no banco de dados.

As seguintes opções estão disponíveis para cada campo na tabela em relação à importação:

* **[!UICONTROL Update (empty) if source value is empty]**: no evento de uma atualização, o valor no campo removerá o valor do banco de dados se o campo estiver vazio no arquivo de origem. Caso contrário, o campo do banco de dados será mantido.
* **[!UICONTROL Update only if destination is empty]**: o valor do arquivo de origem não substitui o valor no campo do banco de dados, a menos que o campo do banco de dados esteja vazio. Nesse caso, ele recebe o valor do arquivo de origem.
* **[!UICONTROL Update the field only when the record is inserted]**: durante uma operação de atualização ou inserção, somente os registros do arquivo de origem novos serão importados.

>[!NOTE]
>
>A definição de uma chave de reconciliação é sempre **obrigatória**, exceto no caso de inserção sem correção de duplicidade.

#### Chaves de reconciliação {#reconciliation-keys}

Pelo menos uma chave de reconciliação deve ser preenchida para gerenciar a correção de duplicidade.

Uma chave de reconciliação é um conjunto de campos usados para identificar um registro. Por exemplo, para importar destinatários, a chave de conciliação pode ser o número da conta, o campo &quot;email&quot; ou os campos &quot;Last name, First name, Company&quot; etc.

Nesse caso, para descobrir se uma linha de um arquivo corresponde a um destinatário existente no banco de dados, o mecanismo de importação compara os valores do arquivo com aqueles do banco de dados para todos os campos da chave. Quando os campos são específicos de um registro, uma comparação entre os dados de origem e de destino pode ser executada, garantindo a integridade dos dados após a importação. Uma segunda chave de reconciliação pode ser preenchida para a mesma tabela; ela é usada para as linhas cuja primeira chave está vazia.

Evite escolher um campo que possa ser modificado durante a importação; se isso ocorrer, o mecanismo poderá criar registros adicionais.

![](assets/s_ncs_user_import_wizard04_3.png)

>[!NOTE]
>
>Para uma importação de destinatário, o identificador da pasta selecionada é adicionado implicitamente à chave.
>
>A reconciliação é executada assim apenas nessa pasta (a menos que nenhuma pasta seja selecionada).

#### Eliminação de duplicação {#deduplication}

>[!NOTE]
>
>O &quot;duplo&quot; é um item que existe duas ou mais vezes no arquivo a ser importado.
>
>O &quot;duplicado&quot; é um item que existe no arquivo a ser importado e também no banco de dados.

The **[!UICONTROL Management of doubles]** field lets you configure the deduplication of data. A desduplicação emite registros que aparecem várias vezes **no arquivo de origem** (ou nos arquivos de origem no caso de uma importação de múltiplos arquivos), ou seja, linhas para as quais os campos da chave de reconciliação são idênticos.

* O gerenciamento de duplicados no modo **[!UICONTROL Update]** (o modo padrão) não executa a desduplicação. Assim, o último registro tem prioridade (porque atualiza os dados dos registros anteriores). A contagem de duplicados não é executada nesse modo.
* Duplicate management in **[!UICONTROL Ignore]** mode or **[!UICONTROL Reject entity]** excludes duplicates from the import. Nesse caso, nenhum registro é importado.
* No modo **[!UICONTROL Reject entity]**, o elemento não é importado e um erro é gerado nos logs de importação.
* No modo **[!UICONTROL Ignore]**, o elemento não é importado, mas não é mantido nenhum registro do erro. Esse modo permite otimizar o desempenho.

>[!CAUTION]
>
>A desduplicação é executada somente na memória. Portanto, o tamanho de uma importação com desduplicação é limitado. O limite depende de vários parâmetros (capacidade do servidor de aplicação, atividade, número de campos na chave etc.). O tamanho máximo de uma desduplicação é da ordem de um milhão de linhas.

A desduplicação emite um registro presente no arquivo de origem e no banco de dados. It concerns operations with update only (i.e. **[!UICONTROL Update and insertion]** or **[!UICONTROL Update]**). A opção **[!UICONTROL Duplicate management]** permite atualizar ou ignorar o registro se estiver tanto no arquivo de origem quanto no banco de dados. The **[!UICONTROL Update or insert based on origin]** option belongs to the optional module and cannot be used in a standard context.

The options **[!UICONTROL Reject]** and **[!UICONTROL Ignore]** operate as presented above.

#### Comportamento no caso de um erro {#behavior-in-the-event-of-an-error}

A maioria das operações de transferência de dados gera vários tipos de erros (formato de linha incoerente, endereço de email inválido etc.). Todos os erros e avisos gerados pelo mecanismo de importação são armazenados e vinculados à instância de importação.

![](assets/s_ncs_user_import_general_tab.png)

Os detalhes dessas recusas podem ser exibidos por meio da guia **[!UICONTROL Rejects]**.

![](assets/s_ncs_user_import_rejets_tab.png)

Há dois tipos de recusas (o tipo é exibido na coluna **[!UICONTROL Connector]**):

* Recusas dos erros em relação ao conector de texto que ocorrem enquanto a linha de arquivo está sendo processada (campo calculado, análise de dados etc.). Nessa situação, no caso de um erro, a linha inteira é sempre recusada.
* Rejeições do conector do banco de dados são relacionados a erros ocorridos durante a reconciliação ou escrita dos dados no banco de dados. No caso de uma importação para várias tabelas, a rejeição pode ocorrer apenas em uma parte do registro (por exemplo, para uma importação de destinatários e eventos associados, um erro pode impedir a atualização de um evento sem recusar o destinatário).

Na página de reconciliação de dados, é possível definir o campo do tipo de gerenciamento de erros desejado por campo e tabela por tabela.

* **[!UICONTROL Ignore and log a warning]**: todos os campos são importados para o banco de dados, exceto aquele que gerou um erro.
* **[!UICONTROL Reject parent element]**: a linha inteira do registro é rejeitada, não apenas o campo que causou um erro.
* **[!UICONTROL Reject all elements]**: as paradas de importação e todos os elementos do registro são rejeitados.

   ![](assets/s_ncs_user_import_wizard04_4.png)

A árvore na tela de rejeição de uma instância de importação indica quais campos foram rejeitados e onde ocorreram os erros.

Você pode gerar um arquivo contendo esses registros por meio do ícone **[!UICONTROL Export rejects]**:

![](assets/s_ncs_user_import_errors_export.png)

### Etapa 5 - Etapa adicional ao importar destinatários {#step-5---additional-step-when-importing-recipients}

A próxima etapa do assistente de importação permite selecionar ou criar a pasta na qual os dados serão importados, mapear automaticamente destinatários importados com uma lista (nova ou existente) e assinar destinatários a um serviço.

![](assets/s_ncs_user_import_wizard05_1.png)

>[!NOTE]
>
>Esta etapa aparece ao importar os destinatários somente e ao usar a tabela de destinatários padrão do Adobe Campaign (**nms:recipient**).

* Clique nos links **[!UICONTROL Edit]** para selecionar a pasta, a lista ou o serviço ao qual deseja associar ou assinar os recipients.

   1. Importação para uma pasta

      The **[!UICONTROL Edit...]** link of the **[!UICONTROL Import into a folder]** section lets you select or create the folder into which the recipients will be imported. Por padrão, se nenhuma partição for definida, os dados serão importados para a pasta padrão do operador.

      >[!NOTE]
      >
      >A pasta padrão de um operador é a primeira pasta que o operador tem acesso de gravação. Consulte [Gerenciamento de acesso a pastas](../../platform/using/access-management.md#folder-access-management).

      Para selecionar a pasta de importação, clique na seta à direita do campo **[!UICONTROL Folder]** e selecione a pasta correspondente. Você também pode usar o ícone **[!UICONTROL Select link]** para exibir a árvore em uma nova janela ou criar uma nova pasta.

      ![](assets/s_ncs_user_import_wizard05_2.png)

      Para criar uma nova pasta, selecione o nó no qual deseja adicionar uma pasta e clique com o botão direito do mouse. Selecione **[!UICONTROL Create a new 'Recipients' folder]**.

      ![](assets/s_ncs_user_import_wizard05_3.png)

      A pasta é adicionada abaixo do nó atual. Insira o nome da nova pasta, pressione Enter para confirmar, e depois clique em **[!UICONTROL OK]**.

      ![](assets/s_ncs_user_import_wizard05_4.png)

   1. Associar com uma lista

      The **[!UICONTROL Edit...]** link in the **[!UICONTROL Add recipients to a list]** section lets you select or create a list into which the recipients will be imported.

      ![](assets/s_ncs_user_import_wizard05_5.png)

      You can create a new list for these recipients by clicking **[!UICONTROL Select link]**, then **[!UICONTROL Create]**. A criação e o gerenciamento de listas são apresentados em [Criação e gerenciamento de listas](../../platform/using/creating-and-managing-lists.md).

      ![](assets/s_ncs_user_import_wizard05_6.png)

      Você pode decidir adicionar os destinatários aos já presentes em uma lista ou para recriar a lista com os novos destinatários. Nesse caso, se a lista já continha destinatários, eles serão excluídos e substituídos pelos destinatários importados.

   1. Como assinar um serviço

      To subscribe all imported recipients to an information service, click the **[!UICONTROL Edit...]** link of the **[!UICONTROL Subscribe recipients to a service]** section in order to select or create the information service which the recipients will be subscribed to. Você pode selecionar a opção **[!UICONTROL Send a confirmation message]**: o conteúdo desta mensagem é definido no template do delivery associado ao serviço de assinatura.

      ![](assets/s_ncs_user_import_wizard05_7.png)

      É possível criar um novo serviço para esses destinatários clicando em **[!UICONTROL Select link]** e depois no ícone **[!UICONTROL Create]**. O gerenciamento dos serviços de informação é apresentado [nesta seção](../../delivery/using/managing-subscriptions.md).

* Use o campo **[!UICONTROL Origin]** para adicionar informações sobre a origem dos recipients aos perfis. Essas informações são particularmente úteis na estrutura de uma importação múltipla.

Clique em **[!UICONTROL Next]** para validar essa etapa e exibir a seguinte.

### Etapa 6 - Iniciar a importação {#step-6---launching-the-import}

A última etapa do assistente permite iniciar a importação de dados. To do this, click the **[!UICONTROL Start]** button.

![](assets/s_ncs_user_import_wizard06_1.png)

### Status da tarefa {#job-statuses}

Status da tarefa indica o status atual de uma tarefa. Cada status é representado por um ícone e rótulo especiais. Essas informações são exibidas na lista de tarefas. Os status e seus ícones estão listados abaixo:

![](assets/s_ncs_user_export_status.png)

* **Edição em progresso**

   A tarefa está sendo criada.

* **Execução em progresso**

   A tarefa está sendo executada.

* **Cancelar**

   Clique no botão **[!UICONTROL Cancel]**: a tarefa em andamento é cancelada.

* **Cancelamento em progresso**

   O comando de cancelamento foi considerado e a tarefa está sendo cancelada.

* **Pausa em progresso**

   Clique em **[!UICONTROL Pause]**: a tarefa está sendo suspensa.

* **Em pausa**

   Clique em **[!UICONTROL Pause]**: a tarefa é suspensa. Ele pode ser reiniciado clicando em **[!UICONTROL Start]**.

* **Concluído**

   A execução do trabalho foi concluída.

* **Concluído com erro**

   O trabalho não foi executado devido a um erro técnico.

* **Desligamento do servidor em progresso**

   A tarefa em andamento foi interrompida porque o servidor do Adobe Campaign foi desligado.

## Modelos de importação genérica {#generic-import-samples}

### Exemplo: importar de uma lista de recipients {#example--import-from-a-list-of-recipients}

Para criar e fornecer uma lista de destinatários da visão geral das listas, execute as seguintes etapas:

1. Criação da lista

   * Click the **[!UICONTROL Lists]** link in the **[!UICONTROL Profiles and targets]** menu of the Adobe Campaign home page.
   * Click the **[!UICONTROL Create]** and then the **[!UICONTROL Import a list]** button.

1. Selecionar o arquivo a ser importado

   Clique na pasta à direita do campo **[!UICONTROL Local file]** e selecione o arquivo que contém a lista a ser importada.

   ![](assets/s_ncs_user_import_example00_01.png)

1. Nome e armazenamento da lista

   Insira o nome da lista e selecione o diretório onde ela deve ser salva.

   ![](assets/s_ncs_user_import_example00_02.png)

1. Iniciar a importação

   Clique em **[!UICONTROL Next]** e depois em **[!UICONTROL Start]** para começar a importar a lista.

   ![](assets/s_ncs_user_import_example00_03.png)

### Exemplo: importar novos registros de um arquivo de texto {#example--import-new-records-from-a-text-file-}

Para importar novos perfis de destinatários armazenados em um arquivo de texto para o banco de dados do Adobe Campaign, execute as seguintes etapas:

1. Escolha de um template

   * From the Adobe Campaign home page, click the **[!UICONTROL Profiles and targets]** link, then **[!UICONTROL Jobs]**. Above the list of jobs, click **[!UICONTROL New import]**.
   * Keep the **[!UICONTROL New text import]** template selected by default.
   * Altere o rótulo e a descrição.
   * Selecione **[!UICONTROL Simple import]**.
   * Mantenha a pasta de tarefas padrão.
   * Click **[!UICONTROL Advanced parameters]** and select the **[!UICONTROL Tracking mode]** option to view the details of your import during execution.

1. Selecionar o arquivo a ser importado

   Clique na pasta à direita do campo **[!UICONTROL Local file]** e selecione o arquivo que deseja importar.

   ![](assets/s_ncs_user_import_example01_01.png)

1. Associar campos

   Click the **[!UICONTROL Guess the destination fields]** icon to map the source and destination schemas automatically. Verifique as informações nesta janela antes de clicar em **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_import_example03_01.png)

1. Reconciliação

   * Vá para a tabela **Destinatários (nms:recipient)**.
   * Selecione a operação **[!UICONTROL Insertion]** e deixe os valores padrão nos outros campos.

      ![](assets/s_ncs_user_import_example04_01.png)

1. Importação de destinatários

   * Se necessário, especifique uma pasta na qual os registros serão importados.

      ![](assets/s_ncs_user_import_example05_01.png)

1. Iniciar a importação

   * Clique em **[!UICONTROL Start]**.

      Na área central do editor, é possível verificar se a operação de importação foi bem-sucedida e visualizar o número de registros processados.

      ![](assets/s_ncs_user_import_example06_01.png)

      O modo **[!UICONTROL Tracking]** permite rastrear os detalhes da importação para cada registro no arquivo de origem. To do this, from the home page click **[!UICONTROL Profiles and Targets]** then **[!UICONTROL Processes]**, select the relevant import, and look up the **[!UICONTROL General]**, **[!UICONTROL Journal]** and **[!UICONTROL Rejects]** tabs.

      * Verificar o progresso da importação

         ![](assets/s_ncs_user_import_example07_01.png)

      * Visualização do processo de cada registro

         ![](assets/s_ncs_user_import_example07_02.png)

### Exemplo: atualizar e inserir recipients {#example--update-and-insert-recipients}

Queremos atualizar registros existentes no banco de dados e criar novos arquivos de um arquivo de texto. Veja um exemplo do procedimento:

1. Escolha de um template

   Repita as etapas descritas no exemplo 2 acima.

1. Arquivo a ser importado

   Selecione o arquivo que deseja importar.

   Em nosso exemplo, a visão geral das primeiras linhas do arquivo mostra que o arquivo contém atualizações para três registros e a criação de um registro.

   ![](assets/s_ncs_user_import_example02_02.png)

1. Associar campos

   Aplique o procedimento no exemplo 2 acima.

1. Reconciliação

   * Keep **[!UICONTROL Update or insert]** selected by default.
   * Mantenha a opção **[!UICONTROL Management of duplicates]** no modo **[!UICONTROL Update]** de forma que registros existentes no banco de dados sejam modificados com dados do arquivo de texto.
   * Select the fields **[!UICONTROL Birth date]**, **[!UICONTROL Name]** and **[!UICONTROL Company]** and assign a reconciliation key to them.

      ![](assets/s_ncs_user_import_example04_02.png)

1. Iniciar a importação

   * Clique em **[!UICONTROL Start]**.

      Na janela de rastreamento, é possível verificar se a operação de importação foi bem-sucedida e visualizar o número de registros processados.

      ![](assets/s_ncs_user_import_example06_02.png)

   * Examine a tabela de destinatários para verificar se os registros foram modificados por esta operação.

      ![](assets/s_ncs_user_import_example06_03.png)

### Exemplo: enriquecer os valores com os de um arquivo externo {#example--enrich-the-values-with-those-of-an-external-file}

Queremos modificar determinados campos em uma tabela de banco de dados a partir de um arquivo de texto, dando prioridade aos valores contidos no banco de dados.

Neste exemplo, você pode ver que determinados campos no arquivo de texto têm um valor, enquanto que os campos correspondentes no banco de dados estão vazios. Outros campos contêm um valor diferente daquele contido no banco de dados.

* Conteúdo do arquivo de texto a ser importado.

   ![](assets/s_ncs_user_import_example02_03.png)

* Status do banco de dados antes da importação

   ![](assets/s_ncs_user_import_example06_04.png)

Siga as etapas abaixo:

1. Escolha de um template

   Aplique o procedimento no exemplo 2 acima.

1. Arquivo a ser importado

   Selecione o arquivo que deseja importar.

1. Associar campos

   Aplique o procedimento no exemplo 2 acima.

   Na visualização das primeiras linhas do arquivo, é possível observar que o arquivo contém atualizações para determinados registros.

1. Reconciliação

   * Acesse a tabela e selecione a operação **[!UICONTROL Update]**.
   * Select the option **[!UICONTROL Reject entity]** for the **[!UICONTROL Management of doubles]** field.
   * Mantenha a opção **[!UICONTROL Management of duplicates]** no modo **[!UICONTROL Update]** de forma que registros existentes no banco de dados sejam modificados com dados do arquivo de texto.
   * Place the cursor on the **[!UICONTROL Last name (@lastName)]** node and select the **[!UICONTROL Update only if destination is empty]** option.
   * Repeat this operation for the **[!UICONTROL Company (@company)]** node.
   * Assign a reconciliation key to the fields **[!UICONTROL Birth date]**, **[!UICONTROL E-mail]** and **[!UICONTROL First name]**.

      ![](assets/s_ncs_user_import_example04_03.png)

1. Iniciar a importação

   Clique em **[!UICONTROL Start]**.

   Examine a tabela de destinatários para verificar se os registros foram modificados pela importação.

   ![](assets/s_ncs_user_import_example06_05.png)

   Somente os valores que estavam vazios foram substituídos por valores do arquivo de texto. Porém, o valor existente no banco de dados não foi substituído pelo valor do arquivo de importação.

### Exemplo: atualizar e enriquecer os valores em um arquivo externo {#example--update-and-enrich-the-values-from-those-in-an-external-file}

Queremos modificar determinados campos em uma tabela de banco de dados a partir de um arquivo de texto, dando prioridade aos valores contidos no arquivo de texto.

Neste exemplo, você verá que determinados campos no arquivo de texto têm um valor vazio, enquanto os campos correspondentes no banco de dados não estão vazios. Outros campos contêm um valor diferente daquele no banco de dados.

* Conteúdo do arquivo de texto a ser importado.

   ![](assets/s_ncs_user_import_example02_04.png)

* Status do banco de dados antes da importação

   ![](assets/s_ncs_user_import_example06_07.png)

1. Escolha de um template

   Aplique o procedimento no exemplo 2 acima.

1. Arquivo a ser importado

   Selecione o arquivo que deseja importar.

   Na visualização das primeiras linhas do arquivo, é possível observar que o arquivo contém campos vazios e atualizações para determinados registros.

1. Associar campos

   Aplique o procedimento no exemplo 2 acima.

1. Reconciliação

   * Acesse a tabela e selecione **[!UICONTROL Update]**.
   * Select the option **[!UICONTROL Reject entity]** for the **[!UICONTROL Management of doubles]** field.
   * Deixe a opção **[!UICONTROL Management of duplicates]** no modo **[!UICONTROL Update]** para os registros existentes no banco de dados a serem modificados com dados do arquivo de texto.
   * Place the cursor on the **[!UICONTROL Account number (@account)]** node and select the option **[!UICONTROL Take empty values into account]**.
   * Select the fields **[!UICONTROL Birth date]**, **[!UICONTROL E-mail]** and **[!UICONTROL First name]** and assign a reconciliation key to them.

      ![](assets/s_ncs_user_import_example04_04.png)

1. Iniciar a importação

   * Clique em **[!UICONTROL Start]**.
   * Examine a tabela de destinatários para verificar se os registros foram modificados pela operação.

      ![](assets/s_ncs_user_import_example06_06.png)

      Os valores do arquivo de texto que estavam vazios substituíram os valores no banco de dados. Os valores existentes no banco de dados foram atualizados com aqueles no arquivo de importação ao manter a opção **[!UICONTROL Update]** selecionada para duplicatas na etapa 4.

## Importação de dados de um workflow {#importing-data-from-a-workflow}

Os workflows podem ser uma maneira útil de automatizar alguns dos processos de importação. Se você importa dados de um arquivo local ou de um SFTP, você pode usar workflows para padronizar os procedimentos de gerenciamento de dados.

Para saber mais sobre como importar dados de um workflow, consulte [esta seção](../../workflow/using/importing-data.md).
