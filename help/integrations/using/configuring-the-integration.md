---
title: Configuração da integração
seo-title: Configuração da integração
description: Configuração da integração
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 31f30db6eaf1fee43f9f757124e3fa8ed1d0075f

---


# Configuração da integração{#configuring-the-integration}

## Configuração no Adobe Campaign {#configuring-in-adobe-campaign}

Para usar essas duas soluções em conjunto, você deve configurá-las para se conectarem.

Siga as etapas abaixo para iniciar a configuração no Adobe Campaign:

1. [Instale o pacote de integração do AEM no Adobe Campaign.](#install-the-aem-integration-package-in-adobe-campaign)
1. [Configuração da conta externa](#configure-the-external-account)
1. [Configuração da filtragem de recursos do AEM](#configure-aem-resources-filtering)

Para configurações avançadas como gestão de campos e blocos de personalização. Consulte a [documentação](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html) do Adobe Experience Manager.

### Instale o pacote de integração do AEM no Adobe Campaign.{#install-the-aem-integration-package-in-adobe-campaign}

You first need to install the **[!UICONTROL AEM integration]** package.

1. From your Adobe Campaign instance, select **[!UICONTROL Tools]** from the upper toolbar.
1. Select **[!UICONTROL Tools > Advanced > Import package...]**.

   ![](assets/aem_config_1.png)

1. Select **[!UICONTROL Install a standard package]**.
1. Marque **[!UICONTROL AEM integration]** e clique no **[!UICONTROL Next]** botão.

   ![](assets/aem_config_2.png)

1. In the next window, click the **[!UICONTROL Start]** button to start the installation of your package. Feche a janela após finalizar a instalação.

### Configuração da zona de segurança para o operador do AEM {#configure-the-security-zone-for-aem-operator}

O **[!UICONTROL AEM integration]** pacote define o operador **[!UICONTROL aemserver]** no Campaign. Este operador será usado para conectar o servidor do Adobe Experience Manager ao Adobe Campaign.

É necessário configurar uma zona de segurança para este operador se conectar ao Adobe Campaign pelo Adobe Experience Manager.

>[!CAUTION]
>
>É altamente recomendável criar uma zona de segurança dedicada ao AEM para evitar problemas de segurança. Para obter mais informações, consulte o [Guia](../../installation/using/configuring-campaign-server.md#defining-security-zones) de instalação.

Se a sua instância do Campaign for hospedada pela Adobe, entre em contato com a equipe de suporte da Adobe. Se você estiver usando o Campaign no local, siga as etapas abaixo:

1. Abra o arquivo de configuração **serverConf.xml**.
1. Acesse o atributo **allowUserPassword** da zona de segurança selecionada e configure-o como  **true**.

   Isso permitirá que o Adobe Experience Manager se conecte ao Adobe Campaign pelo login/senha.

### Configuração da conta externa {#configure-the-external-account}

The **[!UICONTROL AEM integration]** package created the external account for Adobe Experience Cloud. É necessário configurá-lo agora para se conectar com a sua instância do Adobe Experience Manager.

Para configurar a conta externa do AEM, siga as etapas abaixo:

1. Clique no botão **[!UICONTROL Explorer]**.

   ![](assets/aem_config_3.png)

1. Select **[!UICONTROL Administration > Platform > External accounts]**.
1. Na **[!UICONTROL External account]** lista, selecione **[!UICONTROL AEM instance]**.
1. Insira os parâmetros para sua instância de criação do AEM:

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**
   >[!NOTE]
   >
   >Make sure that your **[!UICONTROL Server]** address does not end with a a trailing slash.

   ![](assets/aem_config_4.png)

1. Marque a **[!UICONTROL Enabled]** caixa.
1. Clique no botão **[!UICONTROL Save]**.

### Configuração da filtragem de recursos do AEM {#configure-aem-resources-filtering}

A opção **AEMResourceTypeFilter**&#x200B;é usada para filtrar tipos de recursos do Experience Manager que podem ser usados no Adobe Campaign. Isso permite que o Adobe Campaign recupere o conteúdo do Experience Manager especificamente projetado para ser usado somente no Adobe Campaign.

To check if the **[!UICONTROL AEMResourceTypeFilter]** option is configured:

1. Clique no botão **[!UICONTROL Explorer]**.
1. Select **[!UICONTROL Administration > Platform > Options]**.
1. Na **[!UICONTROL Options]** lista, selecione **[!UICONTROL AEMResourceTypeFilter]**.
1. In the **[!UICONTROL Value (text)]** field, the path should be as follows:

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   Ou em alguns casos:

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## Configuração no Adobe Experience Manager {#configuring-in-adobe-experience-manager}

Siga as etapas abaixo para iniciar a configuração no Adobe Experience Manager:

1. Configure a **replicação** para replicar da instância de criação do AEM para a instância de publicação do AEM.

   Para saber como configurar a replicação, consulte a [documentação](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html) do Adobe Experience Manager.

1. Instale o **FeaturePack** de integração na sua instância de criação e, em seguida, replique a instalação na sua instância de publicação. (Somente para versões 5.6.1 e 6.0 do AEM).

   Para saber como instalar o FeaturePack, consulte a [documentação](https://helpx.adobe.com/experience-manager/aem-previous-versions.html) do Adobe Experience Manager.

1. Conecte o Adobe Experience Manager ao Adobe Campaign configurando um **Serviço na Nuvem** dedicado.

   Para saber como conectar ambas as soluções pelos Serviços na Nuvem, consulte a [documentação](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) do Adobe Experience Manager .

1. Configure o **serviço Externalizador**.

   Para saber como configurá-lo, consulte a [documentação](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html) do Adobe Experience Manager.

