---
product: campaign
title: Configurar a integração com o Adobe Target
description: Saiba como configurar a integração com o Adobe Target
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 95%

---

# Configurar a integração com o Adobe Target{#configuring-the-integration-with-adobe-target}




>[!CAUTION]
>
> Como cliente hospedado ou híbrido, entre em contato com o seu representante da Adobe para configurar essa integração. As etapas abaixo se aplicam somente a clientes no local.

Essa integração exige:

* Organizações do Adobe Experience Cloud e Adobe Target
* Um rawbox do Adobe Target especificado para estabelecer a conexão com o Adobe Campaign

Para configurar essa integração no Adobe Campaign, siga as etapas abaixo:

1. Instale o pacote integrado **[!UICONTROL Integration with the Adobe Experience Cloud]**. [Saiba mais](../../platform/using/working-with-data-packages.md#importing-packages)

   Com este pacote, você tem acesso aos ativos compartilhados por meio do Digital Asset Manager.

1. Ative a conexão pelo IMS (serviço de conexão da Adobe ID) para usar imagens compartilhadas pela Adobe Experience Cloud em seus emails. [Saiba mais](../../integrations/using/about-adobe-id.md)
1. Navegue até **[!UICONTROL Administration > Platform > Options]** para configurar as opções de servidor e organização (Locatário) do Adobe Target: 

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** : O servidor Adobe Target usado para a integração. Essa opção é selecionada por padrão. Esse valor corresponde ao **[!UICONTROL Domain Server]** do Adobe Target, seguido pelo valor **/m2**. Por exemplo: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : Nome da organização do Adobe Target. Esse valor corresponde ao nome do **[!UICONTROL Client]** do Adobe Target.


>[!CAUTION]
>
>Para arquiteturas híbridas e hospedadas, essas opções precisam ser instaladas em todos os servidores, incluindo o [servidor de mid-sourcing](../../installation/using/mid-sourcing-server.md) e a [instância de execução](../../message-center/using/configuring-instances.md#execution-instance).