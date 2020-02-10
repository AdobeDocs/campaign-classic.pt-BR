---
title: Controle de delivery
seo-title: Controle de delivery
description: Controle de delivery
seo-description: null
page-status-flag: never-activated
uuid: f9cef2d9-a6a5-45bd-8c7a-fabc11879628
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 0b5ee05c-4b96-425a-ab0f-60b930de21bd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# Controle de delivery{#delivery-control}

Uma ação do tipo **Controle de delivery** permite iniciar, pausar ou parar um delivery.

Isso pode ser o delivery especificado na transição, um delivery selecionado explicitamente ou um delivery calculado por um script. For more on this, refer to [Delivery](../../workflow/using/delivery.md).

![](assets/edit_diffusion_act.png)

If you select **[!UICONTROL Start]**, the activity will perform all the steps required to start the delivery (target calculation, content preparation, delivery). Se algumas dessas etapas já foram executadas por uma atividade anterior do workflow, elas não serão executadas novamente. For instance, if the target estimation was already performed by a **[!UICONTROL Delivery]** type activity (refer to [Delivery](../../workflow/using/delivery.md)), the **[!UICONTROL Act on the delivery]** activity will launch the remaining steps (content preparation and delivery).

As seguintes opções estão disponíveis:

* **[!UICONTROL Generate an outbound transition]**

   Cria uma transição de saída que será ativada no final da execução. Você pode escolher se quer recuperar ou não o target do delivery.

* **[!UICONTROL Processing errors]**

   Consulte Erros [de](../../workflow/using/monitoring-workflow-execution.md#processing-errors)processamento.

## Parâmetros de entrada {#input-parameters}

* deliveryId

Identificador de entrega, se a ação selecionada for **[!UICONTROL Specified in the transition]**.
