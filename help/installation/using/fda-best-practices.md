---
solution: Campaign Classic
product: campaign
title: Práticas recomendadas e limitações do FDA do Campaign
description: Saiba mais sobre as práticas recomendadas e limitações ao trabalhar com um banco de dados externo (FDA)
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 0a92ebd6c9400f8caf43da8f633c7755a3fb77ce
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 37%

---


# Práticas recomendadas e limitações

## Criar esquemas temporários {#create-temporary-schemas}

Você pode gerenciar vários acessos ao banco de dados externo Greenplum por meio do FDA. Uma opção dedicada permite criar um schema de trabalho diretamente ao configurar a conta externa.

![](assets/fda_work_table.png)

>[!NOTE]
>
>Essa opção só está disponível com PostgreSQL Greenplum.

## Otimizar a personalização de email com dados externos {#optimizing-email-personalization-with-external-data}

Você pode pré-processar a personalização de mensagens em um workflow dedicado. Para fazer isso, use a opção **[!UICONTROL Prepare the personalization data with a workflow]**, disponível na guia **[!UICONTROL Analysis]** das propriedades de delivery.

Durante a análise de delivery, essa opção cria e executa automaticamente um workflow que armazena todos os dados vinculados ao target em uma tabela temporária, incluindo dados de tabelas vinculadas em um banco de dados externo.

Essa opção melhora significativamente o desempenho ao executar a etapa de personalização.

## Usar dados de um banco de dados externo em um workflow {#using-data-from-an-external-database-in-a-workflow}

Em várias atividades de workflow do Adobe Campaign, você pode usar os dados armazenados em um banco de dados externo.

* **Filtrar dados externos**  - A atividade  [](../../workflow/using/targeting-data.md#selecting-data) Querypermite adicionar dados externos e usá-los nas configurações de filtro definidas. Para obter mais informações, consulte [esta página](../../workflow/using/targeting-data.md#selecting-data).

* **Criar subconjuntos**  - A  [](../../workflow/using/split.md) atividade de Splitactivity permite criar subconjuntos. Você pode usar dados externos para definir os critérios de filtragem a serem usados. Para obter mais informações, consulte [esta página](../../workflow/using/split.md).

* **Carregar banco de dados externo**  - Você pode usar os dados externos na atividade  [Data loading](../../workflow/using/data-loading--rdbms-.md)  (RDBMS) . Saiba mais [nesta página](../../workflow/using/data-loading--rdbms-.md).

* **Adição de informações e links**  - A atividade  [](../../workflow/using/enrichment.md) de Enriquecimento permite adicionar dados adicionais à tabela de trabalho do workflow e vincula a uma tabela externa. Nesse contexto, é possível usar dados de um banco de dados externo. Saiba mais [nesta página](../../workflow/using/enrichment.md).

## Limitações de FDA {#limitations}

A opção FDA é feita para manipular os dados em bancos de dados externos em modo de lote em workflows. Para evitar problemas de desempenho, não é recomendável usar o módulo FDA no contexto de operações unitárias, como: personalização, interação, mensagens em tempo real etc.

Evite o máximo possível as operações que precisam usar o banco de dados tanto do Adobe Campaign quanto externo. Para fazer isso, é possível:

* Exportar o banco de dados do Adobe Campaign para o banco de dados externo e executar as operações somente do banco de dados externo antes de importar novamente os resultados para o Adobe Campaign.

* Coletar os dados do banco de dados externo do Adobe Campaign e executar as operações no local.

Se você quiser realizar a personalização de deliveries usando dados do banco de dados externo, colete os dados para usar em um workflow para torná-lo disponível em uma tabela temporária. Em seguida, use os dados da tabela temporária para personalizar seu delivery.

A opção FDA está sujeita às limitações do sistema de banco de dados externo que você usa.

