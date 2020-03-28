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
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Coleção de eventos{#event-collection}

Eventos gerados pelo sistema de informações podem ser coletados usando dois modos:

* chamadas para métodos SOAP permitem que você envie eventos no Adobe Campaign: o método PushEvent permite enviar um evento de cada vez, o método PushEvents permite enviar vários de uma vez. Consulte [Descrição de evento](../../message-center/using/event-description.md).
* a criação de um workflow permite recuperar eventos importando arquivos ou por meio de um gateway SQL (com a opção **Federated Data Access**).

Depois que são coletados, os eventos são divididos, por workflows técnicos, entre as filas em tempo real e batch das instâncias de execução enquanto aguardam a vinculação a um template de mensagem.

![](assets/messagecenter_events_queues_001.png)

