---
title: Acessando informações de deliveries
seo-title: Acessando informações de deliveries
description: Acessando informações de deliveries
seo-description: null
page-status-flag: never-activated
uuid: dc8f0267-1884-4a39-9a7d-d5ef21932928
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: d2631c67-7781-4baa-b24e-e7921353d131
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 211556bbf023731ffeab2e90692410a852ab3555

---


# Acessando informações de deliveries{#accessing-deliveries-information}

## Acessando a lista de deliveries {#accessing-the-list-of-deliveries}

To access the list of deliveries, go to the **[!UICONTROL Campaigns]** universe and click the **[!UICONTROL Deliveries]** link.

If you use [the Explorer view](../../platform/using/adobe-campaign-workspace.md#about-adobe-campaign-explorer), you can access all deliveries via the **[!UICONTROL Campaign management > Deliveries]** node in the tree.

>[!NOTE]
>
>A área de trabalho do Adobe Campaign é apresentado [nesta seção](../../platform/using/adobe-campaign-workspace.md).

Essa página permite que você acesse uma exibição geral dos deliveries: exibe todas os deliveries no seu banco de dados. Você poderá visualizar o status, taxa de sucesso e datas de modificação.

![](assets/d_ncs_user_filter_interface_delivery01.png)

>[!NOTE]
>
>A filtragem de informações é apresentada [nesta seção](../../platform/using/filtering-options.md).

O assistente de delivery permite configurar seus deliveries, iniciar o processo de aprovação e enviar. O conteúdo do assistente depende do canal de comunicação (email, celular, push, mala direta) e dos direitos do operador.

Para manipular os deliveries na lista, clique em uma delivery. Ela abrirá em uma nova janela e você poderá confirmar seu delivery ou pausá-lo.

![](assets/s_ncs_user_interface_delivery02.png)

Dependendo do estágio do ciclo de delivery, os principais status possíveis são:

* Cancelado
* Failed
* Pending
* Concluído
* Em pausa
* Repetição pendente
* Em andamento
* Pronto para delivery
* Preparo em andamento
* Cálculo do target
* Em edição

Cada status tem sua própria cor e rótulo.

![](assets/s_ncs_user_status_campaigns_120.png)

The drop-down list next to the **[!UICONTROL Create]** button enables you to filter deliveries based on their status.

![](assets/delivery_filter_status.png)

## Acessando o calendário de delivery {#accessing-the-delivery-calendar}

To access the delivery calendar, go to the **[!UICONTROL Campaign]** universe and click the **[!UICONTROL Campaign calendar]** link. Este calendário exibe o detalhamento das campanhas ao longo do tempo. Você pode personalizar a exibição por mês, semana ou dia.

![](assets/s_ncs_user_interface_delivery04.png)

Clique no nome de um delivery para exibir as informações principais sobre ele. You can also open the campaign if necessary by clicking **[!UICONTROL Open]**.

![](assets/s_ncs_user_interface_delivery05.png)

## Acessando informações de desempenho de deliveries {#accessing-deliveries-throughput-information}

The information on the **[!UICONTROL Delivery throughput]** page concerns all the deliveries of the platform. Para medir a velocidade em que as mensagens são entregues, os critérios são o número de mensagens enviadas por hora e o tamanho das mensagens (em bits por segundo). No exemplo abaixo, o primeiro gráfico mostra as entregas bem-sucedidas em azul e o número de deliveires incorretos em laranja.

Você poderá escolher o intervalo de tempo para o qual a taxa de desempenho é calculada. To do this, select the value from the drop-down list, and then click **[!UICONTROL Refresh]**.

![](assets/s_ncs_user_interface_delivery06.png)

>[!NOTE]
>
>Para instalações hospedadas ou híbridas, se você tiver atualizado para o MTA aprimorado, a **[!UICONTROL Delivery throughput]** página não exibirá mais a saída para seus destinatários de email. Ele mostrará a velocidade de throughput para o relé de suas mensagens do Campaign para o MTA aprimorado.
>
>Para obter mais informações sobre o Adobe Campaign Enhanced MTA, consulte este [documento](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html).