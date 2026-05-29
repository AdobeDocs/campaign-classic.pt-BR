---
product: campaign
title: Criação de boletim informativo no Experience Manager
description: Criação de boletim informativo no Experience Manager
feature: Experience Manager Integration
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: integrations
content-type: reference
exl-id: 9fa3ce08-3007-4c65-9841-bad339428b7c
TQID: https://experienceleague.adobe.com/-5orLjm8w8PjA4t4Swox55NP2MTw3rGZzGq42JwuzeQ
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 288
ht-degree: 100%

---

# Criação de boletim informativo no Experience Manager{#creating-an-experience-manager-newsletter}



Essa integração pode ser usada para criar um boletim informativo no Adobe Experience Manager que será usado no Adobe Campaign como parte de uma campanha de email.

**No Adobe Experience Manager:**

1. Na instância de criação do AEM, clique no logotipo do **Adobe Experience** no lado superior esquerdo da página e selecione **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. Selecione **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**.
1. Clique no botão **[!UICONTROL Create]** no lado superior direito da página e selecione **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. Selecione o modelo **[!UICONTROL Adobe Campaign Email (AC 6.1)]** e nomeie o informativo.
1. Depois que a página é criada, acesse o menu **[!UICONTROL Page information]** e clique em **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. Na guia **[!UICONTROL Cloud Services]**, selecione **[!UICONTROL Adobe Campaign]** como **[!UICONTROL Cloud service configuration]** e sua instância do Adobe Campaign na segunda lista suspensa.

   ![](assets/aem_uc_4.png)

1. Edite seu conteúdo de email adicionando componentes, por exemplo, campos de personalização do Adobe Campaign.
1. Com o email pronto, acesse o menu **[!UICONTROL Page information]** e clique em **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. Na primeira lista suspensa, selecione **[!UICONTROL Publish to Adobe Campaign]** como modelo de fluxo de trabalho e clique em **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. Em seguida, como a etapa anterior, inicie o fluxo de trabalho **[!UICONTROL Approve for Campaign]**.
1. Um aviso de isenção de responsabilidade aparece na parte superior da página. Clique em **[!UICONTROL Complete]** para confirmar a revisão e clique em **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. Clique novamente em **[!UICONTROL Complete]** e selecione **[!UICONTROL Newsletter approval]** no menu suspenso **[!UICONTROL Next Step]**.

   ![](assets/aem_uc_8.png)

Seu boletim informativo agora está pronto e sincronizado no Adobe Campaign.

**No Adobe Campaign:**

1. Na guia **[!UICONTROL Campaigns]**, clique em **[!UICONTROL Deliveries]** e em **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. No menu suspenso **[!UICONTROL Delivery template]**, selecione o modelo **[!UICONTROL Email delivery with AEM content (mailAEMContent)]**.

   ![](assets/aem_uc_10.png)

1. Adicione um **[!UICONTROL Label]** à entrega e clique em **[!UICONTROL Continue]**.
1. Clique no botão **[!UICONTROL Synchronize]**.

   Se esse botão não aparecer na interface, clique no botão **[!UICONTROL Properties]** e selecione a guia **[!UICONTROL Advanced]**. O campo **[!UICONTROL Content editing mode]** deve ser definido no **[!UICONTROL AEM]** com sua instância do AEM no campo **[!UICONTROL AEM account]**.

   ![](assets/aem_uc_11.png)

1. Selecione a entrega criada anteriormente no Adobe Experience Manager e clique em **[!UICONTROL Ok]**.
1. Clique no botão **[!UICONTROL Refresh content]** assim que algumas alterações forem feitas na entrega do AEM.

   ![](assets/aem_uc_12.png)

O email agora está pronto para ser enviado ao seu público-alvo.
