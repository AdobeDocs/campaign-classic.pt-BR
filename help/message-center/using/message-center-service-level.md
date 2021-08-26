---
product: campaign
title: Nível de serviço do Centro de mensagens
description: Saiba mais sobre o relatório de nível de serviço do Centro de mensagens.
audience: message-center
content-type: reference
topic-tags: reports
exl-id: b8dc9891-84c8-445d-ad6a-d06048c8faaf
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 100%

---

# Nível de serviço do Centro de mensagens {#message-center-service-level}

![](../../assets/v7-only.svg)

Esse relatório exibe as estatísticas de entrega relacionadas às mensagens transacionais, bem como o detalhamento de erros. Você pode clicar em um tipo de erro para exibir os detalhes.

Esse relatório, destinado aos administradores técnicos, também pode ser acessado por meio da guia **[!UICONTROL Monitoring]** na instância de controle.

![](assets/mc_reports_1.png)

Nesse relatório, você pode exibir as estatísticas gerais ou aquelas relativas a uma instância de execução específica. Você também pode filtrar os dados por canal e por um período específico.

Os indicadores exibidos na seção **[!UICONTROL Indicators over the period]** são calculados sobre o período selecionado:

* **[!UICONTROL Incoming (throughput event/h)]** : número médio de horas de eventos inseridos na fila do Centro de mensagens.
* **[!UICONTROL Incoming (event vol)]** : número de eventos inseridos na fila do Centro de mensagens.
* **[!UICONTROL Outgoing (throughput msg/h)]** : número médio de horas de eventos de saída bem-sucedidos do Centro de mensagens (enviados por um delivery).
* **[!UICONTROL Outgoing (msg vol)]** : número de eventos de saída bem-sucedidos do Centro de mensagens (enviados por um delivery).
* **[!UICONTROL Average sending time (seconds)]** : tempo médio gasto no Centro de mensagens para eventos processados com êxito. O cálculo leva em conta o tempo do processamento e o tempo de envio mta.
* **[!UICONTROL Error rate]**: número de eventos com erros comparados ao número de eventos que entraram na fila do Centro de mensagens. Os erros a seguir são levados em conta: erro de roteamento, evento expirado (evento que está na fila por muito tempo), erro de delivery, ignorado pelo delivery (quarentena, etc.).

>[!NOTE]
>
>Os limites de indicador de aviso (laranja) e de alerta (vermelho) podem ser configurados no assistente de implantação. Consulte [Monitorar limites](../../message-center/using/additional-configurations.md#monitoring-thresholds).
