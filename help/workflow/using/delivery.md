---
title: Delivery
seo-title: Delivery
description: Delivery
seo-description: null
page-status-flag: never-activated
uuid: 3a74fd0b-8598-46a0-bf13-cf35db0987d7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 9fd7122e-22c7-4f9a-a2a4-5de3daaa3c2e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Delivery{#delivery}

Uma atividade do tipo **Delivery** permite criar uma ação de delivery. Ele pode ser construído usando elementos de entrada.

Para configurá-lo, edite a atividade e insira as opções de delivery.

![](assets/edit_diffusion.png)

1. **Delivery**

   É possível:

   * Atue no delivery especificado na transição de entrada. To do this, select the first option of the **[!UICONTROL Delivery]** section of the window.

      Essa opção pode ser usada quando uma atividade de workflow anterior já criou ou especificou o delivery. Isso pode ter sido feito, como no exemplo abaixo, por uma atividade do mesmo tipo que gerou uma transição de saída.

      No exemplo a seguir, o delivery é criado pela primeira vez. O público e o conteúdo são definidos mais tarde. Em seguida, as informações desses três elementos são inseridas novamente em uma nova atividade de delivery usando a transição de entrada para que isso possa ser enviado.

      ![](assets/specified_transition_option_exemple.png)

   * Selecione diretamente o delivery envolvido. To do this, select the **[!UICONTROL Explicit]** option and select the delivery from the drop-down list of the **[!UICONTROL Delivery]** field.

      A lista exibe deliveries não concluídos contidos na pasta **Deliveries** por padrão. To access other campaigns, click the **[!UICONTROL Select link]** icon.

      ![](assets/diffusion_edit_1.png)

      Select the campaign from the drop-down list of the **[!UICONTROL Folder]** field, or click **[!UICONTROL Display sub-levels]** to display all of the deliveries contained in sub-folders:

      ![](assets/diffusion_edit_2.png)

      After selecting the delivery action, you can display the content by clicking the **[!UICONTROL Edit link]** icon.

   * Crie um script para calcular o delivery. To do this, select the **[!UICONTROL Calculated by a script]** option and enter the script. You can open an input window by clicking the **[!UICONTROL Edit...]** option. O exemplo a seguir recupera o identificador do delivery:

      ![](assets/diffusion_edit_3.png)

   * Criação de novo delivery To do this, select the **[!UICONTROL New, created from a template]** option and select the delivery template which the delivery will be based on.

      ![](assets/diffusion_edit_4.png)

      Click the **[!UICONTROL Select link]** icon to browse the folders, and click the **[!UICONTROL Edit link]** icon if you wish to view the content of the selected template.

1. **Recipientes**

   Os recipients podem ser especificados pelos eventos de entrada, por exemplo, seguindo uma importação de arquivo ou especificado na ação de delivery. Eles também podem ser armazenados em um ou mais arquivos.

   ![](assets/diffusion_edit_5.png)

1. **Conteúdo**

   O conteúdo da mensagem pode ser definido no delivery ou no evento de entrada.

   ![](assets/diffusion_edit_6.png)

1. **Ação a ser executada**

   Você pode criar o delivery, prepará-lo, iniciá-lo, estimar o target ou enviar uma prova.

   ![](assets/diffusion_edit_7.png)

   Selecione o tipo de ação a ser executada:

   * **[!UICONTROL Save]**: essa opção permite criar a entrega e salvá-la. Ele não irá analisar nem enviá-lo.
   * **[!UICONTROL Estimate the target]**: essa opção permite calcular a meta de entrega para avaliar seu potencial (primeira fase de análise). This action is the equivalent of selecting the **[!UICONTROL Estimate the population to be targeted]** option and clicking **[!UICONTROL Analyze]** when sending a delivery to the main target via **Delivery**.
   * **[!UICONTROL Prepare]**: essa opção permite que você execute o processo de análise completo (cálculo de meta e preparação de conteúdo). O delivery não é enviado. This action is the equivalent of selecting the **[!UICONTROL Deliver as soon as possible]** option and clicking **[!UICONTROL Analyze]** when sending a delivery to the main target with **Delivery**.
   * **[!UICONTROL Send a proof]**: essa opção permite que você envie uma prova da entrega. This action is the equivalent of clicking the **[!UICONTROL Send a proof]** button in the toolbar of a delivery with **Delivery**
   * **[!UICONTROL Prepare and start]**: essa opção inicia o processo de análise completo (cálculo de meta e preparação de conteúdo) e envia a entrega. Essa ação equivale a clicar **[!UICONTROL Deliver as soon as possible]**, **[!UICONTROL Analyze]** e **[!UICONTROL Confirm delivery]** escolher ao enviar uma entrega para a meta principal com **Entrega**.
   The **[!UICONTROL Act on a delivery]** activity used further on in the workflow lets you launch all remaining steps required for starting the delivery (target calculation, content preparation, delivery). For more on this, refer to [Delivery control](../../workflow/using/delivery-control.md).

   As seguintes opções também estão disponíveis:

   * **[!UICONTROL Generate an outbound transition]**

      Cria uma transição de saída que será ativada no final da execução. Você pode escolher se quer recuperar ou não o target do delivery.

   * **[!UICONTROL Do not recover target]**

      Não recupera o target da ação de delivery realizada.

   * **[!UICONTROL Processing errors]**

      Refer to [Delivery control](../../workflow/using/delivery-control.md).
   A guia **Script** permite modificar os parâmetros de delivery.

   ![](assets/edit_diffusion_fil_script.png)

## Exemplo: workflow de delivery {#example--delivery-workflow}

Crie um novo workflow e adicione atividades conforme mostrado no gráfico abaixo:

![](assets/new-workflow-5.png)

Abra a atividade de **Delivery** e defina as propriedades da seguinte maneira:

* Na **[!UICONTROL Delivery]** seção, selecione **[!UICONTROL New, created from a template]** e selecione um modelo de entrega.
* Na **[!UICONTROL Recipients]** seção, selecione **[!UICONTROL Specified in the delivery]**.
* Na **[!UICONTROL Action to execute]** seção, mantenha a **[!UICONTROL Prepare]** opção.

![](assets/new-workflow-param-delivery.png)

Click **[!UICONTROL OK]** to close the properties window. Você acabou de configurar uma atividade que consiste na criação e preparação de um novo delivery com base em um template de delivery cujo destino será especificado.

Abra a atividade de **Aprovação** e defina as propriedades da seguinte maneira:

1. In the **[!UICONTROL Assignment type]** field, select a group in which you are registered. Se estiver conectado com a conta de administrador, selecione o grupo Administração.
1. Em seguida, insira um título e insira o seguinte texto no corpo da mensagem:

   ```
   Do you wish to approve delivery (<%= vars.recCount %> recipient(s))?
   ```

   Esta é uma mensagem que inclui uma expressão escrita em JavaScript: representa **[!UICONTROL vars.recCount]** o número de destinatários direcionados pela entrega da tarefa anterior. Para obter mais informações sobre expressões JavaScript, consulte scripts e modelos [](../../workflow/using/javascript-scripts-and-templates.md)JavaScript.

   ![](assets/new-workflow-param-validation.png)

   The Approval task is detailed in [Approval](../../workflow/using/approval.md).

## Parâmetros de entrada {#input-parameters}

Identificador de entrega, se a **[!UICONTROL Specified in the transition]** opção estiver selecionada na **[!UICONTROL Delivery]** seção.

* deliveryId
* tableName
* schema

Cada evento de entrada deve especificar um target definido por esses parâmetros.

>[!NOTE]
>
>Esse parâmetro só será exibido se a **[!UICONTROL Specified by inbound event(s)]** opção estiver selecionada na **[!UICONTROL Recipients]** seção.

* filename

   O nome completo do arquivo gerado se a **[!UICONTROL File(s) specified by inbound event(s)]** opção estiver selecionada na **[!UICONTROL Recipients]** seção.

* contentId

   Identificador de conteúdo se a **[!UICONTROL Specified by inbound events]** opção estiver selecionada na **[!UICONTROL Content]** seção.

## Parâmetros de output {#output-parameters}

* tableName
* schema
* recCount

Esse conjunto de três valores identifica o target resultante do delivery. **[!UICONTROL tableName]** é o nome da tabela que memoriza os identificadores da meta, **[!UICONTROL schema]** é o esquema da população (normalmente nms:customer) e **[!UICONTROL recCount]** é o número de elementos na tabela.

A transição associada ao complemento tem os mesmos parâmetros.

>[!NOTE]
>
>There are no output parameters when the **[!UICONTROL Do not recover target]** option is selected.

