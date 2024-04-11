---
product: campaign
title: Gerenciar relatórios
description: Gerenciar relatórios
feature: Reporting, Configuration
role: Data Engineer, Developer
badge-v8: label="Também se aplica à versão v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 7%

---

# Gerenciar relatórios{#managing-reports}



Os relatórios baseados em um schema específico aos recipients padrão do Adobe Campaign (nm:recipient ou schema linked) devem ser recriados para considerar os dados da tabela personalizada e suas tabelas vinculadas por meio do target mapping (consulte [Target mapping](../../configuration/using/target-mapping.md) seção).

Para criar novos relatórios, consulte [nesta seção](../../reporting/using/about-reports-creation-in-campaign.md).

Em alguns casos, você também deve colocar novos cubos específicos para essas tabelas em vigor. Os cubos são detalhados em [nesta seção](../../reporting/using/ac-cubes.md).

Os seguintes relatórios estão relacionados:

* **[!UICONTROL Recent proposition tracking]** (recentPropositions): rastreamento de propostas em tempo real.
* **[!UICONTROL Breakdown of opens]** (opensByUserAgent): abre detalhado de acordo com o software do usuário.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): análise de atividades de compartilhamento, aberturas e subscrições por período de tempo.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): rastreamento de indicadores para um delivery em um aplicativo móvel.
* **[!UICONTROL Offer analysis]** (offerAnalysis): análise de ofertas por data e canal.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): taxa de reatividade para os deliveries mais recentes.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): detalhamento de assinaturas ativas por aplicativo móvel.
