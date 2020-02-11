---
title: Configuração da integração de públicos compartilhados no Adobe Campaign
seo-title: Configuração da integração de públicos compartilhados no Adobe Campaign
description: Configuração da integração de públicos compartilhados no Adobe Campaign
seo-description: null
page-status-flag: never-activated
uuid: 6ed137e4-027f-4eb0-a0b5-4beb7deef51f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 4443b0ca-80c6-467d-a4df-50864aae8496
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6ae45cbd87fc0152fc654202e03501fc8d2abd06

---


# Configuração da integração de públicos compartilhados no Adobe Campaign{#configuring-shared-audiences-integration-in-adobe-campaign}

Depois do envio dessa solicitação, a Adobe continuará a provisionar a integração e irá entrar em contato para fornecer detalhes e informações para você finalizar a configuração:

1. [Etapa 1: Configurar ou verificar as contas externas no Adobe Campaign](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [Etapa 2: Configurar a fonte de dados](#step-2--configure-the-data-source)
1. [Etapa 3: Configurar o servidor de rastreamento de campanha](#step-3--configure-campaign-tracking-server)
1. [Etapa 4: Configurar o serviço de ID de visitante](#step-4--configure-the-visitor-id-service)

## Step 1: Configure or check the external accounts in Adobe Campaign {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

Primeiro, precisamos configurar ou verificar as contas externas no Adobe Campaign como descrito a seguir:

1. Clique no **[!UICONTROL Explorer]** ícone.
1. Vá para **[!UICONTROL Administration > Platform > External accounts]**. As contas SFTP mencionadas devem ter sido configuradas pela Adobe e as informações necessárias devem ter sido comunicadas a você.

   * **[!UICONTROL importSharedAudience]** : Conta SFTP dedicada à importação de audiências.
   * **[!UICONTROL exportSharedAudience]** : Conta SFTP dedicada à exportação de audiências.
   ![](assets/aam_config_1.png)

1. Fill in the **[!UICONTROL Server]** field: **ftp-out.demdex.com** domain for the import external account and **ftp-in.demdex.com** domain for the export external account.

   Lembre-se de que uma exportação do Campaign é uma importação para o Audience Manager ou o Serviço principal de pessoas.

   >[!NOTE]
   >
   >Se você estiver usando S3, insira a **[!UICONTROL AWS S3 Account Server]** seguinte sintaxe:\
   `<S3bucket name>.s3.amazonaws.com/<s3object path>`\
   For more information on how to configure your S3 account, refer to this [page](../../platform/using/external-accounts.md#amazon-simple-storage-service--s3--external-account).

   ![](assets/aam_config_2.png)

1. Adicione o **[!UICONTROL Account]** e **[!UICONTROL Password]** fornecido pela Adobe.

Suas contas externas estão configuradas.

## Step 2: Configure the Data Source {#step-2--configure-the-data-source}

A **ID do Visitante – Recipient** é criada no Audience Manager. Esta é uma fonte de dados pronta para uso configurada por padrão para a ID do Visitante. Os segmentos criados a partir do Campaign farão parte dessa fonte de dados.

To configure the **[!UICONTROL Recipient - Visitor ID]** data source:

1. No **[!UICONTROL Explorer]** nó, selecione **[!UICONTROL Administration > Platform > AMC Data sources]**.
1. Select **[!UICONTROL Recipient - Visitor ID]**.
1. Digite o **[!UICONTROL Data Source ID]** e **[!UICONTROL AAM Destination ID]** fornecido pela Adobe.

   ![](assets/aam_config_3.png)

## Step 3: Configure Campaign Tracking server {#step-3--configure-campaign-tracking-server}

Para a configuração da integração com o Serviço Principal de Pessoas ou o Audience Manager, também é necessário configurar o servidor de rastreamento do Campaign.

Certifique-se de que o Servidor de Rastreamento do Campaign está registrado no domínio (CNAME). Você pode encontrar mais informações sobre delegação de nome de domínio [neste artigo](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html).

## Step 4: Configure the Visitor ID Service {#step-4--configure-the-visitor-id-service}

Se o serviço de ID do visitante nunca foi configurado em suas propriedades da Web ou sites, consulte este [documento](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-setup-aam-analytics.html) para saber como configurar o serviço ou este [vídeo](https://helpx.adobe.com/marketing-cloud/how-to/email-marketing.html#step-two).

Sua configuração e provisionamento estão finalizados, a integração agora pode ser usada para importar e exportar públicos ou segmentos.
