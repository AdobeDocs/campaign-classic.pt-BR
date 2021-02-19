---
solution: Campaign Classic
product: campaign
title: Compartilhamento de públicos com a Adobe Experience Cloud
description: Compartilhamento de públicos com a Adobe Experience Cloud
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 100%

---


# Compartilhamento de públicos com a Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!CAUTION]
>
>Para compartilhar públicos com as soluções da Adobe Experience Cloud, é necessário implementar o Adobe Identity Management System. i [Saiba mais sobre o IMS](../../integrations/using/about-adobe-id.md).

Com o Adobe Campaign, você pode compartilhar públicos e segmentos com as soluções Adobe Experience Cloud e os serviços principais. Estão disponíveis duas opções:

1. Envie dados de segmento da Adobe Experience Platform para o Adobe Campaign. Para implementar essa integração, é necessário conectar a Plataforma de dados do cliente em tempo real (RTCDP) ao Campaign. [Saiba mais nesta seção](https://docs.adobe.com/content/help/pt-BR/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).


1. Integre o **Adobe Campaign** com o **serviço principal de pessoas** (também conhecido como **Profiles &amp; Audiences core service**) ou Adobe Audience Manager. Depois será possível:

   * Importar públicos/segmentos compartilhados de diferentes soluções da Adobe Experience Cloud para o Adobe Campaign. Os públicos podem ser importados por meio de listas no Adobe Campaign.

   * Exportar listas no formato de audiences compartilhados da Adobe Experience Cloud. Esses audiences podem ser usados nas diferentes soluções da Adobe Experience Cloud que você usa. Os públicos podem ser exportados após a definição de target em um workflow, usando uma atividade **[!UICONTROL Update shared audience]** dedicada.

A integração oferece suporte a dois tipos de Adobe Experience Cloud IDs:

* **ID do visitante**: esse tipo de identificador reconcilia os visitantes da Adobe Experience Cloud com os recipients do Adobe Campaign.
* **ID declarado**: esse tipo de identificador reconcilia todos os tipos de dados com elementos do banco de dados do Adobe Campaign. Ele é representado no Adobe Campaign como uma chave de reconciliação predefinida.
