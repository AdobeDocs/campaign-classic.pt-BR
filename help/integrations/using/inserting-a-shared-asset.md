---
title: Inserção de um ativo compartilhado
seo-title: Inserção de um ativo compartilhado
description: Inserção de um ativo compartilhado
seo-description: null
page-status-flag: never-activated
uuid: ab661bfd-d0a3-4b5c-ba52-4c76c834d584
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: asset-sharing
discoiquuid: 3d01cc7e-5685-4101-bf4b-ef5f6e52b3c9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Inserção de um ativo compartilhado{#inserting-a-shared-asset}

Os ativos compartilhados da Adobe Experience Cloud podem ser usados em seus emails e landing pages da seguinte maneira:

1. Crie um novo email ou uma nova landing page.

   Se você usar ativos da biblioteca do Adobe Experience Manager Assets, use um template de delivery criado ao [configurar a integração](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets).

   If you do not have this specific template, make sure that in the delivery **Properties**, the **[!UICONTROL Content editing mode]** (**[!UICONTROL Advanced]** tab) is set to **DCE** and that the AEM external account that you want to use for accessing your AEM Assets resource library is provided.

1. Na janela de edição, selecione a opção para adicionar uma imagem:

   * Se você estiver usando o modo [de edição](../../delivery/using/defining-the-email-content.md#adding-images)padrão, selecione **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

      ![](assets/dam_insert_image_standard.png)

   * If you are using the [advanced editing mode](../../web/using/about-campaign-html-editor.md) (DCE), go to an image block, then via the contextual menu, select **[!UICONTROL Select a shared asset]**.

      ![](assets/dam_insert_image_dce.png)

      >[!NOTE]
      >
      >Não é possível inserir imagens compartilhadas do Adobe Campaign no [acesso Web](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) ao usar DCE.

1. Na janela de seleção que é aberta, selecione uma imagem e depois confirme.

   As imagens disponíveis são da biblioteca da Adobe Experience Cloud ou da biblioteca do AEM Assets, dependendo de como a instância da Adobe Campaign é configurada. Consulte a seção [Configurar acesso aos ativos](../../integrations/using/configuring-access-to-assets.md) .

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>Se você usar a integração com o Adobe Target, poderá usar uma imagem compartilhada como uma imagem padrão. Consulte [esta página](../../integrations/using/integrating-with-adobe-target.md).

