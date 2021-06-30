---
product: campaign
title: Configuração do acesso ao Assets
description: Configuração do acesso ao Assets
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: ht
source-wordcount: '508'
ht-degree: 100%

---

# Configuração do acesso ao Assets{#configuring-access-to-assets}

Esta seção detalha as etapas de configuração necessárias no Adobe Campaign para usar as funcionalidades de integração com o Serviço principal de ativos ou a biblioteca do Adobe Experience Manager Assets.

>[!CAUTION]
>
>Essas integrações são simultâneas. Leia as informações a seguir cuidadosamente antes de fazer qualquer configuração.

* Integração com o **Experience Cloud Assets**: essa integração permite inserir imagens da biblioteca da Adobe Experience Cloud. Dependendo da configuração e do modelo de licença, essa biblioteca pode ser o Serviço Principal de Ativos ou Assets on Demand. Essa integração deve ser configurada instalando o pacote integrado **[!UICONTROL Integration with the Adobe Experience Cloud]** no Adobe Campaign.
* Integração com o **AEM Assets**: essa integração permite inserir imagens da biblioteca do Adobe Experience Manager Assets. Essa integração deve ser configurada instalando o pacote integrado **[!UICONTROL AEM Integration]** no Adobe Campaign.

>[!NOTE]
>
>Se os dois pacotes (**[!UICONTROL AEM Integration]** e **[!UICONTROL Integration with the Adobe Experience Cloud]**) estiverem instalados, somente os ativos disponíveis na biblioteca da Adobe Experience Cloud poderão ser usados.

## Integração com Experience Cloud Assets {#integrating-with-experience-cloud-assets}

Para usar a integração entre o Adobe Campaign e o Experience Cloud Assets, você deve ter:

* Uma organização da Adobe Experience Cloud
* O modo de autenticação IMS da Adobe habilitado

Para habilitar a conexão entre o Adobe Campaign e a Adobe Experience Cloud, configure a conexão via IMS (serviço de conexão Adobe ID). Essa configuração é detalhada no documento [Conexão pela Adobe ID. ](../../integrations/using/about-adobe-id.md) Ela inclui:

* Instale o pacote **[!UICONTROL Integration with the Adobe Experience Cloud]**.
* Configuração de uma conta externa da Adobe Experience Cloud.

>[!NOTE]
>
>As funcionalidades vinculadas a essa integração estão disponíveis somente para usuários conectados com a Adobe ID pelo IMS.

## Integração com AEM Asstes {#integrating-with-aem-assets}

Para integrar o AEM Assets com o Adobe Campaign, você deve primeiro configurar a integração entre o Adobe Experience Manager e o Adobe Campaign. Esta configuração exige principalmente:

* Instalação do pacote interno **[!UICONTROL AEM Integration]**
* Configuração de uma conta externa específica do Adobe Experience Manager

Saiba como integrar o Adobe Campaign e o Adobe Experience Manager na [documentação detalhada](../../integrations/using/about-adobe-experience-manager.md).

Depois de configurar essa integração, você pode configurar um novo template de delivery no Adobe Campaign para usar a biblioteca do AEM Assets. Para fazer isso, siga as etapas abaixo:

1. Crie um novo template de delivery ou duplique um existente. Para obter mais informações sobre templates de Delivery, consulte [esta página](../../delivery/using/about-templates.md).
1. Edite as **Propriedades** desse template.
1. Na guia **[!UICONTROL Advanced]**, defina o **[!UICONTROL Content editing mode]** para **DCE**.
1. Selecione a **[!UICONTROL AEM account]** externa que você precisa usar para acessar a biblioteca dos Ativos AEM.

   ![](assets/dam_aem_assets1.png)

Ao inserir imagens no conteúdo de um delivery com base nesse modelo, a opção **[!UICONTROL Select a shared asset]** permite navegar pelas imagens na biblioteca dos Ativos AEM. Saiba mais [nesta seção](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Se o pacote de **[!UICONTROL Integration with the Adobe Experience Cloud]** também estiver instalado na sua instância do Adobe Campaign, você só poderá usar os ativos disponíveis na biblioteca da Adobe Experience Cloud. Para também acessar os ativos na sua biblioteca do AEM Assets, você deve sincronizar o AEM Assets e a Adobe Experience Cloud. Os ativos no AEM Assets também estarão disponíveis na biblioteca da Adobe Experience Cloud. Nesse caso, não é necessário criar um template de delivery específico. Para obter mais informações sobre como sincronizar o AEM Assets e a Adobe Experience Cloud, consulte a [documentação detalhada](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/configure-assets-cc-integration.html?lang=pt-BR#integration).
