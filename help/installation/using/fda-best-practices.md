---
product: campaign
title: Práticas recomendadas e limitações do FDA do Campaign
description: Saiba mais sobre as práticas recomendadas e limitações ao trabalhar com um banco de dados externo (FDA)
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: 586456f27dbc039ecb39cc8bd1f6dbdf8af823be
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 29%

---

# Práticas recomendadas e limitações



## Otimizar a personalização de email com dados externos {#optimizing-email-personalization-with-external-data}

Você pode pré-processar a personalização da mensagem em um fluxo de trabalho dedicado. Para fazer isso, use a opção **[!UICONTROL Prepare the personalization data with a workflow]**, disponível na guia **[!UICONTROL Analysis]** das propriedades de entrega.

Durante a análise de delivery, essa opção cria e executa automaticamente um workflow que armazena todos os dados vinculados ao target em uma tabela temporária, incluindo dados de tabelas vinculadas em um banco de dados externo.

Essa opção melhora significativamente o desempenho ao executar a etapa de personalização.

## Usar dados de um banco de dados externo em um workflow {#using-data-from-an-external-database-in-a-workflow}

Em várias atividades de workflow do Adobe Campaign, é possível usar os dados armazenados em um banco de dados externo.

* **Filtrar dados externos** - A atividade [Query](../../workflow/using/targeting-data.md#selecting-data) permite adicionar dados externos e usá-los nas configurações de filtro definidas. Para obter mais informações, consulte [esta página](../../workflow/using/targeting-data.md#selecting-data).

* **Criar subconjuntos** - A atividade [Split](../../workflow/using/split.md) permite criar subconjuntos. Você pode usar dados externos para definir os critérios de filtragem a serem usados. Para obter mais informações, consulte [esta página](../../workflow/using/split.md).

* **Carregar banco de dados externo** - Você pode usar os dados externos na atividade de [carregamento de dados](../../workflow/using/data-loading-rdbms.md) (RDBMS). Saiba mais [nesta página](../../workflow/using/data-loading-rdbms.md).

* **Adicionando informações e links** - A atividade [Enriquecimento](../../workflow/using/enrichment.md) permite adicionar dados à tabela de trabalho do fluxo de trabalho e links a uma tabela externa. Nesse contexto, ele pode usar dados de um banco de dados externo. Saiba mais [nesta página](../../workflow/using/enrichment.md).

## Medidas de proteção e limitações {#fda-limitations}

A opção FDA foi projetada para manipular os dados em bancos de dados externos em modo de lote em workflows. Para evitar problemas de desempenho, não é recomendável usar o módulo FDA no contexto de operações unitárias, como: personalização, interação, mensagens em tempo real etc.

Não há suporte para direcionamento de dados de um banco de dados e filtragem de resultados usando uma dimensão de filtro que pertence a outro banco de dados. Não é possível unir tabelas que estão em diferentes fontes de dados em uma consulta. Você pode superar essa limitação usando outras atividades de workflow, como Alterar dimensão.

Evite o máximo possível as operações que precisam usar o banco de dados tanto do Adobe Campaign quanto externo. A prática recomendada é:

* Exportar o banco de dados do Adobe Campaign para o banco de dados externo e executar as operações somente do banco de dados externo antes de importar novamente os resultados para o Adobe Campaign.

* Coletar os dados do banco de dados externo do Adobe Campaign e executar as operações no local.

Se você quiser realizar a personalização de entregas usando dados do banco de dados externo, colete os dados para usar em um workflow para torná-lo disponível em uma tabela temporária. Em seguida, use os dados da tabela temporária para personalizar sua entrega.

A opção FDA está sujeita às limitações do sistema de banco de dados externo que você usa.
