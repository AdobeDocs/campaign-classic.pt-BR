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
translation-type: ht
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Criação de boletim informativo no Experience Manager{#creating-an-experience-manager-newsletter}

Essa integração pode ser usada para criar um boletim informativo no Adobe Experience Manager que será usado no Adobe Campaign como parte de uma campanha de email.

Para obter um exemplo mais detalhado sobre como usar essa integração, consulte este [guia com o passo a passo](https://helpx.adobe.com/br/campaign/kb/acc-aem.html).

**No Adobe Experience Manager:**

1. Na instância do autor do AEM, clique no logotipo **Adobe Experience** no lado superior esquerdo da página e selecione **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. Selecione **[!UICONTROL Campaigns > Name of your brand (aqui We.Retail) > Master Area > Email campaigns]**.
1. Clique no botão **[!UICONTROL Create]** no lado superior direito da página e selecione **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. Selecione o modelo do **[!UICONTROL Email do Adobe Campaign (AC 6.1)]** e nomeie o informativo.
1. Depois que a página é criada, acesse o menu **[!UICONTROL Page information]** e clique em **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. Na guia **[!UICONTROL Cloud Services]**, selecione **[!UICONTROL Adobe Campaign]** como **[!UICONTROL Cloud service configuration]** e sua instância do Adobe Campaign na segunda lista suspensa.

   ![](assets/aem_uc_4.png)

1. Edite seu conteúdo de email adicionando componentes como, por exemplo, campos de personalização do Adobe Campaign.
1. Com o email pronto, acesse o menu **[!UICONTROL Page information]** e clique em **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. Na primeira lista suspensa, selecione **[!UICONTROL Publish to Adobe Campaign]** como modelo de fluxo de trabalho e clique em **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. Em seguida, como a etapa anterior, inicie o fluxo de trabalho **[!UICONTROL Approve for Campaign]**.
1. Um aviso de isenção de responsabilidade aparece na parte superior da página. Clique em **[!UICONTROL Complete]** para confirmar a revisão e clique em **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. Clique novamente em **[!UICONTROL Complete]** e selecione a **[!UICONTROL Newsletter approval]** na lista suspensa **[!UICONTROL Next Step]**.

   ![](assets/aem_uc_8.png)

Seu boletim informativo agora está pronto e sincronizado no Adobe Campaign.

**No Adobe Campaign:**

1. Na guia **[!UICONTROL Campaigns]**, clique em **[!UICONTROL Deliveries]** e, em seguida, **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. Na lista suspensa **[!UICONTROL Delivery template]**, selecione o modelo **[!UICONTROL Email delivery with AEM content (mailAEMContent)]**.

   ![](assets/aem_uc_10.png)

1. Adicione um **[!UICONTROL Label]** ao delivery e clique em **[!UICONTROL Continue]**.
1. Clique no botão **[!UICONTROL Synchronize]**.

   Se esse botão não aparecer na interface, clique no botão **[!UICONTROL Properties]** e selecione a guia **[!UICONTROL Advanced]**. O campo **[!UICONTROL Content editing mode]** deve ser definido no **[!UICONTROL AEM]** com sua instância de AEM no campo **[!UICONTROL AEM account]**.

   ![](assets/aem_uc_11.png)

1. Selecione o delivery criado anteriormente no Adobe Experience Manager e clique em **[!UICONTROL Ok]**.
1. Clique no botão **[!UICONTROL Refresh content]** assim que algumas alterações forem feitas na entrega do AEM.

   ![](assets/aem_uc_12.png)

Seu email agora está pronto para ser enviado ao seu público.
