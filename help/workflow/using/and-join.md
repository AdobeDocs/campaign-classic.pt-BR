---
title: AND-join
seo-title: AND-join
description: AND-join
seo-description: null
page-status-flag: never-activated
uuid: 8234d6cd-0e9b-4187-9ddf-9e1f86aa1b9a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 075206aa-ff7b-4fa8-a05d-14a29fb119ba
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f7ed7e59be2cfbde467b0c80d21cfbf52016a2b8
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 56%

---


# AND-join{#and-join}

Um join inicia sua transição de saída somente quando todas as transições de entrada são ativadas, ou seja, quando todas as atividades anteriores são concluídas. Isso permite verificar se determinadas atividades foram concluídas antes de continuar a executar o workflow.

Por exemplo, você pode usar uma atividade AND-join no contexto de criação de conteúdo e automação de envio de delivery, para garantir que um delivery seja iniciado somente depois que as etapas de consulta de públicos alvos e atualizações de conteúdo forem concluídas. Um caso de uso dedicado está disponível [nesta seção](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)

![](assets/and-join-usage.png)

A população enviada da saída da atividade é determinada escolhendo um conjunto principal entre as transições de entrada na atividade.

A transição de saída só pode conter uma das populações de transição de entrada. Se a atividade não estiver configurada, a transição de saída selecionará aleatoriamente uma das populações de entrada.

>[!CAUTION]
>
>In the case of **AND-join** type activities, the event variables are merged but if a same variable is defined twice, there is a conflict and the value remains undetermined. Para obter mais informações, consulte [](../../workflow/using/javascript-scripts-and-templates.md#event-variables).
