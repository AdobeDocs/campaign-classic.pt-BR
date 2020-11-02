---
title: Compartilhamento de públicos com a Adobe Experience Cloud
seo-title: Compartilhamento de públicos com a Adobe Experience Cloud
description: Compartilhamento de públicos com a Adobe Experience Cloud
seo-description: null
page-status-flag: never-activated
uuid: 24ac3463-69ab-48b4-85e0-4fe1948bf5ed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 8f295058-5a78-4512-9bdf-d5f022457e10
translation-type: tm+mt
source-git-commit: 4b98c23f4120cbea6dd54cd68b61202e74bee3e1
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 61%

---


# Compartilhamento de públicos com a Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!CAUTION]
>
>Para compartilhar o audiência com as soluções Adobe Experience Cloud, é necessário implementar o Adobe Identity Management System. [Saiba mais sobre o IMS](../../integrations/using/about-adobe-id.md).

Com a Adobe Campaign, você pode compartilhar audiências e segmentos com as soluções Adobe Experience Cloud e os principais serviços. Duas opções estão disponíveis:

1. Envie dados de segmento da Adobe Experience Platform para a Adobe Campaign. Para implementar essa integração, é necessário conectar sua Plataforma de dados do cliente em tempo real à Campanha (RTCDP). [Saiba mais nesta seção](https://docs.adobe.com/content/help/pt-BR/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).


1. Integrate **Adobe Campaign** with **People core service** (also known as **Profiles &amp; Audiences core service**) or Adobe Audience Manager. Depois será possível:

   * Importar públicos/segmentos compartilhados de diferentes soluções da Adobe Experience Cloud para o Adobe Campaign. Os públicos podem ser importados por meio de listas no Adobe Campaign.

   * Exportar listas no formato de audiences compartilhados da Adobe Experience Cloud. Esses audiences podem ser usados nas diferentes soluções da Adobe Experience Cloud que você usa. Os públicos podem ser exportados após a definição de target em um workflow, usando uma atividade **[!UICONTROL Update shared audience]** dedicada.

Essa integração suporta dois tipos de Adobe Experience Cloud IDs:

* **ID do visitante**: esse tipo de identificador reconcilia os visitantes da Adobe Experience Cloud com os recipients do Adobe Campaign.
* **ID declarado**: esse tipo de identificador reconcilia todos os tipos de dados com elementos do banco de dados do Adobe Campaign. Ele é representado no Adobe Campaign como uma chave de reconciliação predefinida.
