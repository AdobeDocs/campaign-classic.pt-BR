---
product: campaign
title: Gerenciar relatórios
description: Gerenciar relatórios
feature: Reporting, Configuration
role: Developer
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
TQID: 'https://experienceleague.adobe.com/LA4v5oODC9n5K2Ttox9SF7lwcGQOU7IDEvL1P4Sls-4'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
    internal-label: Dynamic reporting
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
    internal-label: Reporting interface
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 4%
---
# Gerenciar relatórios{#managing-reports}



Os relatórios baseados em um esquema específico dos recipients padrão do Adobe Campaign (nm:recipient ou esquema vinculado) devem ser recriados para levar em conta os dados da tabela personalizada e suas tabelas vinculadas pelo target mapping (consulte a seção [Target mapping](../../configuration/using/target-mapping.md)).

Para criar novos relatórios, consulte [esta seção](../../reporting/using/about-reports-creation-in-campaign.md).

Em alguns casos, você também deve colocar novos cubos específicos para essas tabelas em vigor. Os cubos estão detalhados em [esta seção](../../reporting/using/ac-cubes.md).

Os seguintes relatórios estão relacionados:

* **[!UICONTROL Recent proposition tracking]** (recentPropositions): rastreamento de propostas em tempo real.
* **[!UICONTROL Breakdown of opens]** (opensByUserAgent): abertura detalhada de acordo com o software do usuário.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): análise de atividades de compartilhamento, aberturas e assinaturas por período de tempo.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): rastreamento de indicadores para uma entrega em um aplicativo móvel.
* **[!UICONTROL Offer analysis]** (offerAnalysis): análise de oferta por data e canal.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): taxa de reatividade para as entregas mais recentes.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): detalhamento de assinaturas ativas por aplicativo móvel.
