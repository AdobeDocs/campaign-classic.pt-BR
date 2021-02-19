---
solution: Campaign Classic
product: campaign
title: Nível de serviço do Centro de mensagens
description: Nível de serviço do Centro de mensagens
audience: message-center
content-type: reference
topic-tags: reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 100%

---


# Nível de serviço do Centro de mensagens{#message-center-service-level}

Esse relatório exibe as estatísticas de delivery relacionadas às mensagens transacionais, bem como a discriminação de erros. Você pode clicar em um tipo de erro para exibir seus detalhes. Esse relatório, destinado aos administradores técnicos, também pode ser acessado por meio do universo **[!UICONTROL Monitoring]** na instância de controle.

![](assets/mc_reports_1.png)

Nesse relatório, você pode exibir as estatísticas gerais ou aquelas relativas a uma instância de execução específica. Você também pode filtrar os dados por canal e por um período específico. Os indicadores exibidos na seção **[!UICONTROL Indicators over the period]** são calculados sobre o período selecionado:

* **[!UICONTROL Incoming (throughput event/h)]** : número médio de horas de eventos inseridos na fila do Centro de mensagens.
* **[!UICONTROL Incoming (event vol)]** : número de eventos inseridos na fila do Centro de mensagens.
* **[!UICONTROL Outgoing (throughput msg/h)]** : número médio de horas de eventos de saída bem-sucedidos do Centro de mensagens (enviados por um delivery).
* **[!UICONTROL Outgoing (msg vol)]** : número de eventos de saída bem-sucedidos do Centro de mensagens (enviados por um delivery).
* **[!UICONTROL Average sending time (seconds)]** : tempo médio gasto no Centro de mensagens para eventos processados com êxito. O cálculo leva em conta o tempo do processamento e o tempo de envio mta.
* **[!UICONTROL Error rate]**: número de eventos com erros comparados ao número de eventos que entraram na fila do Centro de mensagens. Os erros a seguir são levados em conta: erro de roteamento, evento expirado (evento que está na fila por muito tempo), erro de delivery, ignorado pelo delivery (quarentena, etc.).

>[!NOTE]
>
>Os limites de indicador de aviso (laranja) e de alerta (vermelho) podem ser configurados no assistente de implantação. Consulte [Limites de monitoramento](../../message-center/using/monitoring-thresholds.md).

