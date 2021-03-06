---
product: campaign
title: Práticas recomendadas e limitações do FDA do Campaign
description: Saiba mais sobre as práticas recomendadas e limitações ao trabalhar com um banco de dados externo (FDA)
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: b458ac67733a2f0e508df729add37d9a78dbcbd8
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 40%

---

# Práticas recomendadas e limitações

![](../../assets/v7-only.svg)

## Otimizar a personalização de email com dados externos {#optimizing-email-personalization-with-external-data}

Você pode pré-processar a personalização de mensagens em um workflow dedicado. Para fazer isso, use o **[!UICONTROL Prepare the personalization data with a workflow]** , disponível na **[!UICONTROL Analysis]** das propriedades de delivery.

Durante a análise de delivery, essa opção cria e executa automaticamente um workflow que armazena todos os dados vinculados ao target em uma tabela temporária, incluindo dados de tabelas vinculadas em um banco de dados externo.

Essa opção melhora significativamente o desempenho ao executar a etapa de personalização.

## Usar dados de um banco de dados externo em um workflow {#using-data-from-an-external-database-in-a-workflow}

Em várias atividades de workflow do Adobe Campaign, você pode usar os dados armazenados em um banco de dados externo.

* **Filtrar dados externos** - O [Query](../../workflow/using/targeting-data.md#selecting-data) permite adicionar dados externos e usá-los nas configurações de filtro definidas. Para obter mais informações, consulte [esta página](../../workflow/using/targeting-data.md#selecting-data).

* **Criar subconjuntos** - O [Split](../../workflow/using/split.md) permite criar subconjuntos. Você pode usar dados externos para definir os critérios de filtragem a serem usados. Para obter mais informações, consulte [esta página](../../workflow/using/split.md).

* **Carregar banco de dados externo** - Você pode usar os dados externos no [Carregamento de dados](../../workflow/using/data-loading--rdbms-.md) (RDBMS). Saiba mais [nesta página](../../workflow/using/data-loading--rdbms-.md).

* **Adição de informações e links** - O [Enriquecimento](../../workflow/using/enrichment.md) permite adicionar dados adicionais à tabela de trabalho do workflow e criar links para uma tabela externa. Nesse contexto, é possível usar dados de um banco de dados externo. Saiba mais [nesta página](../../workflow/using/enrichment.md).

## Limitações do FDA {#limitations}

A opção FDA é feita para manipular os dados em bancos de dados externos em modo de lote em workflows. Para evitar problemas de desempenho, não é recomendável usar o módulo FDA no contexto de operações unitárias, como: personalização, interação, mensagens em tempo real etc.

Evite o máximo possível as operações que precisam usar o banco de dados tanto do Adobe Campaign quanto externo. Para fazer isso, é possível:

* Exportar o banco de dados do Adobe Campaign para o banco de dados externo e executar as operações somente do banco de dados externo antes de importar novamente os resultados para o Adobe Campaign.

* Coletar os dados do banco de dados externo do Adobe Campaign e executar as operações no local.

Se você quiser realizar a personalização de deliveries usando dados do banco de dados externo, colete os dados para usar em um workflow para torná-lo disponível em uma tabela temporária. Em seguida, use os dados da tabela temporária para personalizar seu delivery.

A opção FDA está sujeita às limitações do sistema de banco de dados externo que você usa.
