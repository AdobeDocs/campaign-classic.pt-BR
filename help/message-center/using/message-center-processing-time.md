---
product: campaign
title: Tempo de processamento do Centro de mensagens
description: Saiba mais sobre o relatório de tempo de processamento do Centro de mensagens.
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
source-git-commit: e86350cf12db37e3f2c227563057b97922601729
workflow-type: ht
source-wordcount: '217'
ht-degree: 100%

---

# Tempo de processamento do Centro de mensagens {#message-center-processing-time}

Esse relatório exibe os indicadores principais relacionados à fila em tempo real.

Esse relatório, destinado aos administradores técnicos, também pode ser acessado por meio da guia **[!UICONTROL Monitoring]** na instância de controle.

![](assets/mc_reports_2.png)

Assim como para o relatório **[!UICONTROL Message Center service level]**, você pode exibir as estatísticas gerais ou as relativas a uma instância de execução específica. Você também pode filtrar os dados por canal e por um período específico.

Os indicadores exibidos na seção **[!UICONTROL Indicators over the period]** são calculados sobre o período selecionado:

* **[!UICONTROL Average queuing time]**: o tempo médio que processou eventos com êxito no Centro de mensagens. Somente o tempo de processamento é levado em conta.
* **[!UICONTROL Average message sending time (s)]**: o tempo médio que processou eventos com êxito no Centro de mensagens. Somente o tempo de delivery mta é levado em conta.
* **[!UICONTROL Average processing time (s)]**: o tempo médio que processou eventos com êxito no Centro de mensagens. O cálculo leva em conta o tempo do processamento e o tempo de envio mta.
* **[!UICONTROL Maximum number of queued events]**: número máximo de eventos presentes na fila do Centro de mensagens em um determinado momento.
* **[!UICONTROL Minimum number of queued events]**: número mínimo de eventos presentes na fila do Centro de mensagens em um determinado momento.
* **[!UICONTROL Average number of queued events]**: número médio de eventos presentes na fila do Centro de mensagens em um determinado momento.

>[!NOTE]
>
>Os limites de indicador de aviso (laranja) e de alerta (vermelho) podem ser configurados no assistente de implantação do Adobe Campaign. Consulte [Monitorar limites](../../message-center/using/additional-configurations.md#monitoring-thresholds).
