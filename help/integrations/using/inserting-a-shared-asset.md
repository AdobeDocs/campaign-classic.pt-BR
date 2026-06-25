---
product: campaign
title: Inserção de um ativo compartilhado
description: Inserção de um ativo compartilhado
feature: Asset Sharing
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: 30a94bce-6d96-4a6d-a62f-7451c822f0e3
TQID: https://experienceleague.adobe.com/5SrvIw1sYSNd4Hw1we554AfxDj3VgeTeqIOOzTTrWuY
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 233
ht-degree: 100%

---

# Inserção de um ativo compartilhado{#inserting-a-shared-asset}

Os ativos compartilhados da Adobe Experience Cloud podem ser usados em seus emails e páginas de destino da seguinte maneira:

1. Crie um novo email ou uma nova página de destino.

   Se você usar ativos da biblioteca do Adobe Experience Manager Assets, use um modelo de entrega criado ao [configurar a integração](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets).

   Se não tiver esse modelo específico, assegure-se de que nas **Propriedades** da entrega a **[!UICONTROL Content editing mode]** (guia **[!UICONTROL Advanced]**) esteja definida como **DCE** e que a conta externa do AEM usada para acessar a biblioteca de recursos do AEM Assets seja fornecida.

1. Na janela de edição, selecione a opção para adicionar uma imagem:

   * Se estiver usando o [modo de edição padrão](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/emails/defining-the-email-content#adding-images){target="_blank"}, selecione **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

     ![](assets/dam_insert_image_standard.png)

   * Se estiver usando o [modo de edição avançado](../../web/using/about-campaign-html-editor.md) (DCE), vá para um bloco de imagem e, por meio do menu contextual, selecione **[!UICONTROL Select a shared asset]**.

     ![](assets/dam_insert_image_dce.png)

     >[!NOTE]
     >
     >Não é possível inserir imagens compartilhadas do Adobe Campaign no [acesso Web](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) ao usar DCE.

1. Na janela de seleção que é aberta, selecione uma imagem e depois confirme.

   As imagens disponíveis são da biblioteca da Adobe Experience Cloud ou da biblioteca do AEM Assets, dependendo de como a instância da Adobe Campaign é configurada. Consulte a seção [Configurar acesso ao Assets](../../integrations/using/configuring-access-to-assets.md).

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>Se você usar a integração com o Adobe Target, poderá usar uma imagem compartilhada como uma imagem padrão. Consulte [esta página](../../integrations/using/integrating-with-adobe-target.md).
