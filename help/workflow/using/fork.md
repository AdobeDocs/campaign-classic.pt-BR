---
product: campaign
title: Bifurcação
description: Saiba mais sobre a atividade de workflow de bifurcação
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: ht
source-wordcount: '196'
ht-degree: 100%

---

# Bifurcação{#fork}

A atividade **[!UICONTROL Fork]** permite criar várias transições de saída para realizar várias atividades independentemente no mesmo fluxo de trabalho.

Por exemplo, você pode usar a atividade depois de uma consulta para executar duas ações em paralelo:

* Salvar o resultado da consulta em uma audiência,
* Executar uma segmentação no resultado para enviar vários deliveries.

Você também pode usar a atividade no contexto da criação de conteúdo e automação de envio de delivery, a fim de iniciar o cálculo de destino e a criação de conteúdo em paralelo. Um caso de uso específico está disponível [nesta seção](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content).

>[!IMPORTANT]
>
>Transições de saída adicionadas após uma atividade **[!UICONTROL Fork]** não **serão** executadas simultaneamente. Esse comportamento pode afetar o desempenho do fluxo de trabalho. Use essa atividade se precisar executar várias atividades de forma independente e eventualmente juntá-las antes de executar o restante do fluxo de trabalho.

Para configurar a atividade **[!UICONTROL Fork]**, abra-a e defina o número e o rótulo das transições de saída desejadas.

![](assets/s_user_segmentation_fork.png)

Em seguida, você pode configurar cada transição de saída e associá-la usando uma atividade [AND-join](../../workflow/using/and-join.md), se necessário. Dessa forma, o restante do fluxo de trabalho será executado somente depois que as transições de saída da atividade **[!UICONTROL Fork]** forem concluídas.
