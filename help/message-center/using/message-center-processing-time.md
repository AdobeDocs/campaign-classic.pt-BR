---
title: Tempo de processamento do Centro de mensagens
seo-title: Tempo de processamento do Centro de mensagens
description: Tempo de processamento do Centro de mensagens
seo-description: null
page-status-flag: never-activated
uuid: 06aca2c2-33c0-4839-bee4-fd838c49ce76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: reports
discoiquuid: d1f591d2-95e8-4d99-bc60-955c96b532eb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Tempo de processamento do Centro de mensagens{#message-center-processing-time}

Esse relatório exibe os indicadores principais relacionados à fila em tempo real. This report, aimed at technical administrators, can also be accessed via the **[!UICONTROL Monitoring]** universe in the control instance.

![](assets/mc_reports_2.png)

Just like for the **[!UICONTROL Message Center service level]** report, you can choose to display the overall statistics or those relative to a particular execution instance. Você também pode filtrar os dados por canal e por um período específico. The indicators displayed in the **[!UICONTROL Indicators over the period]** section are calculated over the period selected:

* **[!UICONTROL Average queuing time]** : o tempo médio que processou com êxito os eventos gastos no Centro de Mensagens. Somente o tempo de processamento é levado em conta.
* **[!UICONTROL Average message sending time (s)]** : o tempo médio que processou com êxito os eventos gastos no Centro de Mensagens. Somente o tempo de delivery mta é levado em conta.
* **[!UICONTROL Average processing time (s)]** : o tempo médio que processou com êxito os eventos gastos no Centro de Mensagens. O cálculo leva em conta o tempo do processamento e o tempo de envio mta.
* **[!UICONTROL Maximum number of queued events]** : número máximo de eventos presentes na fila do Centro de Mensagens em qualquer momento.
* **[!UICONTROL Minimum number of queued events]** : número mínimo de eventos presentes na fila do Centro de Mensagens em qualquer momento.
* **[!UICONTROL Average number of queued events]** : número médio de eventos presentes na fila do Centro de Mensagens em qualquer momento.

>[!NOTE]
>
>Os limites de indicador de aviso (laranja) e de alerta (vermelho) podem ser configurados no assistente de implantação do Adobe Campaign. Consulte Limites [de monitoramento](../../message-center/using/monitoring-thresholds.md).

