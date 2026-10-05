---
product: campaign
title: Nível de serviço do Centro de mensagens
description: Saiba mais sobre o relatório de nível de serviço do Centro de mensagens
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: reports
exl-id: b8dc9891-84c8-445d-ad6a-d06048c8faaf
TQID: 'https://experienceleague.adobe.com/v9s-xydUk-4cNxNYSAj1HLCOOscZhpQDP-bSJt9mUzg'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 100%
---
# Nível de serviço do Centro de mensagens {#message-center-service-level}



Esse relatório exibe as estatísticas de entrega relacionadas às mensagens transacionais, bem como o detalhamento de erros. Você pode clicar em um tipo de erro para exibir os detalhes.

Esse relatório, destinado aos administradores técnicos, também pode ser acessado por meio da guia **[!UICONTROL Monitoring]** na instância de controle.

![](assets/mc_reports_1.png)

Nesse relatório, você pode exibir as estatísticas gerais ou aquelas relativas a uma instância de execução específica. Você também pode filtrar os dados por canal e por um período específico.

Os indicadores exibidos na seção **[!UICONTROL Indicators over the period]** são calculados sobre o período selecionado:

* **[!UICONTROL Incoming (throughput event/h)]** : número médio de horas de eventos inseridos na fila do Centro de mensagens.
* **[!UICONTROL Incoming (event vol)]** : número de eventos inseridos na fila do Centro de mensagens.
* **[!UICONTROL Outgoing (throughput msg/h)]** : número médio de horas de eventos de saída bem-sucedidos do Centro de mensagens (enviados por uma entrega).
* **[!UICONTROL Outgoing (msg vol)]** : número de eventos de saída bem-sucedidos do Centro de mensagens (enviados por uma entrega).
* **[!UICONTROL Average sending time (seconds)]** : tempo médio gasto no Centro de mensagens para eventos processados com êxito. O cálculo leva em conta o tempo do processamento e o tempo de envio mta.
* **[!UICONTROL Error rate]**: número de eventos com erros comparados ao número de eventos que entraram na fila do Centro de mensagens. Os erros a seguir são levados em conta: erro de roteamento, evento expirado (evento que está na fila por muito tempo), erro de entrega, ignorado pela entrega (quarentena, etc.).

>[!NOTE]
>
>Os limites de indicador de aviso (laranja) e de alerta (vermelho) podem ser configurados no assistente de implantação. Consulte [Monitorar limites](../../message-center/using/additional-configurations.md#monitoring-thresholds).
