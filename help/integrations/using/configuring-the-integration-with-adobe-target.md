---
product: campaign
title: Configurar a integração com o Adobe Target
description: Saiba como configurar a integração com o Adobe Target
feature: Target Integration
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
TQID: https://experienceleague.adobe.com/k6TljRgymSefOITPaogJdR7HOrl1BnnZm9jbkemrcyg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 198
ht-degree: 100%

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

1. Habilite a conexão pelo IMS (serviço de conexão da Adobe ID) para usar imagens compartilhadas pela Adobe Experience Cloud em seus emails. [Saiba mais](../../integrations/using/about-adobe-id.md)
1. Navegue até **[!UICONTROL Administration > Platform > Options]** para configurar as opções de servidor e organização (Locatário) do Adobe Target:

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** : O servidor Adobe Target usado para a integração. Essa opção é selecionada por padrão. Esse valor corresponde ao **[!UICONTROL Domain Server]** do Adobe Target, seguido pelo valor **/m2**. Por exemplo: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : Nome da organização do Adobe Target. Esse valor corresponde ao nome do **[!UICONTROL Client]** do Adobe Target.


>[!CAUTION]
>
>Para arquiteturas híbridas e hospedadas, essas opções precisam ser instaladas em todos os servidores, incluindo o [servidor de mid-sourcing](../../installation/using/mid-sourcing-server.md) e a [instância de execução](../../message-center/using/configuring-instances.md#execution-instance).