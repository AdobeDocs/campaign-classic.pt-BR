---
product: campaign
title: Controle de entregas
description: Saiba mais sobre a atividade de workflow de controle de entrega
feature: Workflows
hide: true
hidefromtoc: true
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 100%

---

# Controle de entregas{#delivery-control}



Uma ação do tipo **Controle de entrega** permite iniciar, pausar ou parar uma entrega.

Isso pode ser a entrega especificada na transição, uma entrega selecionada explicitamente ou uma entrega calculada por um script. Para obter mais informações, consulte [Delivery](delivery.md).

![](assets/edit_diffusion_act.png)

Se você selecionar **[!UICONTROL Start]**, a atividade executará todas as etapas necessárias para iniciar a entrega (cálculo de direcionamento, preparação de conteúdo, entrega). Se algumas dessas etapas já foram executadas por uma atividade anterior do workflow, elas não serão executadas novamente. Por exemplo, se a estimativa de direcionamento já foi executada por uma atividade do tipo **[!UICONTROL Delivery]** (consulte [Entrega](delivery.md)), a atividade **[!UICONTROL Act on the delivery]** iniciará as etapas restantes (preparação de conteúdo e entrega).

As seguintes opções estão disponíveis:

* **[!UICONTROL Generate an outbound transition]**

  Cria uma transição de saída que será ativada no final da execução. Você pode escolher se quer recuperar ou não o target da entrega.

* **[!UICONTROL Processing errors]**

  Consulte [Processamento de erros](monitoring-workflow-execution.md#processing-errors).

## Parâmetros de entrada {#input-parameters}

* deliveryId

Identificador de entrega, se a ação selecionada for **[!UICONTROL Specified in the transition]**.
