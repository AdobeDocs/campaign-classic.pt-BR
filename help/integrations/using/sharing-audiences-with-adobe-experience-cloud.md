---
product: campaign
title: Compartilhamento de públicos-alvos com a Adobe Experience Cloud
description: Compartilhamento de públicos-alvos com a Adobe Experience Cloud
feature: Audiences
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
TQID: https://experienceleague.adobe.com/MGzMyGtmzaVGZy6oWHcirPPdSSpu9YYcuR30KIVZ9bc
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 253
ht-degree: 100%

---

# Compartilhamento de públicos-alvos com a Adobe Experience Cloud {#sharing-audiences-with-adobe-experience-cloud}


>[!CAUTION]
>
>Para compartilhar públicos-alvos com as soluções da Adobe Experience Cloud, é necessário implementar o Adobe Identity Management System. i [Saiba mais sobre o IMS](../../integrations/using/about-adobe-id.md).

O Adobe Campaign permite compartilhar públicos-alvo e segmentos com os serviços da Adobe Experience Cloud. Estão disponíveis duas opções:

1. Envie dados de segmento da Adobe Experience Platform para o Adobe Campaign. Para implementar essa integração, é necessário conectar a Plataforma de dados do cliente em tempo real (RTCDP) ao Campaign. [Saiba mais nesta seção](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=pt-BR){target="_blank"}.

1. Integre o **Adobe Campaign** aos **públicos-alvo da Experience Cloud** ou ao **Adobe Audience Manager**. Depois será possível:

   * Importar públicos-alvos/segmentos compartilhados de diferentes soluções da Adobe Experience Cloud para o Adobe Campaign. Os públicos-alvos podem ser importados por meio de listas no Adobe Campaign.

   * Exportar listas no formato de públicos-alvo compartilhados da Adobe Experience Cloud. Esses públicos-alvos podem ser usados nas diferentes soluções da Adobe Experience Cloud que você usa. Os públicos-alvo podem ser exportados após o direcionamento num fluxo de trabalho, usando uma atividade **[!UICONTROL Update shared audience]** dedicada.

A integração oferece suporte a dois tipos de Adobe Experience Cloud IDs:

* **ID do visitante**: esse tipo de identificador reconcilia os visitantes da Adobe Experience Cloud com os destinatários do Adobe Campaign.
* **ID declarado**: esse tipo de identificador reconcilia todos os tipos de dados com elementos do banco de dados do Adobe Campaign. Ele é representado no Adobe Campaign como uma chave de reconciliação predefinida.

  >[!NOTE]
  >
  > A fonte de dados de ID declarada agora também pode ser usada com a integração dos ativos da Experience Cloud.
  >
