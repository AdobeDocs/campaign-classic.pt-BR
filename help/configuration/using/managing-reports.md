---
title: Gerenciamento de relatórios
seo-title: Gerenciamento de relatórios
description: Gerenciamento de relatórios
seo-description: null
page-status-flag: never-activated
uuid: 3b8e6f11-4cbd-450e-871b-50fd0ead96db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 21777423-0c8a-4bb1-b210-972f660648bd
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 5%

---


# Gerenciamento de relatórios{#managing-reports}

Os relatórios baseados em um schema específico aos recipient padrão da Adobe Campaign (nm:recipient ou schema vinculado) devem ser redesenvolvidos para levar em conta os dados da tabela personalizada e suas tabelas vinculadas por meio do target mapping (consulte a seção [Target mapping](../../configuration/using/target-mapping.md) ).

Para criar novos relatórios, consulte [esta seção](../../reporting/using/about-reports-creation-in-campaign.md).

Em alguns casos, você também deve colocar novos cubos específicos para essas tabelas. Cubes are detailed in [this section](../../reporting/using/about-cubes.md).

Os seguintes relatórios dizem respeito:

* **[!UICONTROL Recent proposition tracking]** (recentProposts): rastreamento de propostas em tempo real.
* **[!UICONTROL Breakdown of opens]** (openByUserAgent): é aberto detalhado de acordo com o software do usuário.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): análise de compartilhar atividades, aberturas e subscrições por período de tempo.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): indicadores de rastreamento de um delivery em um aplicativo móvel.
* **[!UICONTROL Offer analysis]** (offerAnalysis): análise de oferta por data e canal.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): taxa de reatividade para os delivery mais recentes.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): detalhamento de subscrições ativas por aplicativo móvel.

