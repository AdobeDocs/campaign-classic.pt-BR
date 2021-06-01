---
product: campaign
title: Gerenciamento de relatórios
description: Gerenciamento de relatórios
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 4%

---

# Gerenciamento de relatórios{#managing-reports}

Os relatórios baseados em um schema específico para os recipients padrão do Adobe Campaign (nm:recipient ou schema vinculado) devem ser redesenvolvidos para considerar os dados da tabela personalizada e suas tabelas vinculadas por meio do target mapping (consulte a seção [Target mapping](../../configuration/using/target-mapping.md)).

Para criar novos relatórios, consulte [esta seção](../../reporting/using/about-reports-creation-in-campaign.md).

Em alguns casos, você também deve colocar novos cubos específicos para essas tabelas em vigor. Os cubos são detalhados em [nesta seção](../../reporting/using/about-cubes.md).

Os seguintes relatórios estão relacionados:

* **[!UICONTROL Recent proposition tracking]** (recentPropositions): rastreamento de apresentação em tempo real.
* **[!UICONTROL Breakdown of opens]** (opensByUserAgent): é aberta dividida de acordo com o software do usuário.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): análise de atividades de compartilhamento, aberturas e subscrições por período de tempo.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): indicadores de rastreamento para um delivery em um aplicativo móvel.
* **[!UICONTROL Offer analysis]** (offerAnalysis): análise de oferta por data e canal.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): taxa de reatividade para os deliveries mais recentes.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): detalhamento de subscrições ativas por aplicativo móvel.
