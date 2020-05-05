---
title: Acesso a um banco de dados externo
seo-title: Acesso a um banco de dados externo
description: Acesso a um banco de dados externo
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: d2758b5e81d1720a4f01a610e51c4a33995d88d1

---


# Uso de dados de um banco de dados externo em um workflow {#using-data-from-an-external-database-in-a-workflow}

Em várias atividades de workflow do Adobe Campaign, você pode usar os dados armazenados em um banco de dados externo.

## Filtragem em dados externos {#filtering-on-external-data}

A atividade query permite adicionar dados externos e usá-los nas configurações de filtro definidas.

Para obter mais informações, consulte a seção [Query](../../workflow/using/targeting-data.md#selecting-data).

## Criação de subconjuntos {#creating-sub-sets}

A atividade dividida permite criar subconjuntos. Você pode usar dados externos para definir os critérios de filtragem a serem usados.

Para obter mais informações, consulte a seção [Split](../../workflow/using/split.md).

## Carregamento de banco de dados externo {#loading-external-database}

Você pode utilizar os dados externos no carregamento de dados (RDBMS). Essa atividade é apresentada na seção [Carregamento de dados](../../workflow/using/data-loading--rdbms-.md).

## Adição de informações e links {#adding-information-and-links}

A atividade de enriquecimento permite incluir dados adicionais na mesa de trabalho do workflow, como também links para uma tabela externa. Por esse motivo, é possível explorar os dados de um banco de dados externo. Essa atividade é apresentada na seção [Enriquecimento](../../workflow/using/enrichment.md) .
