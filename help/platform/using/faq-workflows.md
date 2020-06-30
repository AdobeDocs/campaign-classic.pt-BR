---
title: Perguntas frequentes sobre workflows
seo-title: Automatizar processos e gerenciar dados com fluxos de trabalho
description: Perguntas frequentes sobre o Adobe Campaign Classic
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: ht
source-wordcount: '373'
ht-degree: 100%

---


# Perguntas frequentes sobre workflows {#workflows-faq}

Saiba como organizar processos e tarefas com fluxos de trabalho do Adobe Campaign.

## Quais são as principais etapas para criar um fluxo de trabalho? {#what-are-the-key-steps-to-create-a-workflow-}

[Clique aqui para saber como criar seu primeiro fluxo de trabalho](../../workflow/using/building-a-workflow.md): aprenda conceitos e práticas recomendadas para criar fluxos de trabalho no Campaign.

## Como posso importar dados no Campaign? {#how-can-i-import-data-in-campaign-}

Conheça as práticas recomendadas para importar dados por meio de um fluxo de trabalho do Campaign [nesta seção](../../workflow/using/importing-data.md).

## Posso monitorar a execução do fluxo de trabalho? {#can-i-monitor-workflow-execution-}

Entenda como monitorar a execução do fluxo de trabalho do Campaign [nesta página](../../workflow/using/starting-a-workflow.md).

## Como posso atualizar dados do Campaign com um fluxo de trabalho? {#how-can-i-update-campaign-data-with-a-workflow-}

Você pode executar uma atualização em grande escala, mesclar e inserir dados no banco de dados.

[Clique aqui para saber mais](../../workflow/using/update-data.md).

## Como posso aproveitar os recursos de gestão de dados? {#how-can-i-leverage-data-management-capabilities-}

No Adobe Campaign, você pode aproveitar um conjunto de atividades para resolver problemas complexos de definição de metas oferecendo ferramentas mais eficientes e flexíveis. As atividades de gestão de dados permitem implementar uma gestão consistente de todas as comunicações com um contato usando informações relacionadas a seus contratos, assinaturas, reatividade a remessas, etc. A gestão de dados permite acompanhar o ciclo de vida dos dados durante as operações de segmentação, em particular:

* Simplificação e otimização de processos de target, ao incluir dados que não são modelados no datamart (criando novas tabelas: extensão local para todo workflow para construção do target, dependendo da configuração).
* Manutenção e transmissão de cálculos de buffer, especialmente durante as fases de construção do target ou para administração de banco de dados.
* Acesso a bases externas (opcional): bancos de dados heterogêneos considerados durante o processo de segmentação.

[Clique aqui para saber mais](../../workflow/using/targeting-data.md#data-management) e poder projetar metas complexas e trabalhar com seus dados combinando atividades de fluxo de trabalho para gestão de dados.

## Posso automatizar o envio de mensagens personalizadas? {#can-i-automate-personalized-messages-sending-}

Leia [este caso de uso](../../workflow/using/enriching-data.md) para enviar mensagens personalizadas às pessoas de acordo com suas pontuações mais altas em uma competição.

## Como dividir um público em subconjuntos com um fluxo de trabalho? {#how-can-i-split-an-audience-in-subsets-with-a-workflow-}

Saiba como dividir um destino em vários subconjuntos [nesta seção](../../workflow/using/split.md).

## Como posso atualizar os dados do destinatário de um arquivo externo? {#how-can-i-update-recipient-data-from-an-external-file-}

Você pode modificar determinados campos em uma tabela do Campaign com valores de um arquivo de texto externo.

[Clique aqui para saber como](../../platform/using/importing-data.md#example--enrich-the-values-with-those-of-an-external-file).

## Como posso identificar e direcionar novos destinatários? {#how-can-i-identify-and-target-new-recipients-}

[Este caso de uso](../../workflow/using/using-aggregates.md) ensina como usar agregações para identificar automaticamente os últimos destinatários adicionados ao banco de dados e enviar a eles uma mensagem de boas-vindas.
