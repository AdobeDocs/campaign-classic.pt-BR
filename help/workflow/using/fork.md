---
solution: Campaign Classic
product: campaign
title: Bifurcação
description: Saiba mais sobre a atividade de workflow de bifurcação
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: e5f718908d0bb6893e54c51700865ecda09c80db
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 9%

---


# Bifurcação{#fork}

A atividade **[!UICONTROL Fork]** permite criar várias transições de saída, a fim de realizar várias atividades independentemente no mesmo fluxo de trabalho.

Por exemplo, você pode usar a atividade depois de um query para executar duas ações simultaneamente:

* Salve o resultado do query em uma audiência,
* Execute uma segmentação no resultado para enviar vários delivery.

Você também pode usar a atividade no contexto da criação de conteúdo e da automação de envio de delivery, para iniciar o cálculo de públicos alvos e a criação de conteúdo em paralelo. Um caso de uso específico está disponível [nesta seção](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content).

>[!IMPORTANT]
>
>Transições de saída adicionadas após uma atividade **[!UICONTROL Fork]** **não serão** executadas simultaneamente. Esse comportamento pode afetar o desempenho do fluxo de trabalho. Use essa atividade se precisar executar várias atividades independentemente e eventualmente juntá-las antes de executar o restante do fluxo de trabalho.

Para configurar a atividade **[!UICONTROL Fork]**, abra-a e defina o número e o rótulo das transições de saída.

![](assets/s_user_segmentation_fork.png)

Em seguida, você pode configurar cada transição de saída e associá-la usando uma atividade [AND-join](../../workflow/using/and-join.md), se necessário. Dessa forma, o restante do fluxo de trabalho será executado somente depois que as transições de saída **[!UICONTROL Fork]** da atividade forem concluídas.
