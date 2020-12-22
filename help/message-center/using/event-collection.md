---
solution: Campaign Classic
product: campaign
title: Coleção de eventos
description: Coleção de eventos
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: d1130691e40c0cac183db37a4c0b410d00bb696a
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 75%

---


# Coleção de eventos{#event-collection}

Eventos gerados pelo sistema de informações podem ser coletados usando dois modos:

* Chamadas para métodos SOAP permitem que você envie eventos por push no Adobe Campaign: o método PushEvent permite enviar um evento de cada vez, o método PushEvents permite enviar vários de uma vez. Consulte [Descrição de evento](../../message-center/using/event-description.md).
* A criação de um workflow permite recuperar eventos importando arquivos ou por meio de um gateway SQL (com a opção **Federated Data Access**).

Depois que são coletados, os eventos são divididos, por workflows técnicos, entre as filas em tempo real e em lote das instâncias de execução enquanto aguardam a vinculação a um modelo de mensagem.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>No instância de execução, as pastas **[!UICONTROL Real time events]** ou **[!UICONTROL Batch events]** não devem ser definidas como visualização, pois isso pode levar a problemas de [direito de acesso](../../platform/using/access-management.md#about-permissions). Para obter mais informações sobre como configurar uma pasta como uma visualização, consulte [Sobre o visualização](../../platform/using/access-management.md#about-views).
