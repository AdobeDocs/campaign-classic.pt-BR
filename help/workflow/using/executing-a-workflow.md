---
title: Execução de um fluxo de trabalho
seo-title: Execução de um fluxo de trabalho
description: Execução de um fluxo de trabalho
seo-description: null
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4b4ec97e52a494dd88b2516650ae514294f00934

---


# Execução de um fluxo de trabalho{#executing-a-workflow}

Diretrizes para solução de problemas relacionados à execução de fluxos de trabalho estão disponíveis [nesta seção](../../production/using/workflow-execution.md).

## Iniciando um workflow {#starting-a-workflow}

Um workflow é sempre iniciado manualmente. When started, it can however remain inactive depending on the information specified via a scheduler (see [Scheduler](../../workflow/using/scheduler.md)) or activity scheduling.

As ações relacionadas à execução do workflow para construção do target (iniciar, parar, pausar etc.) são processos **assíncronos**: a ordem é registrada e entrará em vigor assim que o servidor estiver disponível para aplicá-lo.

A barra de ferramentas permite iniciar e controlar a execução do workflow.

The list of options available in the **[!UICONTROL Actions]** menu and the right-click menu are detailed below.

### Barra de ferramentas Ações {#actions-toolbar}

Os botões da barra de ferramentas são detalhados nesta [seção](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow). The **[!UICONTROL Actions]** button gives you access to additional execution options for acting on selected workflows. You can also use the **[!UICONTROL File > Actions]** menu, or right-click a workflow and select **[!UICONTROL Actions]**.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   Essa ação permite iniciar a execução de um workflow: um workflow **Concluído**, **Em edição** ou **Pausado** altera o status para **Iniciado**. Em seguida, o motor de workflow manipula a execução desse workflow. Se o workflow tiver sido pausado, ele será retomado, caso contrário, o workflow será iniciado desde o início e as atividades iniciais serão ativadas.

   O início é um processo assíncrono: A solicitação é salva e processada o mais rápido possível por um servidor de fluxo de trabalho.

* **[!UICONTROL Pause]**

   Esta ação define o status do workflow como **Pausado**. Nenhuma atividade é ativada até que o workflow seja retomado. No entanto, as operações em andamento não são interrompidas.

* **[!UICONTROL Stop]**

   Esta ação interrompe um workflow sendo executado no momento. O status da instância é definido como **Concluído**. Se possível, as operações em andamento são interrompidas. Importações e queries SQL são canceladas imediatamente.

   A interrupção é um processo assíncrono. A solicitação é registrada, então o servidor de workflow ou servidores cancelam as operações em andamento. A interrupção de uma instância de workflow pode demorar, especialmente se o workflow estiver em execução em vários servidores, cada um deles deve assumir o controle para cancelar as tarefas em andamento.

* **[!UICONTROL Restart]**

   Essa ação interrompe e depois retoma o workflow. Na maioria dos casos, é possível reiniciar mais rápido. Também é útil automatizar a reinicialização quando a interrupção leva um determinado tempo: isso ocorre porque o comando &#39;Parar&#39; não está disponível quando o workflow está sendo interrompido.

   The **[!UICONTROL Start / Pause / Stop / Restart]** actions are also available via the execution icons in the toolbar. Para obter mais informações, consulte esta [seção](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow).

* **[!UICONTROL Purge history]**

   Essa ação permite limpar o histórico do workflow. For more on this, refer to [Purging the logs](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

* **[!UICONTROL Start in simulation mode]**

   Essa opção permite iniciar o workflow no modo de simulação em vez do modo real. This means that when you enable this mode, only activities that do not impact the database or the file system are executed (e.g. **[!UICONTROL Query]**, **[!UICONTROL Union]**, **[!UICONTROL Intersection]**, etc.). Atividades que têm impacto (por exemplo, **[!UICONTROL Export]**, **[!UICONTROL Import]** etc.) assim como os posteriores (na mesma sucursal) não são executados.

* **[!UICONTROL Execute pending tasks now]**

   Essa ação permite iniciar todas as tarefas pendentes assim que possível. To start a specific task, right-click its activity and select **[!UICONTROL Execute pending task(s) now]**.

* **[!UICONTROL Unconditional stop]**

   This option changes the workflow status to **[!UICONTROL Finished]**. Essa ação só deve ser usada como último recurso se o processo de interrupção normal falhar após alguns minutos. Use apenas a interrupção incondicional se tiver certeza de que não há tarefas de workflow em andamento.

   >[!CAUTION]
   >
   >Essa opção destina-se somente aos usuários avançados.

* **[!UICONTROL Save as template]**

   Essa ação cria um novo modelo de workflow com base no workflow selecionado. You need to specify the folder where it will be saved (in the **[!UICONTROL Folder]** field).

   As opções **[!UICONTROL Mass update of selected lines]** e **[!UICONTROL Merge selected lines]** são opções genéricas de plataforma disponíveis em todos os **[!UICONTROL Actions]** menus. Para obter mais informações, consulte esta [seção](../../platform/using/updating-data.md).

### Menu de contexto {#right-click-menu}

Quando uma ou mais atividades de workflow forem selecionadas, você pode clicar com o botão direito do mouse para agir em sua seleção.

![](assets/contextual_menu.png)

As seguintes opções estão disponíveis no menu de contexto:

**[!UICONTROL Open]**: essa opção permite acessar as propriedades da atividade.

**[!UICONTROL Display logs:]** essa opção permite que você visualize o log de execução da tarefa para a atividade selecionada. Consulte [Exibir logs](../../workflow/using/monitoring-workflow-execution.md#displaying-logs).

**[!UICONTROL Execute pending task(s) now:]** essa ação permite que você inicie tarefas pendentes o mais rápido possível.

**[!UICONTROL Workflow restart from a task:]** essa opção permite reiniciar o fluxo de trabalho usando os resultados armazenados anteriormente para essa atividade.

**[!UICONTROL Cut/Copy/Paste/Delete:]** essas opções permitem que você recorte, copie, cole e exclua atividades.

**[!UICONTROL Copy as bitmap:]** essa opção permite que você realize uma captura de tela de todas as atividades.

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** essas opções também estão disponíveis na **[!UICONTROL Advanced]** guia das propriedades da atividade. They are detailed in [Execution](../../workflow/using/advanced-parameters.md#execution).

**[!UICONTROL Save / Cancel:]** permite salvar ou cancelar as alterações feitas em um fluxo de trabalho.

>[!NOTE]
>
>Você pode selecionar um grupo de atividades e aplicar um desses comandos a eles.

O menu de contexto também é detalhado nesta [seção](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow).

## Ciclo de vida do workflow {#workflow-life-cycle}

O ciclo do workflow tem três etapas principais.

* **Em edição**

   Esta é a fase inicial de projeto: Quando o novo fluxo de trabalho é criado, seu status é &quot;sendo editado&quot;. O workflow ainda não foi processado pelo servidor e pode ser modificado sem risco.

* **Iniciado**

   Quando a fase inicial de design for concluída, o workflow poderá ser iniciado. Nesta fase, a instância é tratada pelo servidor e as tarefas individuais são executadas. O workflow ainda pode ser modificado com determinadas precauções.

* **Concluído**

   Um workflow é &#39;Concluído&#39; quando não há mais nenhuma tarefa em andamento ou quando um operador tiver interrompido explicitamente a instância.

Por exemplo, as atividades de **Start** e de **Delivery** são destacadas enquanto a atividade de **Aprovação** pisca no workflow abaixo.

![](assets/new-workflow-6.png)

Isso significa que as duas primeiras atividades foram executadas com êxito e que a aprovação está em andamento, ou seja, foi criada, mas ainda não foi concluída.

Os caracteres **574 -Ok** exibidos acima da transição após a atividade de **Delivery** significam que a preparação do delivery teve 574 recipients como alvo e que a operação foi concluída com êxito. Essas informações, que são adicionadas às transições quando são executadas, são calculadas pelas atividades que processam dados.

O workflow é iniciado e aguarda um operador pertencente ao grupo especificado na atividade de **Aprovação** para tomar uma decisão. Os operadores pertencentes ao grupo e que têm um endereço de email ou número de telefone celular são notificados.

A gestão de operador é apresentada nesta [seção](../../platform/using/access-management.md).

Para obter mais informações sobre como monitorar seus fluxos de trabalho, consulte [esta seção](../../workflow/using/monitoring-workflow-execution.md).

## Ciclo de vida dos dados {#data-life-cycle}

### Tabela de trabalho {#work-table}

Nos workflows, os dados transportados de uma atividade para outra são armazenados em uma tabela de trabalho temporária.

Esses dados podem ser exibidos e analisados clicando com o botão direito do mouse na transição apropriada.

![](assets/wf-right-click-analyze.png)

Para fazer isso, selecione o menu relevante:

* Exibição do target

   This menu displays the available data on the target population as well as the structure of the work table (**[!UICONTROL Schema]** tab).

   ![](assets/wf-right-click-display.png)

   Para obter mais informações, consulte [Worktables e esquema](../../workflow/using/monitoring-workflow-execution.md#worktables-and-workflow-schema)de fluxo de trabalho.

* Análise do target

   Esse menu permite acessar o assistente de análise descritiva que produz estatísticas e relatórios sobre os dados de transição.

   Para obter mais informações, consulte esta [seção](../../reporting/using/using-the-descriptive-analysis-wizard.md).

Os dados do target são descartados na execução do workflow Somente a última tabela de trabalho está acessível. You can configure the workflow so that all work tables remain accessible: check the **[!UICONTROL Keep the result of interim populations between two executions]** option in the workflow properties.

No entanto, recomendamos que você evite ativar essa opção quando a quantidade de dados for significativa.

![](assets/wf-purge-data-option.png)

### Dados do target {#target-data}

Os dados armazenados na tabela de trabalho do workflow podem ser acessados nos campos de personalização.

Isso permite que você use dados coletados por uma lista ou com base nas respostas de uma pesquisa em um delivery. Para fazer isso, use a seguinte sintaxe:

```
%= targetData.FIELD %
```

**[!UICONTROL Target extension]** Os elementos de personalização do tipo (targetData) não estão disponíveis para fluxos de trabalho de direcionamento. O target do delivery deve ser construído no workflow e especificado na transição de entrada do delivery.

If you want to create delivery proofs, the proof target needs to be built based on the **[!UICONTROL Address substitution]** mode so that the personalization data can be entered. Para obter mais informações, consulte esta [seção](../../delivery/using/steps-defining-the-target-population.md#using-address-substitution-in-proof).

No exemplo a seguir, vamos coletar uma lista de informações sobre os clientes, para ser usada em um email personalizado.

Siga as etapas abaixo:

1. Crie um workflow para coletar informações, reconcilie com os dados já existentes no banco de dados, e depois inicie um delivery.

   ![](assets/wf-targetdata-sample-1.png)

   No nosso exemplo, o conteúdo do arquivo é o seguinte:

   ```
   Music,First name,Last name,Account,CD/DVD,Card
   Pop,David,BLAIR,4323,CD,0
   Rock,Daniel,ARCARI,3222,DVD,1
   Disco,Uma,ALTON,0488,DVD,0
   Jazz,Paul,BOLES,6475,CD,1
   Jazz,David,BOUKHARI,0841,DVD,1
   [...]
   ```

   Para carregar o arquivo, siga as seguintes etapas:

   ![](assets/wf-targetdata-sample-2.png)

1. Configure the **[!UICONTROL Enrichment]** type activity to reconcile the collected data with that already in the Adobe Campaign database.

   Aqui, a chave de conciliação é o número da conta:

   ![](assets/wf-targetdata-sample-3.png)

1. Then configure the **[!UICONTROL Delivery]**: it is created based on a template, and the recipients are specified by the inbound transition.

   ![](assets/wf-targetdata-sample-4.png)

   >[!CAUTION]
   >
   >Somente os dados contidos na transição podem ser usados para personalizar o delivery. **os campos de personalização do tipo targetData** só estão disponíveis para a população de entrada da **[!UICONTROL Delivery]** atividade.

1. No template de delivery, use os campos coletados no workflow.

   To do this, insert **[!UICONTROL Target extension]** type personalization fields.

   ![](assets/wf-targetdata-sample-5.png)

   Nesse exemplo, queremos inserir o gênero de música e o tipo de mídia favoritos do cliente (CD ou DVD), conforme declarado no arquivo coletado pelo workflow.

   Como um diferencial, vamos adicionar um cupom para os titulares de cartões de fidelidade, ou seja, recipients para os quais o valor &#39;Cartão&#39; for igual a 1.

   ![](assets/wf-targetdata-sample-6.png)

   **[!UICONTROL Target extension]** Os dados do tipo (targetData) são inseridos em entregas usando as mesmas características de todos os campos de personalização. Eles também podem ser usados no assunto, rótulos de link ou nos próprios links.

   As mensagens endereçadas para os recipients coletados conterão os seguintes dados:

   ![](assets/wf-targetdata-sample-7.png)

## Definição de aprovações {#defining-approvals}

As aprovações permitem que os operadores tomem decisões que regem um workflow ou confirmem sua execução contínua.

Uma mensagem é enviada a um grupo de operadores e o workflow aguarda uma resposta antes de continuar. O workflow não é interrompido e outras operações podem ocorrer. Por exemplo, pode haver várias aprovações simultâneas pendentes.

Uma aprovação pode conter várias opções para o operador escolher. No entanto, é possível restringir o número de escolhas a um para enviar uma tarefa a ser executada por um operador, como, por exemplo, a execução de target. O operador pode responder depois que a tarefa for executada (o processo então reinicia). O exemplo a seguir ilustra esses tipos de aprovações:

![](assets/validation-1.png)

Em operações, todos os estágios que exigem aprovação se baseiam no mesmo princípio.

![](assets/validation-1-in-op.png)

Exemplos de aprovação podem ser encontrados nesta [seção](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).

Um operador pode responder de uma das duas formas seguintes: validação usando a página da Web vinculada na mensagem de email ou através do console.

>[!NOTE]
>
>Após salvar a resposta, ela não poderá ser modificada.

### Envio de emails {#sending-emails}

É possível receber uma mensagem de aprovação contendo um link para uma página da Web pela qual é possível responder. Para que o operador de target receba um email de aprovação, o endereço de email do operador deve ser completo. Se esse não for o caso, o operador deve usar o console para responder

A gestão de operador é apresentada nesta [seção](../../platform/using/access-management.md).

Emails de aprovação são enviados continuamente. O modelo de entrega padrão é **[!UICONTROL notifyAssignee]**: Ele é salvo na **[!UICONTROL Administration > Campaign management > Technical delivery templates]** pasta. Esse cenário pode ser personalizado e também é recomendável fazer uma cópia e alterar templates para cada atividade.

As entregas criadas por meio deste modelo são armazenadas na **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]** pasta.

### Aprovação através do console {#approval-via-the-console}

Em operações, os elementos a serem aprovados são exibidos no painel da campanha.

For technical workflows, the tasks that the user can approve can be accessed from the tree structure in the **[!UICONTROL Administration > Production > Objects created automatically > Pending approvals]** folder.

![](assets/validation-node.png)

### Grupos {#groups}

Uma aprovação é atribuída a um grupo de operadores, um único operador ou um conjunto de operadores selecionados por meio de uma condição de filtragem.

1. Para a forma mais simples de aprovação, a tarefa é concluída assim que um operador responde. Qualquer outro operador que tenta responder será notificado que outra pessoa já fez isso.
1. Para obter várias aprovações, consulte [Várias aprovações](#multiple-approval).

Os grupos de operadores para aprovações devem ser designados como atribuições ou funções em vez de pessoas nomeadas. Por exemplo, um grupo &quot;Orçamento da campanha&quot; é preferível ao &quot;Grupo do Harry&quot;. Recomendamos ter pelo menos duas pessoas em um grupo que possam aprovar uma tarefa. Dessa forma, se uma pessoa estiver ausente, a outra poderá responder.

### Expirações {#expirations}

Expirações são transições específicas usadas em diferentes tipos de atividade e particularmente em aprovações. Uma expiração pode ser usada para acionar uma ação após um determinado período de tempo na ausência de uma resposta ou para buscar o workflow (e atribuir uma aprovação a um grupo diferente, por exemplo).

A segunda guia nas propriedades da atividade de aprovação permite definir uma ou mais expirações. Na verdade, você pode definir vários tipos de expiração.

![](assets/expiration.png)

To add a new expiration, click **[!UICONTROL Add]**. Uma transição é adicionada a cada expiração criada. É possível:

* modificar os parâmetros típicos diretamente clicando em uma célula na lista (ou pressionando F2),
* or edit the expression by clicking the **[!UICONTROL Detail...]** button.

>[!NOTE]
>
>Não é necessário especificar uma ordem para as expirações, pois são processadas em ordem cronológica.

The **[!UICONTROL Do not terminate the task]** option leaves the approval active when the delay is overrun. Esse modo possibilita gerenciar lembretes ao deixar a aprovação ativa: os operadores ainda podem responder. Essa opção é desabilitada por padrão, significando que a tarefa é considerada concluída na expiração e que os operadores não podem mais responder.

Você pode criar quatro tipos de expirações:

* **Atraso após o início** da tarefa: A expiração é calculada adicionando um tempo especificado à data em que a aprovação é ativada.
* **Atraso após uma data** específica: A expiração é calculada adicionando um tempo a uma data especificada.
* **Atraso antes de uma determinada data**: A expiração é calculada subtraindo um período de tempo de uma data especificada.
* **Expiração calculada pelo script**: A expiração é calculada usando o JavaScript.

   O exemplo a seguir calcula uma expiração 24 horas antes da data em que um delivery é iniciado (identificada por **vars.deliveryId**):

   ```
   var delivery = nms.delivery.get(vars.deliveryId)
   var expiration = delivery.scheduling.contactDate
   var oneDay = 1000*60*60*24
   expiration.setTime(expiration.getTime() - oneDay)
   return expiration
   ```

### Aprovação múltipla {#multiple-approval}

A aprovação múltipla é um mecanismo que permite que todos os operadores de aprovação respondam. Uma transição é ativada para cada resposta.

A aprovação múltipla é útil para mecanismos de voto ou pesquisa. Você pode contar respostas e processar seu resultado após um determinado período ao adicionar um prazo.

### Direitos necessários {#required-rights}

Os operadores em um grupo devem ter pelo menos os seguintes direitos para poder responder a uma solicitação de aprovação:

* Permissões de gravação para workflow.
* Permissões de leitura e gravação para a pasta que contém as tarefas a serem aprovadas.

O grupo &#39;Execução de workflow&#39; tem esses direitos. Um operador adicionado a esse grupo tem os direitos de responder a uma solicitação de aprovação.

## Arquitetura {#architecture}

Os workflows são manipulados por um módulo específico. Esse módulo pode ser iniciado em vários servidores para compartilhar a carga de processamento.

![](assets/architecture.png)

* O processo &#39;Executor de Instância de Workflow&#39; (runwf) executa todas as tarefas de uma determinada instância de workflow. Quando não há tarefas a serem executadas no momento, se torna &#39;passivo&#39;, indicando que seu status é salvo no banco de dados e depois é interrompido.
* O módulo &#39;Servidor de Workflow&#39; (wfserver) monitora as instâncias de workflows atuais. Quando há uma tarefa para executar, esse módulo cria um processo para ativar (ou reativar) a instância correspondente.

Quando um operador executa uma ação em um workflow (iniciar, parar, pausar etc.), a ação não é executada imediatamente pelo módulo &#39;nlserver&#39;, mas, em vez disso, é colocada em uma fila para ser processada pelo módulo de workflow.
