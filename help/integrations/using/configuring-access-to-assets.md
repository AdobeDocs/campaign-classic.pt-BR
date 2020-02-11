---
title: Configuração do acesso ao Assets
seo-title: Configuração do acesso ao Assets
description: Configuração do acesso ao Assets
seo-description: null
page-status-flag: never-activated
uuid: dc8c0016-92c8-41ab-98c6-d0fe0bfd6c41
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: asset-sharing
discoiquuid: df1b6ead-3471-404a-b43f-a68fb86cb14c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Configuração do acesso ao Assets{#configuring-access-to-assets}

Esta seção detalha as etapas de configuração necessárias no Adobe Campaign para usar as funcionalidades de integração com o Serviço principal de ativos ou a biblioteca do Adobe Experience Manager Assets.

>[!CAUTION]
>
>Essas integrações são simultâneas. Leia as informações a seguir cuidadosamente antes de fazer qualquer configuração.

* Integração com o **Experience Cloud
          Assets**: essa integração permite inserir imagens da biblioteca da Adobe
          Experience Cloud. Dependendo da configuração e do modelo de licença, essa biblioteca pode ser o 
          Serviço Principal de Ativos ou Ativos por Demanda. This integration must be set up by installing the **[!UICONTROL Integration with the Adobe Experience Cloud]** built-in package in Adobe Campaign.
* Integração com o **AEM Assets**: essa integração permite inserir imagens da biblioteca do Adobe Experience Manager Assets. This integration must be set up by installing the **[!UICONTROL AEM Integration]** built-in package in Adobe Campaign.

>[!NOTE]
>
>If the two packages (**[!UICONTROL AEM Integration]** and **[!UICONTROL Integration with the Adobe Experience Cloud]** ) are installed, only the assets available in the Adobe Experience Cloud library can be used. Para também acessar os ativos na sua 
              biblioteca do AEM Assets, você deve sincronizar o AEM Assets e a Adobe Experience Cloud. Os
             ativos no AEM Assets também estarão disponíveis na biblioteca da Adobe Experience
             Cloud. Para obter mais informações sobre como sincronizar o AEM Assets e a Adobe Experience Cloud, consulte a [documentação detalhada](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html).

## Integração com Experience Cloud Assets {#integrating-with-experience-cloud-assets}

Para usar a integração entre o Adobe Campaign e o Experience Cloud Assets, você deve ter:

* Uma organização da Adobe Experience Cloud
* O modo de autenticação IMS da Adobe habilitado

Para habilitar a conexão entre o Adobe Campaign e a Adobe Experience Cloud, configure a conexão via IMS (serviço de conexão Adobe ID). Essa configuração é detalhada no documento [Conexão pela Adobe ID. ](../../integrations/using/about-adobe-id.md) Ela inclui:

* Installing the **[!UICONTROL Integration with the Adobe Experience Cloud]** package.
* Configuração de uma conta externa da Adobe Experience Cloud.

>[!NOTE]
>
>As funcionalidades vinculadas a essa integração estão disponíveis somente para usuários conectados com a Adobe ID pelo IMS.

## Integração com AEM Asstes {#integrating-with-aem-assets}

Para integrar o AEM Assets com o Adobe Campaign, você deve primeiro configurar a integração entre o Adobe Experience Manager e o Adobe Campaign. Esta configuração exige principalmente:

* Instalação do pacote **[!UICONTROL AEM Integration]** integrado
* Configuração de uma conta externa específica do Adobe Experience Manager

Saiba como integrar o Adobe Campaign e o Adobe Experience Manager na [documentação detalhada](../../integrations/using/about-adobe-experience-manager.md).

Depois de configurar essa integração, você pode configurar um novo template de delivery no Adobe Campaign para usar a biblioteca do AEM Assets. Para fazer isso, siga as etapas abaixo:

1. Crie um novo template de delivery ou duplique um existente. Para obter mais informações sobre templates de Delivery, consulte [esta página](../../delivery/using/about-templates.md).
1. Edite as **Propriedades** desse template.
1. Na **[!UICONTROL Advanced]** guia, defina **[!UICONTROL Content editing mode]** como **DCE**.
1. Select the external **[!UICONTROL AEM account]** that you need to use to access your AEM Assets library.

   ![](assets/dam_aem_assets1.png)

When you insert images into a delivery&#39;s content based on this template, the **[!UICONTROL Select a shared asset]** option will then allow you to browse images in the AEM Assets library. Saiba mais [nesta seção](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>If the **[!UICONTROL Integration with the Adobe Experience Cloud]** package is also installed on your Adobe Campaign instance, you will only be able to use the assets available in the Adobe Experience Cloud library. Para também acessar os ativos na sua 
              biblioteca do AEM Assets, você deve sincronizar o AEM Assets e a Adobe Experience Cloud. Os
             ativos no AEM Assets também estarão disponíveis na biblioteca da Adobe Experience
             Cloud. Nesse caso, não é necessário criar um template de delivery 
         específico. Para obter mais informações sobre como sincronizar o AEM Assets e a Adobe Experience Cloud, consulte a [documentação detalhada](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html).

