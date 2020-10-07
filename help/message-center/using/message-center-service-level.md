---
title: Nível de serviço do Centro de mensagens
seo-title: Nível de serviço do Centro de mensagens
description: Nível de serviço do Centro de mensagens
seo-description: null
page-status-flag: never-activated
uuid: 8e363706-292b-40db-97bc-d41b41910556
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: reports
discoiquuid: e46a4e87-6c02-4b9c-bf6d-bb4e785e78fa
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 72%

---


# Nível de serviço do Centro de mensagens{#message-center-service-level}

Esse relatório exibe as estatísticas de delivery relacionadas às mensagens transacionais, bem como a discriminação de erros. Você pode clicar em um tipo de erro para exibir seus detalhes. Esse relatório, destinado aos administradores técnicos, também pode ser acessado por meio do universo **[!UICONTROL Monitoring]** na instância de controle.

![](assets/mc_reports_1.png)

Nesse relatório, você pode exibir as estatísticas gerais ou aquelas relativas a uma instância de execução específica. Você também pode filtrar os dados por canal e por um período específico. The indicators displayed in the **[!UICONTROL Indicators over the period]** section are calculated over the period selected:

* **[!UICONTROL Incoming (throughput event/h)]** : número médio por hora de eventos inseridos na fila do Centro de mensagens.
* **[!UICONTROL Incoming (event vol)]** : número de eventos inseridos na fila do Centro de mensagens.
* **[!UICONTROL Outgoing (throughput msg/h)]** : número médio por hora de eventos de saída bem-sucedidos do Centro de mensagens (enviados por um delivery).
* **[!UICONTROL Outgoing (msg vol)]** : número de eventos bem-sucedidos do Centro de mensagens de saída (enviados por um delivery).
* **[!UICONTROL Average sending time (seconds)]** : tempo médio gasto no Centro de Mensagens para eventos processados com êxito. O cálculo leva em conta o tempo do processamento e o tempo de envio mta.
* **[!UICONTROL Error rate]**: número de eventos com erros comparados ao número de eventos que entraram na fila do Centro de mensagens. Os erros a seguir são levados em conta: erro de roteamento, evento expirado (evento que está na fila por muito tempo), erro de delivery, ignorado pelo delivery (quarentena, etc.).

>[!NOTE]
>
>Os limites de indicador de aviso (laranja) e de alerta (vermelho) podem ser configurados no assistente de implantação. Consulte [Limites de monitoramento](../../message-center/using/monitoring-thresholds.md).

