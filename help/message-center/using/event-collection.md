---
solution: Campaign Classic
product: campaign
title: Coleção de eventos
description: Coleção de eventos
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 63cde1c2-8f4c-4cb0-aa98-0c42f9e5f3c6
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '138'
ht-degree: 100%

---

# Coleção de eventos{#event-collection}

Eventos gerados pelo sistema de informações podem ser coletados usando dois modos:

* Chamadas para métodos SOAP permitem que você envie eventos por push no Adobe Campaign: o método PushEvent permite enviar um evento de cada vez, o método PushEvents permite enviar vários de uma vez. Consulte [Descrição de evento](../../message-center/using/event-description.md).
* A criação de um workflow permite recuperar eventos importando arquivos ou por meio de um gateway SQL (com a opção **Federated Data Access**).

Depois que são coletados, os eventos são divididos, por workflows técnicos, entre as filas em tempo real e em lote das instâncias de execução enquanto aguardam a vinculação a um modelo de mensagem.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>Na instância de execução, as pastas **[!UICONTROL Real time events]** ou **[!UICONTROL Batch events]** não devem ser definidas como visualizações, pois isso pode causar problemas de direito de acesso. Para obter mais informações sobre como configurar uma pasta como visualização, consulte [esta seção](../../platform/using/access-management-folders.md).
