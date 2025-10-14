---
product: campaign
title: Perguntas frequentes sobre fluxos de trabalho
description: Perguntas frequentes sobre o Campaign Classic
feature: Troubleshooting, Workflows
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 7d1bb3c6-d056-4212-9500-75459a0046fa
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 65%

---

# Perguntas frequentes sobre fluxos de trabalho {#workflows-faq}



Saiba como organizar processos e tarefas com fluxos de trabalho do Adobe Campaign.

## Quais são as principais etapas para criar um fluxo de trabalho? {#what-are-the-key-steps-to-create-a-workflow-}

Saiba como criar seu primeiro fluxo de trabalho na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html?lang=pt-BR){target="_blank"}: aprenda conceitos e práticas recomendadas para criar fluxos de trabalho no Campaign.

## Como posso importar dados no Campaign? {#how-can-i-import-data-in-campaign-}

Saiba mais sobre as práticas recomendadas para importar dados [nesta seção](../../platform/using/import-export-best-practices.md).

## Posso monitorar a execução do fluxo de trabalho? {#can-i-monitor-workflow-execution-}

Entenda como monitorar a execução do fluxo de trabalho do Campaign na [documentação do Campaign v8]&#x200B;(https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution
.html){target="_blank"}.

## Como posso atualizar dados do Campaign com um fluxo de trabalho? {#how-can-i-update-campaign-data-with-a-workflow-}

Você pode executar uma atualização em grande escala, mesclar e inserir dados no banco de dados.

Saiba mais na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/update-data.html?lang=pt-BR){target="_blank"}.

## Como posso aproveitar os recursos de gestão de dados? {#how-can-i-leverage-data-management-capabilities-}

No Adobe Campaign, você pode aproveitar um conjunto de atividades para resolver problemas complexos de direcionamento oferecendo ferramentas mais eficientes e flexíveis. As atividades de gestão de dados permitem implementar uma gestão consistente de todas as comunicações com um contato usando informações relacionadas a seus contratos, assinaturas, reatividade a entregas, etc. A gestão de dados permite acompanhar o ciclo de vida dos dados durante as operações de segmentação, em particular:

* Simplificação e otimização de processos de segmentação, ao incluir dados que não são modelados no datamart (criando novas tabelas: extensão local para todo fluxo de trabalho de segmentação, dependendo da configuração).
* Manutenção e transmissão de cálculos de buffer, especialmente durante as fases de construção do target ou para administração de banco de dados.
* Acesso a bases externas (opcional): bancos de dados heterogêneos considerados durante o processo de direcionamento.

Saiba como projetar metas complexas e trabalhar com seus dados combinando atividades de fluxo de trabalho para gestão de dados na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows.html?lang=pt-BR){target="_blank"}.

## Posso automatizar o envio de mensagens personalizadas? {#can-i-automate-personalized-messages-sending-}

Consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/enrich-data.html?lang=pt-BR){target="_blank"} para saber como enviar mensagens personalizadas às pessoas de acordo com suas pontuações mais altas em uma competição.

## Como dividir um público-alvo em subconjuntos com um workflow? {#how-can-i-split-an-audience-in-subsets-with-a-workflow-}

Saiba como dividir um destino em vários subconjuntos na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html?lang=pt-BR){target="_blank"}.

## Como posso atualizar os dados do destinatário de um arquivo externo? {#how-can-i-update-recipient-data-from-an-external-file-}

Você pode modificar determinados campos em uma tabela do Campaign com valores de um arquivo de texto externo.

[Clique aqui para saber como](../../platform/using/import-operations-samples.md#example--enrich-the-values-with-those-of-an-external-file).

## Como posso identificar e direcionar novos destinatários? {#how-can-i-identify-and-target-new-recipients-}

Consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/using-aggregates.html?lang=pt-BR){target="_blank"} para saber como usar agregações para identificar automaticamente os últimos destinatários adicionados ao banco de dados e enviar a eles uma mensagem de boas-vindas.
