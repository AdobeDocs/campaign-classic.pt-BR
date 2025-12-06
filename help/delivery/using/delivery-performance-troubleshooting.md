---
product: campaign
title: Desempenho da entrega e solução de problemas
description: Saiba como otimizar o desempenho do delivery e solucionar problemas no Campaign Classic v7
feature: Monitoring, Deliverability, Troubleshooting
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 5%

---

# Desempenho da entrega e solução de problemas {#delivery-performance-troubleshooting}

>[!NOTE]
>
>Orientações abrangentes sobre o desempenho do delivery e as práticas recomendadas estão documentadas na página [Práticas recomendadas de delivery do Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices). Esse conteúdo se aplica aos usuários do Campaign Classic v7 e do Campaign v8.
>
>Esta página documenta **configurações específicas do Campaign Classic v7** para otimização de desempenho e solução de problemas em implantações híbridas e locais.

Para obter práticas recomendadas abrangentes sobre desempenho de entrega, otimização de plataforma, gerenciamento de quarentena, manutenção de banco de dados e recomendações de agendamento, consulte a [documentação de Práticas recomendadas de entrega do Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}.

## Otimização do desempenho {#performance-optimization}

Para **implantações híbridas/no local do Campaign Classic v7**, as seguintes otimizações de banco de dados e infraestrutura podem melhorar o desempenho da entrega.

### Otimização do banco de dados

**Endereços de índice** para otimizar o desempenho de consultas SQL usadas no aplicativo. Um índice pode ser declarado a partir do elemento principal do schema de dados. Essa otimização requer acesso direto ao banco de dados e personalização de esquema disponíveis em implantações locais.

### Ajuste da infraestrutura

**Configuração de entregas grandes**: entregas para mais de um milhão de destinatários precisam de espaço nas filas de envio. Para instalações no local, os MTA secundários podem ser configurados para lidar com tamanhos de lote personalizados. Entre em contato com o administrador do sistema para ajustar essas configurações com base na capacidade da infraestrutura.

>[!NOTE]
>
>Para usuários do Campaign v8 Managed Cloud Services, a otimização da infraestrutura e a configuração do MTA são gerenciadas pela Adobe. Consulte as [Práticas recomendadas de entrega do Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} para obter as recomendações de desempenho aplicáveis à sua implantação.

### Manutenção do banco de dados {#database-maintenance}

Para **implantações híbridas/no local do Campaign Classic v7**, a manutenção da plataforma e do banco de dados afeta diretamente o desempenho de envio da entrega.

As tarefas de manutenção regulares incluem:

**Limpeza do banco de dados**: use o fluxo de trabalho de limpeza do banco de dados para remover logs de entrega, dados de rastreamento e tabelas temporárias antigos. Uma manutenção deficiente do banco de dados pode retardar a preparação e o envio do delivery.

**Monitoramento do desempenho do banco de dados**: Monitore o desempenho da consulta, a fragmentação do índice e as estatísticas da tabela. Para obter orientações detalhadas, consulte [esta página](../../production/using/database-performances.md).

**Monitoramento do fluxo de trabalho técnico**: verifique se todos os fluxos de trabalho técnicos (especialmente os de limpeza, rastreamento e atualização da capacidade de entrega) estão sendo executados corretamente sem erros.

>[!NOTE]
>
>Para usuários do Campaign v8 Managed Cloud Services, a manutenção do banco de dados e os workflows técnicos são monitorados e gerenciados pela Adobe. Concentre-se no monitoramento específico de entrega, conforme descrito na [Documentação de monitoramento de entregas do Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}.

## Solução de problemas de entrega {#troubleshooting}

>[!NOTE]
>
>Orientações abrangentes sobre a solução de problemas de delivery estão documentadas na documentação do Campaign v8, aplicável aos usuários do Campaign Classic v7 e do Campaign v8:
>
>* Falhas de entrega comuns e soluções: [Noções básicas sobre falhas de entrega](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* Diagnóstico de entrega lenta: [Monitorar entregas na interface do Campaign](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* Práticas recomendadas de entrega: [Práticas recomendadas de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>Esta seção documenta a **solução de problemas específica do Campaign Classic v7** para implantações híbridas e locais.

Para **implantações híbridas/no local do Campaign Classic v7**, as seguintes etapas de solução de problemas são específicas para a infraestrutura que você gerencia.

### Configuração de regras MX

Se você tiver problemas de limitação com ISPs específicos, talvez seja necessário revisar e ajustar a configuração das regras MX. Para obter mais informações sobre regras MX e cotas, consulte [esta seção](../../installation/using/email-deliverability.md#about-mx-rules).

### Manutenção do banco de dados para desempenho do delivery

Se você encontrar o seguinte erro em implantações de mid-sourcing:

```
Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
```

A causa está vinculada a problemas de desempenho em que a instância de marketing gasta muito tempo criando dados antes de enviá-los ao servidor mid-sourcing.

**Para instalações locais**, execute um vácuo e reindexe no banco de dados. Para obter mais informações sobre manutenção de banco de dados, consulte [esta seção](../../production/using/recommendations.md).

Você também deve reiniciar todos os fluxos de trabalho com uma atividade agendada e todos os fluxos de trabalho com o status de falha. Consulte [esta seção](../../workflow/using/scheduler.md).

### Monitoramento do fluxo de trabalho técnico

Para instalações no local, verifique se todos os workflows técnicos relacionados à capacidade de entrega estão sendo executados sem erros:

**Fluxo de trabalho de atualização da capacidade de entrega**: atualiza as regras de qualificação de email de devolução e os indicadores de capacidade de entrega.

**Fluxo de trabalho de rastreamento**: processa os dados de rastreamento das entregas enviadas.

**Fluxo de trabalho de limpeza do banco de dados**: limpa regularmente logs de entrega antigos e tabelas temporárias para manter o desempenho.

Verifique o status do fluxo de trabalho em **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

>[!NOTE]
>
>Para usuários do Campaign v8 Managed Cloud Services, os workflows técnicos e o monitoramento da infraestrutura são gerenciados pela Adobe. Concentre-se no conteúdo de entrega e no direcionamento conforme descrito na [documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

## Tópicos relacionados

* [Noções básicas sobre falhas de entrega](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (documentação do Campaign v8)
* [Práticas recomendadas de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentação do Campaign v8)
* [Monitorar entregas na interface do Campaign](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (documentação do Campaign v8)
* [Manutenção do banco de dados](../../production/using/recommendations.md) (v7 híbrido/no local)
* [Entregabilidade de email](../../installation/using/email-deliverability.md) (v7 híbrido/no local)
* [Desempenhos do banco de dados](../../production/using/database-performances.md) (v7 híbrido/no local)

