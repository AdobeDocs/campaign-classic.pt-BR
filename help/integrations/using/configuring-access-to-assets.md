---
product: campaign
title: Configuração do acesso ao Assets
description: Configuração do acesso ao Assets
feature: Asset Sharing
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: ht
source-wordcount: '499'
ht-degree: 100%

---

# Configuração do acesso ao Assets {#configuring-access-to-assets}

Esta seção detalha as etapas de configuração necessárias no Adobe Campaign para usar as funcionalidades de integração com o Assets ou a biblioteca do Adobe Experience Manager Assets (AEM Assets).

>[!CAUTION]
>
>Essas integrações são simultâneas. Leia as informações a seguir cuidadosamente antes de fazer qualquer configuração.

* Integração com o **Experience Cloud Assets**: essa integração permite inserir imagens da biblioteca da Adobe Experience Cloud. Essa integração deve ser configurada instalando o pacote integrado **[!UICONTROL Integration with the Adobe Experience Cloud]** no Adobe Campaign.
* Integração com o **AEM Assets**: essa integração permite inserir imagens da biblioteca de ativos do Adobe Experience Manager. Essa integração deve ser configurada instalando o pacote integrado **[!UICONTROL AEM Integration]** no Adobe Campaign. Observe que essa integração não está mais disponível a partir do Adobe Experience Manager 6.4.

>[!NOTE]
>
>Se os dois pacotes (**[!UICONTROL AEM Integration]** e **[!UICONTROL Integration with the Adobe Experience Cloud]**) estiverem instalados, somente os ativos disponíveis na biblioteca da Adobe Experience Cloud poderão ser usados.

## Integração com ativos da Experience Cloud {#integrating-with-experience-cloud-assets}

Para usar a integração entre o Adobe Campaign e o Experience Cloud Assets, você deve ter:

* Uma organização da Adobe Experience Cloud
* Habilitação do modo de autenticação do Adobe IMS

Para habilitar a conexão entre o Adobe Campaign e a Adobe Experience Cloud, configure a conexão via IMS (serviço de conexão Adobe ID). Essa configuração é detalhada no documento [Conexão pela Adobe ID. ](../../integrations/using/about-adobe-id.md) Ela inclui:

* Instale o pacote **[!UICONTROL Integration with the Adobe Experience Cloud]**.
* Configuração de uma conta externa da Adobe Experience Cloud.

>[!NOTE]
>
>As funcionalidades vinculadas a essa integração estão disponíveis somente para usuários conectados com a Adobe ID pelo IMS.

## Integração com AEM Asstes {#integrating-with-aem-assets}


>[!CAUTION]
>
>Esse recurso foi descontinuado a partir do Adobe Experience Manager 6.4. [Saiba mais](https://experienceleague.adobe.com/pt-br/docs/experience-manager-64/release-notes/deprecated-removed-features#removed-features)

Para integrar o AEM Assets com o Adobe Campaign, você deve primeiro configurar a integração entre o Adobe Experience Manager e o Adobe Campaign. Esta configuração exige principalmente:

* Instalação do pacote integrado **[!UICONTROL AEM Integration]**
* Configuração de uma conta externa específica do Adobe Experience Manager

Saiba como integrar o Adobe Campaign e o Adobe Experience Manager na [documentação detalhada](../../integrations/using/about-adobe-experience-manager.md).

Depois de configurar essa integração, você pode configurar um novo modelo de entrega no Adobe Campaign para usar a biblioteca do AEM Assets. Para fazer isso, siga as etapas abaixo:

1. Crie um novo modelo de entrega ou duplique um existente. Consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-templates.html?lang=pt-BR){target="_blank"}.
1. Edite as **Propriedades** desse modelo.
1. Na guia **[!UICONTROL Advanced]**, defina o **[!UICONTROL Content editing mode]** para **DCE**.
1. Selecione a **[!UICONTROL AEM account]** externa que você precisa usar para acessar a biblioteca dos Ativos AEM.

   ![](assets/dam_aem_assets1.png)

Ao inserir imagens no conteúdo de uma entrega com base nesse modelo, a opção **[!UICONTROL Select a shared asset]** permite navegar pelas imagens na biblioteca dos Ativos AEM. Saiba mais [nesta seção](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Se o pacote de **[!UICONTROL Integration with the Adobe Experience Cloud]** também estiver instalado na sua instância do Adobe Campaign, você só poderá usar os ativos disponíveis na biblioteca da Adobe Experience Cloud. Para também acessar os ativos na sua biblioteca do AEM Assets, você deve sincronizar o AEM Assets e a Adobe Experience Cloud. Os ativos no AEM Assets também estarão disponíveis na biblioteca da Adobe Experience Cloud. Nesse caso, não é necessário criar um modelo da entrega específico.
