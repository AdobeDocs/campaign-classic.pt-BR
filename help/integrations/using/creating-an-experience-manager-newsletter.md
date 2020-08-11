---
title: Criação de boletim informativo no Experience Manager
seo-title: Criação de boletim informativo no Experience Manager
description: Criação de boletim informativo no Experience Manager
seo-description: null
page-status-flag: never-activated
uuid: 75cf4891-06a6-42d2-9b22-b4d93e0dc64a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 627ade78-96b3-4a6e-9ace-74610a3c8d1a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: bc54cef4c44be4c694e062f56685dbb09d2fcf8e
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 66%

---


# Criação de boletim informativo no Experience Manager{#creating-an-experience-manager-newsletter}

Essa integração pode ser usada para criar um boletim informativo no Adobe Experience Manager que será usado no Adobe Campaign como parte de uma campanha de email.

Para obter um exemplo mais detalhado sobre como usar essa integração, consulte este [guia com o passo a passo](https://helpx.adobe.com/campaign/kb/acc-aem.html).

**No Adobe Experience Manager:**

1. Na instância do autor do AEM, clique no logotipo **Adobe Experience** no lado superior esquerdo da página e selecione **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. Selecione **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**.
1. Clique no botão **[!UICONTROL Create]** no lado superior direito da página e selecione **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. Select the **[!UICONTROL Adobe Campaign Email (AC 6.1)]** template and name your newsletter.
1. Once your page is created, access the **[!UICONTROL Page information]** menu and click **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. In the **[!UICONTROL Cloud Services]** tab, select **[!UICONTROL Adobe Campaign]** as **[!UICONTROL Cloud service configuration]** and your Adobe Campaign instance in the second drop-down.

   ![](assets/aem_uc_4.png)

1. Edite seu conteúdo de email adicionando componentes como, por exemplo, campos de personalização do Adobe Campaign.
1. When your email is ready, access the **[!UICONTROL Page information]** menu and click **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. From the first drop-down, select **[!UICONTROL Publish to Adobe Campaign]** as workflow model and click **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. Then, as the previous step, launch the **[!UICONTROL Approve for Campaign]** workflow.
1. Um aviso de isenção de responsabilidade aparece na parte superior da página. Click **[!UICONTROL Complete]** to confirm the review and click **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. Clique novamente **[!UICONTROL Complete]** e selecione **[!UICONTROL Newsletter approval]** no **[!UICONTROL Next Step]** menu suspenso.

   ![](assets/aem_uc_8.png)

Seu boletim informativo agora está pronto e sincronizado no Adobe Campaign.

**No Adobe Campaign:**

1. From the **[!UICONTROL Campaigns]** tab, click **[!UICONTROL Deliveries]** then **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. Na lista **[!UICONTROL Delivery template]** suspensa, selecione o **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** modelo.

   ![](assets/aem_uc_10.png)

1. Adicione um **[!UICONTROL Label]** ao delivery e clique em **[!UICONTROL Continue]**.
1. Clique no botão **[!UICONTROL Synchronize]**.

   Se esse botão não aparecer na interface, clique no botão **[!UICONTROL Properties]** e selecione a guia **[!UICONTROL Advanced]**. The **[!UICONTROL Content editing mode]** field should be set to **[!UICONTROL AEM]** with your AEM instance in the **[!UICONTROL AEM account]** field.

   ![](assets/aem_uc_11.png)

1. Selecione o delivery criado anteriormente no Adobe Experience Manager e clique em **[!UICONTROL Ok]**.
1. Clique no botão **[!UICONTROL Refresh content]** assim que algumas alterações forem feitas na entrega do AEM.

   ![](assets/aem_uc_12.png)

Seu email agora está pronto para ser enviado ao seu público.
