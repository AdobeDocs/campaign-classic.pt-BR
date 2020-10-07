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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 90%

---


# Configuração da integração de públicos compartilhados no Adobe Campaign{#configuring-shared-audiences-integration-in-adobe-campaign}

Depois do envio dessa solicitação, a Adobe continuará a provisionar a integração e irá entrar em contato para fornecer detalhes e informações para você finalizar a configuração:

1. [Etapa 1: configurar ou verificar as contas externas no Adobe Campaign](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [Etapa 2: configurar a fonte de dados](#step-2--configure-the-data-source)
1. [Etapa 3: configurar o servidor de rastreamento do Campaign](#step-3--configure-campaign-tracking-server)
1. [Etapa 4: configurar o Serviço de ID de visitante](#step-4--configure-the-visitor-id-service)

## Etapa 1: configurar ou verificar as contas externas no Adobe Campaign {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

Primeiro, precisamos configurar ou verificar as contas externas no Adobe Campaign como descrito a seguir:

1. Clique no ícone **[!UICONTROL Explorer]**.
1. Vá para **[!UICONTROL Administration > Platform > External accounts]**. As contas SFTP mencionadas devem ter sido configuradas pela Adobe e as informações necessárias devem ter sido comunicadas a você.

   * **[!UICONTROL importSharedAudience]**: conta SFTP dedicada à importação de públicos.
   * **[!UICONTROL exportSharedAudience]**: conta SFTP dedicada à exportação de públicos.

   ![](assets/aam_config_1.png)

1. Preencha o campo **[!UICONTROL Server]**: domínio **ftp-out.demdex.com** para a conta externa de importação e domínio **ftp-in.demdex.com** para a conta externa de exportação.

   Lembre-se de que uma exportação do Campaign é uma importação para o Audience Manager ou o Serviço principal de pessoas.

   >[!NOTE]
   >
   >If you are using S3, enter your **[!UICONTROL AWS S3 Account Server]** following this syntax:
   >
   >`<S3bucket name>.s3.amazonaws.com/<s3object path>`
   >
   >Para obter mais informações sobre como configurar sua conta S3, consulte esta [página](../../platform/using/external-accounts.md#amazon-simple-storage-service--s3--external-account).

   ![](assets/aam_config_2.png)

1. Add the **[!UICONTROL Account]** and **[!UICONTROL Password]** provided by Adobe.

Suas contas externas estão configuradas.

## Etapa 2: configurar a Fonte de Dados {#step-2--configure-the-data-source}

A **ID do Visitante – Recipient** é criada no Audience Manager. Esta é uma fonte de dados pronta para uso configurada por padrão para a ID do Visitante. Os segmentos criados a partir do Campaign farão parte dessa fonte de dados.

To configure the **[!UICONTROL Recipient - Visitor ID]** data source:

1. From the **[!UICONTROL Explorer]** node, select **[!UICONTROL Administration > Platform > AMC Data sources]**.
1. Selecione **[!UICONTROL Recipient - Visitor ID]**.
1. Digite o **[!UICONTROL Data Source ID]** e **[!UICONTROL AAM Destination ID]** fornecido pelo Adobe.

   ![](assets/aam_config_3.png)

## Etapa 3: configurar o servidor de rastreamento do Campaign {#step-3--configure-campaign-tracking-server}

Para a configuração da integração com o Serviço Principal de Pessoas ou o Audience Manager, também é necessário configurar o servidor de rastreamento do Campaign.

Certifique-se de que o Servidor de Rastreamento do Campaign está registrado no domínio (CNAME). Você pode encontrar mais informações sobre delegação de nome de domínio [neste artigo](https://helpx.adobe.com/br/campaign/kb/domain-name-delegation.html).

## Etapa 4: configurar o Serviço de ID de visitante {#step-4--configure-the-visitor-id-service}

Se o serviço de ID do visitante nunca foi configurado em suas propriedades da Web ou sites, consulte este [documento](https://docs.adobe.com/content/help/en/id-service/using/implementation/setup-aam-analytics.html) para saber como configurar o serviço ou este [vídeo](https://helpx.adobe.com/marketing-cloud/how-to/email-marketing.html#step-two).

Sua configuração e provisionamento estão finalizados, a integração agora pode ser usada para importar e exportar públicos ou segmentos.
