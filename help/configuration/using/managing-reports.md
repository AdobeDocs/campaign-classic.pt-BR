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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Gerenciamento de relatórios{#managing-reports}

Os relatórios baseados em um esquema específico aos destinatários padrão do Adobe Campaign (nm:receipt ou esquema vinculado) devem ser redesenvolvidos para levar em conta os dados da tabela personalizada e suas tabelas vinculadas pelo mapeamento de destino (consulte a seção de mapeamento [do](../../configuration/using/target-mapping.md) Target).

Para criar novos relatórios, consulte [esta seção](../../reporting/using/about-reports-creation-in-campaign.md).

Em alguns casos, você também deve colocar novos cubos que são específicos dessas tabelas. Cubes are detailed in [this section](../../reporting/using/about-cubes.md).

Os seguintes relatórios dizem respeito:

* **[!UICONTROL Recent proposition tracking]** (recentProposts): rastreamento de propostas em tempo real.
* **[!UICONTROL Breakdown of opens]** (openByUserAgent): é aberto detalhado de acordo com o software do usuário.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): análise de atividades de compartilhamento, aberturas e assinaturas por período.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): indicadores de rastreamento para uma entrega em um aplicativo móvel.
* **[!UICONTROL Offer analysis]** (offerAnalysis): análise de oferta por data e canal.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): taxa de reatividade para as entregas mais recentes.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): detalhamento de assinaturas ativas por aplicativo móvel.

