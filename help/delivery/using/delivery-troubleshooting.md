---
product: campaign
title: Solução de problemas de envio de entrega
description: Saiba mais sobre o desempenho da entrega e como solucionar problemas relacionados ao monitoramento da entrega
feature: Monitoring, Deliverability, Troubleshooting
role: User
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 16%

---

# Solução de problemas de envio de entrega {#delivery-troubleshooting}

>[!NOTE]
>
>Orientações abrangentes sobre a solução de problemas de delivery estão documentadas na documentação do Campaign v8, aplicável aos usuários do Campaign Classic v7 e do Campaign v8:
>
>* Falhas de entrega comuns e soluções: [Noções básicas sobre falhas de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* Diagnóstico de entrega lenta: [Monitorar entregas na interface do Campaign](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* Práticas recomendadas de entrega: [Práticas recomendadas de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>Esta página documenta a **solução de problemas específica do Campaign Classic v7** para implantações híbridas e locais.

## Solução de problemas {#v7-specific}

Para **implantações híbridas/no local do Campaign Classic v7**, as seguintes etapas de solução de problemas são específicas para a infraestrutura que você gerencia:

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
>Para usuários do Campaign v8 Managed Cloud Services, os workflows técnicos e o monitoramento da infraestrutura são gerenciados pela Adobe. Concentre-se no conteúdo de entrega e no direcionamento conforme descrito na [documentação do Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

## Tópicos relacionados

* [Noções básicas sobre falhas de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (documentação do Campaign v8)
* [Práticas recomendadas de entrega](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentação do Campaign v8)
* [Monitorar entregas na interface do Campaign](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (documentação do Campaign v8)
* [Manutenção do banco de dados](../../production/using/recommendations.md) (v7 híbrido/no local)
* [Entregabilidade de email](../../installation/using/email-deliverability.md) (v7 híbrido/no local)
