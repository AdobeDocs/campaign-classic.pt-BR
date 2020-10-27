---
title: Coleção de eventos
seo-title: Coleção de eventos
description: Coleção de eventos
seo-description: null
page-status-flag: never-activated
uuid: 8c373962-40d4-4982-9bd1-ce1cf8261dd5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: cfff302a-6ac0-461a-a1e4-8e4b617fe134
translation-type: tm+mt
source-git-commit: 95dff2f3704e316e9ec9e454a8f3fb9835508ccd
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 50%

---


# Coleção de eventos{#event-collection}

Eventos gerados pelo sistema de informações podem ser coletados usando dois modos:

* As chamadas aos métodos SOAP permitem que você envie eventos para o Adobe Campaign: o método PushEvent permite que você envie um evento de cada vez, o método PushEvents permite que você envie vários de uma só vez. Consulte [Descrição de evento](../../message-center/using/event-description.md).
* Creating a workflow lets you recover events by importing files or via an SQL gateway (with the **Federated Data Access** option).

Depois que são coletados, os eventos são divididos, por workflows técnicos, entre as filas em tempo real e batch das instâncias de execução enquanto aguardam a vinculação a um template de mensagem.

![](assets/messagecenter_events_queues_001.png)
