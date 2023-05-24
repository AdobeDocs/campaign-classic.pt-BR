---
product: campaign
title: Práticas recomendadas e limitações do FDA do Campaign
description: Saiba mais sobre as práticas recomendadas e limitações ao trabalhar com um banco de dados externo (FDA)
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 40%

---

# Práticas recomendadas e limitações



## Otimizar a personalização de email com dados externos {#optimizing-email-personalization-with-external-data}

Você pode pré-processar a personalização da mensagem em um fluxo de trabalho dedicado. Para fazer isso, use o **[!UICONTROL Prepare the personalization data with a workflow]** opção, disponível na **[!UICONTROL Analysis]** das propriedades de delivery.

Durante a análise de delivery, essa opção cria e executa automaticamente um workflow que armazena todos os dados vinculados ao target em uma tabela temporária, incluindo dados de tabelas vinculadas em um banco de dados externo.

Essa opção melhora significativamente o desempenho ao executar a etapa de personalização.

## Usar dados de um banco de dados externo em um workflow {#using-data-from-an-external-database-in-a-workflow}

Em várias atividades de workflow do Adobe Campaign, é possível usar os dados armazenados em um banco de dados externo.

* **Filtrar dados externos** - A [Query](../../workflow/using/targeting-data.md#selecting-data) A atividade permite adicionar dados externos e usá-los nas configurações de filtro definidas. Para obter mais informações, consulte [esta página](../../workflow/using/targeting-data.md#selecting-data).

* **Criar subconjuntos** - A [Split](../../workflow/using/split.md) A atividade permite criar subconjuntos. Você pode usar dados externos para definir os critérios de filtragem a serem usados. Para obter mais informações, consulte [esta página](../../workflow/using/split.md).

* **Carregar banco de dados externo** - Você pode usar os dados externos na [Carregamento de dados](../../workflow/using/data-loading--rdbms-.md) (RDBMS). Saiba mais [nesta página](../../workflow/using/data-loading--rdbms-.md).

* **Adição de informações e links** - A [Enriquecimento](../../workflow/using/enrichment.md) A atividade permite adicionar dados à tabela de trabalho do workflow e links para uma tabela externa. Nesse contexto, ele pode usar dados de um banco de dados externo. Saiba mais [nesta página](../../workflow/using/enrichment.md).

## Limitações do FDA {#limitations}

A opção FDA é feita para manipular os dados em bancos de dados externos em modo de lote em workflows. Para evitar problemas de desempenho, não é recomendável usar o módulo FDA no contexto de operações unitárias, como: personalização, interação, mensagens em tempo real etc.

Evite o máximo possível as operações que precisam usar o banco de dados tanto do Adobe Campaign quanto externo. Para fazer isso, é possível:

* Exportar o banco de dados do Adobe Campaign para o banco de dados externo e executar as operações somente do banco de dados externo antes de importar novamente os resultados para o Adobe Campaign.

* Coletar os dados do banco de dados externo do Adobe Campaign e executar as operações no local.

Se você quiser realizar a personalização de deliveries usando dados do banco de dados externo, colete os dados para usar em um workflow para torná-lo disponível em uma tabela temporária. Em seguida, use os dados da tabela temporária para personalizar seu delivery.

A opção FDA está sujeita às limitações do sistema de banco de dados externo que você usa.
