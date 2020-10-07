---
title: Sobre processamento de evento
seo-title: Sobre processamento de evento
description: Sobre processamento de evento
seo-description: null
page-status-flag: never-activated
uuid: 6c3e02b3-0d4d-4661-952a-e4915ca9ef92
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: a78c9986-7c49-47db-99a0-9f0949c4dee7
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 100%

---


# Sobre processamento de evento{#about-event-processing}

No contexto de mensagens transacionais, um evento é gerado por um sistema de informações externo e é enviado ao Adobe Campaign através dos métodos **[!UICONTROL PushEvent]** e **[!UICONTROL PushEvents]** (consulte [Descrição do evento](../../message-center/using/event-description.md)). Ele contém dados vinculados ao evento, como seu tipo (confirmação de pedido ou criação de conta em um site, por exemplo), endereço de email ou número de celular, bem como outras informações que permitem enriquecer e personalizar a mensagem transacional antes do delivery. Pode se tratar de informações de contato do cliente, idioma da mensagem ou formato do email.

Exemplo de dados de evento:

![](assets/messagecenter_events_request_001.png)

Para processar eventos de mensagens transacionais, você deve seguir as etapas abaixo:

1. Coleção de evento,
1. Transferência de evento para um template de mensagem,
1. Enriquecimento de evento com dados de personalização,
1. Execução do Delivery,
1. Reciclagem dos eventos cujo delivery vinculado falhou (esta etapa pode ser realizada por meio de um workflow do Adobe Campaign).

## Status do evento {#event-statuses}

O **Histórico de Eventos**, em **[!UICONTROL Event history]** > **[!UICONTROL Message Center]** , agrupa todos os eventos processados em uma única visualização. Eles podem ser categorizados por tipo de evento ou por **status**. Esses status são:

* **Pendente**: o que significa que o evento pode ser:

   * um evento que foi recém-coletado e que ainda não foi processado. A coluna **[!UICONTROL Number of errors]** mostra o valor 0. O template de email ainda não foi vinculado.
   * um evento processado, mas cuja confirmação está incorreta. A coluna **[!UICONTROL Number of errors]** mostra um valor que não é 0. Para saber quando esse evento será processado novamente, consulte a coluna **[!UICONTROL Process requested on]**.

* **Delivery pendente**: o evento foi processado e o template do delivery está vinculado. O delivery do email está pendente e o processo de delivery clássico é aplicado. Para obter mais informações, é possível abrir o delivery. Consulte [Delivery](../../delivery/using/about-message-tracking.md).
* **Enviado**, **Ignorado** e **Erro de Delivery**: esses status de delivery são recuperados por meio do workflow **updateEventsStatus** . Para obter mais informações, você poderá abrir o delivery relevante.
* **Evento não coberto**: a fase de roteamento do Centro de mensagens falhou. Por exemplo, o Adobe Campaign não encontrou o email que atua como template para o evento.
* **Evento expirado**: o número máximo de tentativas de envio foi atingido. O evento é considerado nulo.
