---
product: campaign
title: Controle de entregas
description: Saiba mais sobre a atividade de fluxo de trabalho de controle de entrega
feature: Workflows
hide: true
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
TQID: 'https://experienceleague.adobe.com/WVXqtjcGQQOQJfVi58BqtLPqgG7AkgslAzQk4Vjbl9k'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 100%
---
# Controle de entregas{#delivery-control}



Uma ação do tipo **Controle de entrega** permite iniciar, pausar ou parar uma entrega.

Isso pode ser a entrega especificada na transição, uma entrega selecionada explicitamente ou uma entrega calculada por um script. Para obter mais informações, consulte [Delivery](delivery.md).

![](assets/edit_diffusion_act.png)

Se você selecionar **[!UICONTROL Start]**, a atividade executará todas as etapas necessárias para iniciar a entrega (cálculo de direcionamento, preparação de conteúdo, entrega). Se algumas dessas etapas já foram executadas por uma atividade anterior do fluxo de trabalho, elas não serão executadas novamente. Por exemplo, se a estimativa de direcionamento já foi executada por uma atividade do tipo **[!UICONTROL Delivery]** (consulte [Entrega](delivery.md)), a atividade **[!UICONTROL Act on the delivery]** iniciará as etapas restantes (preparação de conteúdo e entrega).

As seguintes opções estão disponíveis:

* **[!UICONTROL Generate an outbound transition]**

  Cria uma transição de saída que será ativada no final da execução. Você pode escolher se quer recuperar ou não o target da entrega.

* **[!UICONTROL Processing errors]**

  Consulte [Processamento de erros](monitoring-workflow-execution.md#processing-errors).

## Parâmetros de entrada {#input-parameters}

* deliveryId

Identificador de entrega, se a ação selecionada for **[!UICONTROL Specified in the transition]**.
