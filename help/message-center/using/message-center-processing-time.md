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
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '216'
ht-degree: 100%

---


# Tempo de processamento do Centro de mensagens{#message-center-processing-time}

Esse relatório exibe os indicadores principais relacionados à fila em tempo real. Esse relatório, destinado aos administradores técnicos, também pode ser acessado por meio do universo **[!UICONTROL Monitoring]** na instância de controle.

![](assets/mc_reports_2.png)

Assim como para o relatório **[!UICONTROL Message Center service level]**, você pode exibir as estatísticas gerais ou aquelas relativas a uma instância de execução específica. Você também pode filtrar os dados por canal e por um período específico. Os indicadores exibidos na seção **[!UICONTROL Indicators over the period]** são calculados sobre o período selecionado:

* **[!UICONTROL Average queuing time]**: o tempo médio que processou eventos com êxito no Centro de mensagens. Somente o tempo de processamento é levado em conta.
* **[!UICONTROL Average message sending time (s)]**: o tempo médio que processou eventos com êxito no Centro de mensagens. Somente o tempo de delivery mta é levado em conta.
* **[!UICONTROL Average processing time (s)]**: o tempo médio que processou eventos com êxito no Centro de mensagens. O cálculo leva em conta o tempo do processamento e o tempo de envio mta.
* **[!UICONTROL Maximum number of queued events]**: número máximo de eventos presentes na fila do Centro de mensagens em um determinado momento.
* **[!UICONTROL Minimum number of queued events]**: número mínimo de eventos presentes na fila do Centro de mensagens em um determinado momento.
* **[!UICONTROL Average number of queued events]**: número médio de eventos presentes na fila do Centro de mensagens em um determinado momento.

>[!NOTE]
>
>Os limites de indicador de aviso (laranja) e de alerta (vermelho) podem ser configurados no assistente de implantação do Adobe Campaign. Consulte [Limites de monitoramento](../../message-center/using/monitoring-thresholds.md).

