---
title: Configuração da integração com o Adobe Target
seo-title: Configuração da integração com o Adobe Target
description: Configuração da integração com o Adobe Target
seo-description: null
page-status-flag: never-activated
uuid: b9337e92-e4e5-4cba-a559-75db7460d5c5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-target
discoiquuid: 378d5ff9-88c0-43f1-beb8-454701e9f1d1
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Configuração da integração com o Adobe Target{#configuring-the-integration-with-adobe-target}

## Pré-requisitos {#prerequisites}

Para usar a integração entre o Adobe Campaign e o Adobe Target, você deve ter:

* Organizações do Adobe Experience Cloud e Adobe Target
* Um rawbox do Adobe Target especificado para estabelecer a conexão com o Adobe Campaign

## Configuração do Adobe Campaign {#configuring-adobe-campaign}

Para configurar o Adobe Campaign:

1. Instale o pacote padrão **[!UICONTROL Integration with the Adobe Experience Cloud]**. A instalação de um pacote de integração é a mesma instalação de um pacote padrão, que é detalhado na seção [Importação de pacotes. ](../../platform/using/working-with-data-packages.md#importing-packages) Isso dá acesso aos ativos compartilhados por meio do Digital Asset Manager.
1. Ative a conexão pelo IMS (serviço de conexão da Adobe ID) para usar imagens compartilhadas pela Adobe Experience Cloud em seus emails. Consulte a seção sobre [IMS](../../integrations/using/about-adobe-id.md).
1. Em **[!UICONTROL Administration > Platform > Options]**, configure as opções do servidor e da organização (locatário) para o Adobe Target:

   * **[!UICONTROL TNT_EdgeServer]**: servidor do Adobe Target usado para a integração. Essa opção é selecionada por padrão. Esse valor corresponde ao **[!UICONTROL Domain Server]** do Adobe Target, seguido pelo valor **/m2**. Por exemplo: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]**: Nome da organização do Adobe Target. Esse valor corresponde ao nome do **[!UICONTROL Client]** do Adobe Target.
   ![](assets/tar_options.png)

