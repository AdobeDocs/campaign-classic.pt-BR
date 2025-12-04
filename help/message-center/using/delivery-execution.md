---
product: campaign
title: Execução da entrega
description: Saiba mais sobre a execução e o monitoramento da entrega de mensagens transacionais
feature: Transactional Messaging, Message Center, Monitoring
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 930c6395-0c00-40ee-a925-3e0cae67c55f
source-git-commit: e60a8391416bc9899548971bddb61705467a80e5
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 99%

---

# Execução da entrega {#delivery-execution}



## Envio de mensagem transacional {#transactional-message-send}

Na instância de execução, uma vez que o estágio de enriquecimento esteja completo e um modelo da entrega esteja vinculado ao evento, a entrega será enviada.

>[!NOTE]
>
>O MTA prioriza o processamento das mensagens transacionais ante qualquer outra entrega.

Todas as entregas são agrupadas na pasta **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]**.

![](assets/messagecenter_deliveries_execinstances_001.png)

Por padrão, elas são classificadas em subpastas por mês de entrega. Essa classificação poderá ser alterada nas propriedades do modelo de mensagem conforme mostrado abaixo.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>Para instalações hospedadas ou híbridas, se você atualizou para o [MTA aprimorado](../../delivery/using/sending-with-enhanced-mta.md), todas as mensagens transacionais também podem ser enviadas com o MTA aprimorado do Adobe Campaign para melhorar a capacidade de entrega, a taxa de transferência e o tratamento de rejeições. Todos os impactos são os mesmos que os das mensagens de marketing padrão.

## Monitoramento de mensagens transacionais {#transactional-message-monitoring}

Para monitorar as mensagens transacionais, verifique os [logs da entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard#delivery-logs-and-history){target="_blank"}.

As entregas transacionais enviadas da instância de execução são sincronizadas de volta à instância de controle por meio de um fluxo de trabalho técnico (**[!UICONTROL Message Center execution instance]**) que é executado a cada hora.

>[!NOTE]
>
>As entregas acumulam semanalmente os eventos com base na atualização mais recente do evento, e não na data de criação do evento. Portanto, ao extrair logs da entrega de mensagens transacionais da instância de controle, a ID da entrega associada a cada ID de log da entrega pode mudar com o tempo, conforme o log é atualizado (por exemplo, quando uma rejeição de entrada é recebida para o evento).

<!--The transactional deliveries sent from the execution instance are synchronized back to the control instance as follows.

Let's take a [delivery template](../../message-center/using/introduction.md) labelled *Template_1*.

1. An event corresponding to *Template_1* is received on the execution instance.
1. The **Processing real time events** (rtEventsProcessing) workflow processes the event and searches for an existing delivery for the current month.

    >[!NOTE]
    >
    >If not found, a new delivery is created and the event is assigned to the new delivery.

1. The transactional email is sent and the delivery status changes to **[!UICONTROL Sent]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and updates the delivery logs on the control instance.
1. The control instance searches for an existing delivery for week 40 (2020-09-28_Template_1).

    >[!NOTE]
    >
    >If not found, a new delivery is created.

1. The week after, an inbound bounce is received for the event.
1. The status of the event changes to **[!UICONTROL Delivery failed]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and searches for a delivery for week 41 (2020-10-05_Template_1) to update the delivery logs. The delivery logs are then linked to a new delivery for the current week.

To summarize, the deliveries weekly accumulate the events based on the latest event update, and not on the event creation date.

Therefore, when extracting transactional messaging delivery logs from the control instance, the delivery ID associated with each delivery log ID changes every week.-->

Para monitorar a atividade e a execução da(s) instância(s) de execução, consulte [Relatórios de mensagens transacionais](../../message-center/using/about-transactional-messaging-reports.md).
