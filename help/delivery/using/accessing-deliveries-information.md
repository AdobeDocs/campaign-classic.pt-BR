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
source-git-commit: 631e29bd6e59b8ae46084dee3a1d470916a2032b

---


# Acessando informações de deliveries{#accessing-deliveries-information}

## Acessando a lista de deliveries {#accessing-the-list-of-deliveries}

Para acessar a lista de , acesse o universo **[!UICONTROL Campaigns]** e clique no link **[!UICONTROL Deliveries]** Deliveries.

Com o uso da [visualização do Explorer](../../platform/using/adobe-campaign-workspace.md#about-adobe-campaign-explorer), é possível acessar todas os entregas por meio do nó **[!UICONTROL Campaign management > Deliveries]** na árvore.

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

A lista suspensa ao lado do botão **[!UICONTROL Create]** permite filtrar os deliveries com base nos status.

![](assets/delivery_filter_status.png)

## Acessando o calendário de delivery {#accessing-the-delivery-calendar}

To access the delivery calendar, go to the **[!UICONTROL Campaign]** universe and click the **[!UICONTROL Campaign calendar]** link. Este calendário exibe o detalhamento das campanhas ao longo do tempo. Você pode personalizar a exibição por mês, semana ou dia.

![](assets/s_ncs_user_interface_delivery04.png)

Clique no nome de um delivery para exibir as informações principais sobre ele. Também é possível abrir a campanha, se necessário, clicando em **[!UICONTROL Open]**.

![](assets/s_ncs_user_interface_delivery05.png)

## Acessando informações de desempenho de deliveries {#accessing-deliveries-throughput-information}

As informações na página **[!UICONTROL Delivery throughput]** se referem a todos as entregas da plataforma. Para medir a velocidade em que as mensagens são entregues, os critérios são o número de mensagens enviadas por hora e o tamanho das mensagens (em bits por segundo). No exemplo abaixo, o primeiro gráfico mostra as entregas bem-sucedidas em azul e o número de deliveires incorretos em laranja.

Você poderá escolher o intervalo de tempo para o qual a taxa de desempenho é calculada. Para fazer isso, selecione o valor na lista suspensa e clique em **[!UICONTROL Refresh]**.

![](assets/s_ncs_user_interface_delivery06.png)

>[!NOTE]
>
>Para instalações hospedadas ou híbridas, se o MTA aprimorado estiver atualizado, a página **[!UICONTROL Delivery throughput]** não exibe mais a Taxa de transferência aos destinatários de email. Ele mostra a velocidade da Taxa de transferência para o relé das suas mensagens do Campaign para o MTA aprimorado.
>
>Para obter mais informações sobre o MTA aprimorado do Adobe Campaign, consulte este [documento](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html).