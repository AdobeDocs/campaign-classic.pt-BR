---
product: campaign
title: Compartilhamento de públicos com a Adobe Experience Cloud
description: Compartilhamento de públicos com a Adobe Experience Cloud
feature: Audiences, People Core Service Integration
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 100%

---

# Compartilhamento de públicos com a Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}



>[!CAUTION]
>
>Para compartilhar públicos com as soluções da Adobe Experience Cloud, é necessário implementar o Adobe Identity Management System. i [Saiba mais sobre o IMS](../../integrations/using/about-adobe-id.md).

Com o Adobe Campaign, você pode compartilhar públicos e segmentos com as soluções Adobe Experience Cloud e os serviços principais. Estão disponíveis duas opções:

1. Envie dados de segmento da Adobe Experience Platform para o Adobe Campaign. Para implementar essa integração, é necessário conectar a Plataforma de dados do cliente em tempo real (RTCDP) ao Campaign. [Saiba mais nesta seção](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=pt-BR).

1. Integre o **Adobe Campaign** com o **serviço principal de pessoas** (também conhecido como **Profiles &amp; Audiences core service**) ou Adobe Audience Manager. Depois será possível:

   * Importar públicos/segmentos compartilhados de diferentes soluções da Adobe Experience Cloud para o Adobe Campaign. Os públicos podem ser importados por meio de listas no Adobe Campaign.

   * Exportar listas no formato de públicos-alvo compartilhados da Adobe Experience Cloud. Esses audiences podem ser usados nas diferentes soluções da Adobe Experience Cloud que você usa. Os públicos-alvo podem ser exportados após o direcionamento num fluxo de trabalho, usando uma atividade **[!UICONTROL Update shared audience]** dedicada.

A integração oferece suporte a dois tipos de Adobe Experience Cloud IDs:

* **ID do visitante**: esse tipo de identificador reconcilia os visitantes da Adobe Experience Cloud com os destinatários do Adobe Campaign.
* **ID declarado**: esse tipo de identificador reconcilia todos os tipos de dados com elementos do banco de dados do Adobe Campaign. Ele é representado no Adobe Campaign como uma chave de reconciliação predefinida.

  >[!NOTE]
  >
  > A fonte de dados de ID declarada agora também pode ser usada com a integração do serviço principal Pessoas.
  >
  >Se você estiver usando a integração do serviço principal Pessoas e quiser adicionar a integração do Audience Manager, será necessária a ajuda de um consultor do Adobe Audience Manager para evitar a perda de todas as sincronizações de ID coletadas durante a transição para o uso dessa fonte de dados de ID declarada em um contexto do Adobe Audience Manager.
