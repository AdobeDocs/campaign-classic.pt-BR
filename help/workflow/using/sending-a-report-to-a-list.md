---
title: Envio de um relatório a uma lista
seo-title: Envio de um relatório a uma lista
description: Envio de um relatório a uma lista
seo-description: null
page-status-flag: never-activated
uuid: 29759fd8-47f3-47cc-9f7e-263e305fd6fb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 41b8a8a8-efac-4e8e-8aea-d4fd06c46e74
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Envio de um relatório a uma lista{#sending-a-report-to-a-list}

This use case details how to generate a monthly out-of-the-box **[!UICONTROL Tracking indicators]** report in PDF format and how to send it to a list of recipients.

![](assets/use_case_report_intro.png)

As principais etapas de implementação para este caso de uso são:

* Criando uma lista de destinatários que receberão a entrega (consulte: [Etapa 1: Criando a lista](#step-1--creating-the-recipient-list)de destinatários).
* Creating a delivery template that will let you generate a new delivery each time the workflow is executed (refer to: [Step 2: Creating the delivery template](#step-2--creating-the-delivery-template)).
* Creating a workflow that will let you generate the report in PDF format and send it to the list of recipients (refer to: [Step 3: Creating the workflow](#step-3--creating-the-workflow)).

## Step 1: Creating the recipient list {#step-1--creating-the-recipient-list}

Vá para o **[!UICONTROL Profiles and targets]** universo, clique no **[!UICONTROL Lists]** link e depois no **[!UICONTROL Create]** botão. Select **[!UICONTROL New list]** and create a new recipient list for the report to be sent to.

![](assets/use_case_report_1.png)

Para saber mais sobre criação de listas, consulte esta [seção](../../platform/using/creating-and-managing-lists.md).

## Step 2: Creating the delivery template {#step-2--creating-the-delivery-template}

1. Vá para o **[!UICONTROL Resources > Templates > Delivery templates]** nó do Adobe Campaign explorer e duplique o modelo **[!UICONTROL Email delivery]** pronto para usar.

   ![](assets/use_case_report_2.png)

   Para obter mais informações sobre criação de template de delivery, consulte esta [seção](../../delivery/using/about-templates.md).

1. Insira os vários parâmetros do template: rótulo, target (a lista de recipients criados anteriormente), assunto e conteúdo.

   ![](assets/use_case_report_3.png)

1. Cada vez que o fluxo de trabalho é executado, o **[!UICONTROL Tracking indicators]** relatório é atualizado (consulte a [Etapa 3: Criação do fluxo de trabalho](#step-3--creating-the-workflow)). To include the latest version of the report in the delivery, you need to add a **[!UICONTROL Calculated attachment]**:

   Para obter mais informações sobre um anexo calculado, consulte esta [seção](../../delivery/using/attaching-files.md#creating-a-calculated-attachment).

   * Clique no **[!UICONTROL Attachments]** link e clique em **[!UICONTROL Add]**, em seguida, selecione **[!UICONTROL Calculated attachment]**.

      ![](assets/use_case_report_4.png)

   * Go to the **[!UICONTROL Type]** field and select the fourth option: **[!UICONTROL File name is computed during delivery of each message (it may then depend on the recipient profile)]**.

      ![](assets/use_case_report_5.png)

      The value entered in the **[!UICONTROL Label]** field will not appear in the final delivery.

   * Vá para a zona de edição e digite o caminho de acesso e o nome do arquivo.

      ![](assets/use_case_report_6.png)

      >[!CAUTION]
      >
      >O arquivo deve estar presente no servidor. Seu caminho e nome devem ser idênticos aos inseridos na atividade de **[!UICONTROL JavaScript code]** tipo do fluxo de trabalho (consulte: [Etapa 3: Criação do fluxo de trabalho](#step-3--creating-the-workflow)).

   * Selecione a **[!UICONTROL Advanced]** guia e marque **[!UICONTROL Script the name of the file name displayed in the mails sent]**. Vá para a zona de edição e insira o nome que deseja dar ao anexo na delivery final.

      ![](assets/use_case_report_6bis.png)

## Etapa 3: Criação do fluxo de trabalho {#step-3--creating-the-workflow}

O seguinte workflow foi criado para este caso de uso. Ele tem três atividades:

* One **[!UICONTROL Scheduler]** type activity that lets you execute the workflow once a month,
* One **[!UICONTROL JavaScript code]** type activity that lets you generate the report in PDF format,
* one **[!UICONTROL Delivery]** type activity that uses the previously created delivery template.

![](assets/use_case_report_8.png)

1. Now go to the **[!UICONTROL Administration > Production > Technical workflows]** node and create a new workflow.

   ![](assets/use_case_report_7.png)

1. Start by adding a **[!UICONTROL Scheduler]** type activity and configure it so that the workflow executes on the first Monday of the month.

   ![](assets/use_case_report_9.png)

   For more on configuring the scheduler, refer to [Scheduler](../../workflow/using/scheduler.md).

1. Em seguida, adicione um tipo de atividade. **[!UICONTROL JavaScript code]**

   ![](assets/use_case_report_10.png)

   Insira o seguinte código na zona de edição:

   ```
   var reportName = "deliveryFeedback";
   var path = "/tmp/deliveryFeedback.pdf";
   var exportFormat = "PDF";
   var reportURL = "<PUT THE URL OF THE REPORT HERE>";
   var _ctx = <ctx _context="global" _reportContext="deliveryFeedback" />
   var isAdhoc = 0;
   
   xtk.report.export(reportName, _ctx, exportFormat, path, isAdhoc);
   ```

   As seguintes variáveis são utilizadas:

   * **var reportName**: insira o nome interno do relatório em aspas duplas. Nesse caso, o nome interno do relatório **Tracking indicator** é &quot;deliveryFeedback&quot;.
   * **caminho var**: insira o caminho de salvamento do arquivo (&quot;tmp/files/&quot;), o nome que deseja dar ao arquivo (&quot;deliveryFeedback&quot;) e a extensão de arquivo (&quot;.pdf&quot;). Nesse caso, usamos o nome interno como o nome do arquivo. Os valores precisam estar entre aspas duplas e separados pelo caractere &quot;+&quot;.

      >[!CAUTION]
      >
      >O arquivo deve ser salvo no servidor. You must enter the same path and the same name in the **[!UICONTROL General]** tab of the edit window for the calculated attachment (refer to: [Step 2: Creating the delivery template](#step-2--creating-the-delivery-template)).

   * **var exportFormat**: insira o formato de exportação do arquivo (&quot;PDF&quot;).
   * **var _ctx** (contexto): neste caso, estamos a utilizar o **[!UICONTROL Tracking indicators]** relatório no seu contexto global.

1. Finish by adding a **[!UICONTROL Delivery]** type activity with the following options:

   * **[!UICONTROL Delivery]**: selecione **[!UICONTROL New, created from a template]** e selecione o modelo de entrega criado anteriormente.
   * Para os campos **[!UICONTROL Recipients]** e **[!UICONTROL Content]** , selecione **[!UICONTROL Specified in the delivery]**.
   * **[!UICONTROL Action to execute]**: selecione **[!UICONTROL Prepare and start]**.
   * Desmarcar **[!UICONTROL Generate an outbound transition]** e **[!UICONTROL Process errors]**.
   ![](assets/use_case_report_11.png)

