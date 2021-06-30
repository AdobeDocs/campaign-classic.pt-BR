---
product: campaign
title: Processamento de evento
description: Saiba como os eventos de mensagens transacionais são processados no Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 3d85866a-6339-458c-807a-b267cce772b8
source-git-commit: e86350cf12db37e3f2c227563057b97922601729
workflow-type: ht
source-wordcount: '691'
ht-degree: 100%

---

# Processamento de evento {#about-event-processing}

No contexto de mensagens transacionais, um evento é gerado por um sistema de informação externo e enviado para o Adobe Campaign por meio de métodos **[!UICONTROL PushEvent]** e **[!UICONTROL PushEvents]** (consulte [Descrição do evento](../../message-center/using/event-description.md)).

Esse evento contém dados vinculados ao evento, como seu [tipo](../../message-center/using/creating-event-types.md) (confirmação de pedido, criação de conta em um site etc.), endereço de email ou número de celular, bem como outras informações que permitem enriquecer e personalizar a mensagem transacional antes da entrega (informações de contato do cliente, idioma da mensagem, formato do email etc.).

Exemplo de dados do evento:

![](assets/messagecenter_events_request_001.png)

## Etapas de processamento de evento {#event-processing}

Para processar eventos de mensagens transacionais, as seguintes etapas são aplicadas na(s) instância(s) de execução:

1. [Coleção de eventos](#event-collection)
1. [Transferência de evento para um modelo de mensagem](#routing-towards-a-template)
1. Enriquecimento de evento com dados de personalização
1. [Execução da entrega](../../message-center/using/delivery-execution.md)
1. [Reciclagem de eventos](#event-recycling) cuja entrega vinculada falhou (por meio de um fluxo de trabalho do Adobe Campaign)

Depois que todas as etapas acima forem executadas por meio da instância de execução, cada recipient direcionado receberá uma mensagem personalizada.

>[!NOTE]
>
>Para obter mais informações sobre as instâncias de mensagens transacionais, consulte [Arquitetura de mensagens transacionais](../../message-center/using/transactional-messaging-architecture.md).


## Coleção de eventos {#event-collection}

Eventos gerados pelo sistema de informações podem ser coletados usando dois modos:

* Chamadas para métodos SOAP permitem que você envie eventos por push no Adobe Campaign: o método PushEvent permite enviar um evento de cada vez, o método PushEvents permite enviar vários de uma vez. Para obter mais informações, consulte [Descrição do evento](../../message-center/using/event-description.md).

* A criação de um fluxo de trabalho permite recuperar eventos importando arquivos ou por meio de um gateway SQL (com a opção [Federated Data Access](../../installation/using/about-fda.md)).

Depois que são coletados, os eventos são divididos por workflows técnicos entre as filas em tempo real e em lote das instâncias de execução enquanto aguardam a vinculação a um modelo de mensagem.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>Na instância de execução, as pastas **[!UICONTROL Real time events]** ou **[!UICONTROL Batch events]** não devem ser definidas como visualizações, pois isso pode causar problemas de direito de acesso. Para obter mais informações sobre como configurar uma pasta como visualização, consulte [esta seção](../../platform/using/access-management-folders.md).

## Roteamento para um modelo {#routing-towards-a-template}

Depois que o modelo de mensagem é publicado nas instâncias de execução, dois modelos são gerados automaticamente: um para ser vinculado a um evento em tempo real e outro para ser vinculado a um evento em lote.

A etapa de roteamento consiste em vincular um evento ao modelo de mensagem apropriado, com base:

* O tipo de evento especificado nas propriedades do próprio evento:

   ![](assets/messagecenter_event_type_001.png)

* O tipo de evento especificado nas propriedades do modelo de mensagem:

   ![](assets/messagecenter_event_type_002.png)

Por padrão, o roteamento é baseado nas seguintes informações:

* O tipo de evento
* O canal a ser usado (por padrão: email)
* O template do delivery mais recente, com base na data da publicação

## Status do evento {#event-statuses}

O **Histórico de Eventos**, em **[!UICONTROL Event history]** > **[!UICONTROL Message Center]** , agrupa todos os eventos processados em uma única visualização. Eles podem ser categorizados por tipo de evento ou por **status**. Esses status são:

* **Pendente**: o evento pode ser:

   * um evento que foi recém-coletado e que ainda não foi processado. A coluna **[!UICONTROL Number of errors]** mostra o valor 0. O modelo de email ainda não foi vinculado.
   * um evento processado, mas cuja confirmação está incorreta. A coluna **[!UICONTROL Number of errors]** mostra um valor que não é 0. Para saber quando esse evento será processado novamente, consulte a coluna **[!UICONTROL Process requested on]**.

* **Entrega pendente**: o evento foi processado e o modelo de entrega foi vinculado. A entrega do email está pendente e o processo de entrega clássico é aplicado. Para obter mais informações, é possível abrir a entrega.
* **Enviado**, **Ignorado** e **Erro de entrega**: esses status de entrega são recuperados por meio do fluxo de trabalho **updateEventsStatus**. Para obter mais informações, você poderá abrir a entrega relevante.
* **Evento não coberto**: a fase de roteamento de mensagens transacionais falhou. Por exemplo, o Adobe Campaign não encontrou o email que atua como modelo para o evento.
* **Evento expirado**: o número máximo de tentativas de envio foi atingido. O evento é considerado nulo.

## Reciclagem de eventos {#event-recycling}

Se o delivery de uma mensagem em um canal específico falhar, o Adobe Campaign poderá reenviar a mensagem usando um canal diferente. Por exemplo, se um delivery no canal SMS falhar, a mensagem será reenviada usando o canal de email.

Para fazer isso, é necessário configurar um workflow que recrie todos os eventos com o status **Delivery error** e atribuir um canal diferente a eles.

>[!CAUTION]
>
>Essa etapa só poderá ser executada usando um workflow e, portanto, é reservada a usuários experts. Para obter mais informações, entre em contato com o executivo da sua conta da Adobe.