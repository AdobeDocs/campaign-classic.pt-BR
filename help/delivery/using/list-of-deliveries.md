---
solution: Campaign Classic
product: campaign
title: Acessando a lista de deliveries
description: Saiba como acessar a lista de delivery criados.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: f2a126d0aa471831f84d4c8457cfd6f0fae7b14f
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 94%

---


# Acessando a lista de deliveries {#list-of-deliveries}

Você pode acessar deliveries a partir da lista de delivery, por meio do nó **[!UICONTROL Campaign Management > Deliveries]** da árvore.

![](assets/deliveries-list.png)

Por padrão, a lista de deliveries contém os nomes e os status dos deliveries criados no nó selecionado. Ele também mostra o número de mensagens a serem enviadas, processadas e enviadas com sucesso.

* O número de **[!UICONTROL Messages to send]** corresponde ao número de recipients target após a análise e antes do delivery.
* O número de mensagens na coluna **[!UICONTROL Success]** corresponde ao número de mensagens enviadas pelo servidor e recebidas pelos recipients.
* O número de mensagens **[!UICONTROL Processed]** corresponde ao número de mensagens recebidas mais o número de mensagens com erros.

>[!NOTE]
>
>Para deliveries grandes, convém atualizar esses valores. Para fazer isso, selecione o delivery em questão e clique com o botão direito nele. Selecione **[!UICONTROL Action > Recompute delivery and tracking indicators...]** e depois use o assistente para atualizar essas informações.

**Tópicos relacionados:**

* [Painel de delivery](../../delivery/using/delivery-dashboard.md)
* [Status de delivery](../../delivery/using/delivery-statuses.md)
