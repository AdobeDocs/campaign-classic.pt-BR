---
product: campaign
title: Compartilhamento de públicos com a Adobe Experience Cloud
description: Compartilhamento de públicos com a Adobe Experience Cloud
feature: Audiences
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 100%

---

# Compartilhamento de públicos com a Adobe Experience Cloud {#sharing-audiences-with-adobe-experience-cloud}


>[!CAUTION]
>
>Para compartilhar públicos com as soluções da Adobe Experience Cloud, é necessário implementar o Adobe Identity Management System. i [Saiba mais sobre o IMS](../../integrations/using/about-adobe-id.md).

O Adobe Campaign permite compartilhar públicos-alvo e segmentos com os serviços da Adobe Experience Cloud. Estão disponíveis duas opções:

1. Envie dados de segmento da Adobe Experience Platform para o Adobe Campaign. Para implementar essa integração, é necessário conectar a Plataforma de dados do cliente em tempo real (RTCDP) ao Campaign. [Saiba mais nesta seção](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=pt-BR){target="_blank"}.

1. Integre o **Adobe Campaign** aos **públicos-alvo da Experience Cloud** ou ao **Adobe Audience Manager**. Depois será possível:

   * Importar públicos/segmentos compartilhados de diferentes soluções da Adobe Experience Cloud para o Adobe Campaign. Os públicos podem ser importados por meio de listas no Adobe Campaign.

   * Exportar listas no formato de públicos-alvo compartilhados da Adobe Experience Cloud. Esses audiences podem ser usados nas diferentes soluções da Adobe Experience Cloud que você usa. Os públicos-alvo podem ser exportados após o direcionamento num fluxo de trabalho, usando uma atividade **[!UICONTROL Update shared audience]** dedicada.

A integração oferece suporte a dois tipos de Adobe Experience Cloud IDs:

* **ID do visitante**: esse tipo de identificador reconcilia os visitantes da Adobe Experience Cloud com os destinatários do Adobe Campaign.
* **ID declarado**: esse tipo de identificador reconcilia todos os tipos de dados com elementos do banco de dados do Adobe Campaign. Ele é representado no Adobe Campaign como uma chave de reconciliação predefinida.

  >[!NOTE]
  >
  > A fonte de dados de ID declarada agora também pode ser usada com a integração dos ativos da Experience Cloud.
  >
