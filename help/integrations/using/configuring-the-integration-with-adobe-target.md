---
product: campaign
title: Configuração da integração com o Adobe Target
description: Configuração da integração com o Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: b6e24c63ece12f25b7dafe3fede9e38b3aab2427
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 73%

---

# Configuração da integração com o Adobe Target{#configuring-the-integration-with-adobe-target}

![](../../assets/common.svg)


>[!CAUTION]
>
> Como cliente hospedado ou híbrido, entre em contato com o representante do Adobe para configurar essa integração. As etapas abaixo se aplicam somente a clientes locais.

## Pré-requisitos {#prerequisites}

Para usar a integração entre o Adobe Campaign e o Adobe Target, você deve ter:

* Organizações do Adobe Experience Cloud e Adobe Target
* Um rawbox do Adobe Target especificado para estabelecer a conexão com o Adobe Campaign

## Configuração do Adobe Campaign {#configuring-adobe-campaign}

Para configurar o Adobe Campaign:

1. Instale o **[!UICONTROL Integration with the Adobe Experience Cloud]** pacote integrado. [Saiba mais](../../platform/using/working-with-data-packages.md#importing-packages)

   Esse pacote fornece acesso aos ativos compartilhados por meio do Digital Asset Manager.

1. Ative a conexão pelo IMS (serviço de conexão da Adobe ID) para usar imagens compartilhadas pela Adobe Experience Cloud em seus emails. [Saiba mais](../../integrations/using/about-adobe-id.md)
1. Navegue até **[!UICONTROL Administration > Platform > Options]** para configurar as opções do servidor e da organização (locatário) para o Adobe Target:

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** : O servidor Adobe Target usado para a integração. Essa opção é selecionada por padrão. Esse valor corresponde ao **[!UICONTROL Domain Server]** do Adobe Target, seguido pelo valor **/m2**. Por exemplo: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : Nome da organização do Adobe Target. Esse valor corresponde ao nome do **[!UICONTROL Client]** do Adobe Target.


>[!CAUTION]
>
>Para arquiteturas híbridas e hospedadas, essas opções precisam ser instaladas em todos os servidores, incluindo o [servidor de mid-sourcing](../../installation/using/mid-sourcing-server.md) e a [instância de execução](../../message-center/using/configuring-instances.md#execution-instance).