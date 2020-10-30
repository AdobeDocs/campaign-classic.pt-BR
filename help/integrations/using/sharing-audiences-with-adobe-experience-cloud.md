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
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '216'
ht-degree: 100%

---


# Compartilhamento de públicos com a Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!NOTE]
>
>A utilização dessa integração requer a implementação do IMS. Consulte a seção sobre [IMS](../../integrations/using/about-adobe-id.md).

O Adobe Campaign permite trocar e compartilhar públicos/segmentos com as soluções Adobe Experience Cloud e serviços principais. Para fazer isso, você precisa integrar o **Adobe Campaign** com o **serviço principal de Pessoas** (também conhecido como **serviço central de Perfis e Públicos**) ou o Adobe Audience Manager. Depois será possível:

* Importar públicos/segmentos compartilhados de diferentes soluções da Adobe Experience Cloud para o Adobe Campaign. Os públicos podem ser importados por meio de listas no Adobe Campaign.
* Exportar listas no formato de audiences compartilhados da Adobe Experience Cloud. Esses audiences podem ser usados nas diferentes soluções da Adobe Experience Cloud que você usa. Os públicos podem ser exportados após a definição de target em um workflow, usando uma atividade **[!UICONTROL Update shared audience]** dedicada.

>[!CAUTION]
>
>Dependendo do tipo de dados, a importação de públicos no Adobe Campaign pode estar sujeita a restrições legais.

A integração oferece suporte a dois tipos de IDs da Adobe Experience Cloud:

* **ID do visitante**: esse tipo de identificador reconcilia os visitantes da Adobe Experience Cloud com os recipients do Adobe Campaign.
* **ID declarado**: esse tipo de identificador reconcilia todos os tipos de dados com elementos do banco de dados do Adobe Campaign. Ele é representado no Adobe Campaign como uma chave de reconciliação predefinida.
