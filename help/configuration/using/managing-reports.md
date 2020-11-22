---
solution: Campaign Classic
product: campaign
title: Gerenciamento de relatórios
description: Gerenciamento de relatórios
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 4%

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

