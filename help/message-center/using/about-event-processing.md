---
product: campaign
title: Processamento de evento
description: Saiba como os eventos de mensagens transacionais são processados no Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 3d85866a-6339-458c-807a-b267cce772b8
source-git-commit: b46a483594f210c4530a934194c6d2b73deaeaf9
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 45%

---

# Processamento de evento {#about-event-processing}

No contexto de mensagens transacionais, um evento é gerado por um sistema de informações externo e é enviado ao Adobe Campaign por meio dos métodos **[!UICONTROL PushEvent]** e **[!UICONTROL PushEvents]** (consulte [Descrição do evento](../../message-center/using/event-description.md)).

Esse evento contém dados vinculados ao evento, como seu [type](../../message-center/using/creating-event-types.md) (confirmação de pedido, criação de conta em um site etc.), endereço de email ou número de celular, bem como outras informações que permitem enriquecer e personalizar a mensagem transacional antes do delivery (informações de contato do cliente, idioma da mensagem, formato de email etc.).

Exemplo de dados de evento:

![](assets/messagecenter_events_request_001.png)

## Etapas de processamento de evento {#event-processing}

Para processar eventos de mensagens transacionais, as seguintes etapas são aplicadas na(s) instância(s) de execução:

1. [Coleção de eventos](#event-collection)
1. [Transferência de evento para um template de mensagem](#routing-towards-a-template)
1. Enriquecimento de evento com dados de personalização
1. [Execução da entrega](../../message-center/using/delivery-execution.md)
1. [Reciclagem de ](#event-recycling) eventos cujo delivery vinculado falhou (por meio de um workflow do Adobe Campaign)

Depois que todas as etapas acima forem executadas por meio da instância de execução, cada recipient target receberá uma mensagem personalizada.

>[!NOTE]
>
>Para obter mais informações sobre as instâncias de mensagens transacionais, consulte [Arquitetura de mensagens transacionais](../../message-center/using/transactional-messaging-architecture.md).


## Coleção de eventos {#event-collection}

Eventos gerados pelo sistema de informações podem ser coletados usando dois modos:

* Chamadas para métodos SOAP permitem que você envie eventos no Adobe Campaign: o método PushEvent permite enviar um evento de cada vez, o método PushEvents permite enviar vários eventos de uma vez. Para obter mais informações, consulte [Descrição do evento](../../message-center/using/event-description.md).

* A criação de um workflow permite recuperar eventos importando arquivos ou por meio de um gateway SQL (com a opção [Federated Data Access](../../installation/using/about-fda.md)).

Depois que são coletados, os eventos são divididos por workflows técnicos entre as filas em tempo real e em lote da(s) instância(s) de execução, enquanto aguardam a vinculação a um template de mensagem.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>Na instância de execução, as pastas **[!UICONTROL Real time events]** ou **[!UICONTROL Batch events]** não devem ser definidas como visualizações, pois isso pode causar problemas de direito de acesso. Para obter mais informações sobre como configurar uma pasta como visualização, consulte [esta seção](../../platform/using/access-management-folders.md).

## Roteamento para um template {#routing-towards-a-template}

Depois que o template de mensagem é publicado na(s) instância(s) de execução, dois templates são gerados automaticamente: um para ser vinculado a um evento em tempo real e outro para ser vinculado a um evento em lote.

A etapa de roteamento consiste em vincular um evento ao template de mensagem apropriado, com base em:

* O tipo de evento especificado nas propriedades do próprio evento:

   ![](assets/messagecenter_event_type_001.png)

* O tipo de evento especificado nas propriedades do template de mensagem:

   ![](assets/messagecenter_event_type_002.png)

Por padrão, o roteamento depende das seguintes informações:

* O tipo de evento
* O canal a ser usado (por padrão: email)
* O template do delivery mais recente, com base na data da publicação

## Status do evento {#event-statuses}

O **Histórico de Eventos**, em **[!UICONTROL Event history]** > **[!UICONTROL Message Center]** , agrupa todos os eventos processados em uma única visualização. Eles podem ser categorizados por tipo de evento ou por **status**. Esses status são:

* **Pendente**: O evento pode ser:

   * Um evento que acabou de ser coletado e que ainda não foi processado. A coluna **[!UICONTROL Number of errors]** mostra o valor 0. O template de email ainda não foi vinculado.
   * Um evento processado, mas cuja confirmação está incorreta. A coluna **[!UICONTROL Number of errors]** mostra um valor que não é 0. Para saber quando esse evento será processado novamente, consulte a coluna **[!UICONTROL Process requested on]**.

* **Delivery** pendente: O evento foi processado e o template do delivery está vinculado. O delivery do email está pendente e o processo de delivery clássico é aplicado. Para obter mais informações, você pode abrir o [delivery](../../delivery/using/about-message-tracking.md).
* **Enviado**,  **** Ignorado e Erro  **de delivery**: Esses status de delivery são recuperados por meio do workflow  **** updateEventsStatus . Para obter mais informações, você poderá abrir o delivery relevante.
* **Evento não coberto**: Falha na fase de roteamento de mensagens transacionais. Por exemplo, o Adobe Campaign não encontrou o email que atua como template para o evento.
* **Evento expirado**: O número máximo de tentativas de envio foi atingido. O evento é considerado nulo.

## Reciclagem de eventos {#event-recycling}

Se o delivery de uma mensagem em um canal específico falhar, o Adobe Campaign poderá reenviar a mensagem usando um canal diferente. Por exemplo, se um delivery no canal SMS falhar, a mensagem será reenviada usando o canal de email.

Para fazer isso, é necessário configurar um workflow que recrie todos os eventos com o status **Delivery error** e atribuir um canal diferente a eles.

>[!CAUTION]
>
>Essa etapa só poderá ser executada usando um workflow e, portanto, é reservada a usuários experts. Para obter mais informações, entre em contato com o executivo da sua conta Adobe.