---
product: campaign
title: Práticas recomendadas de desempenho de entrega
description: Saiba mais sobre o desempenho da entrega e as práticas recomendadas
feature: Deliverability
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 6%

---

# Práticas recomendadas de desempenho de entrega {#delivery-performances}

>[!NOTE]
>
>Orientações abrangentes sobre o desempenho do delivery e as práticas recomendadas estão documentadas na página [Práticas recomendadas de delivery do Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices). Esse conteúdo se aplica aos usuários do Campaign Classic v7 e do Campaign v8.
>
>Esta página documenta **configurações de desempenho específicas do Campaign Classic v7** para implantações híbridas e locais.

Para obter práticas recomendadas abrangentes sobre desempenho de entrega, otimização de plataforma, gerenciamento de quarentena, manutenção de banco de dados e recomendações de agendamento, consulte a [documentação de Práticas recomendadas de entrega do Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}.

## Ajuste de desempenho {#best-practices-performance}

Para **implantações híbridas/no local do Campaign Classic v7**, as seguintes otimizações de banco de dados e infraestrutura podem melhorar o desempenho da entrega:

### Otimização do banco de dados

**Endereços de índice** para otimizar o desempenho de consultas SQL usadas no aplicativo. Um índice pode ser declarado a partir do elemento principal do schema de dados. Essa otimização requer acesso direto ao banco de dados e personalização de esquema disponíveis em implantações locais.

### Ajuste da infraestrutura

**Configuração de entregas grandes**: entregas para mais de um milhão de destinatários precisam de espaço nas filas de envio. Para instalações no local, os MTA secundários podem ser configurados para lidar com tamanhos de lote personalizados. Entre em contato com o administrador do sistema para ajustar essas configurações com base na capacidade da infraestrutura.

>[!NOTE]
>
>Para usuários do Campaign v8 Managed Cloud Services, a otimização da infraestrutura e a configuração do MTA são gerenciadas pela Adobe. Consulte as [Práticas recomendadas de entrega do Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} para obter as recomendações de desempenho aplicáveis à sua implantação.

## Manutenção do banco de dados {#performance-issues}

Para **implantações híbridas/no local do Campaign Classic v7**, a manutenção da plataforma e do banco de dados afeta diretamente o desempenho de envio da entrega.

As tarefas de manutenção regulares incluem:

**Limpeza do banco de dados**: use o fluxo de trabalho de limpeza do banco de dados para remover logs de entrega, dados de rastreamento e tabelas temporárias antigos. Uma manutenção deficiente do banco de dados pode retardar a preparação e o envio do delivery.

**Monitoramento do desempenho do banco de dados**: Monitore o desempenho da consulta, a fragmentação do índice e as estatísticas da tabela. Para obter orientações detalhadas, consulte [esta página](../../production/using/database-performances.md).

**Monitoramento do fluxo de trabalho técnico**: verifique se todos os fluxos de trabalho técnicos (especialmente os de limpeza, rastreamento e atualização da capacidade de entrega) estão sendo executados corretamente sem erros.

>[!NOTE]
>
>Para usuários do Campaign v8 Managed Cloud Services, a manutenção do banco de dados e os workflows técnicos são monitorados e gerenciados pela Adobe. Concentre-se no monitoramento específico de entrega, conforme descrito na [Documentação de monitoramento de entregas do Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}.

## Tópicos relacionados

* [Práticas recomendadas de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentação do Campaign v8)
* [Monitorar sua capacidade de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"} (documentação do Campaign v8)
* [Solução de problemas de entrega](delivery-troubleshooting.md)
* [Desempenhos do banco de dados](../../production/using/database-performances.md) (v7 híbrido/no local)
