---
product: campaign
title: Perguntas comuns
description: Perguntas frequentes sobre o Adobe Campaign Classic
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 20552812-5c58-4d48-9636-d5135197685d
source-git-commit: cfba72840f7a0d335516d38be24363865d83d18d
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 100%

---

# Perguntas frequentes sobre desenvolvedores {#dev-faq}

![](../../assets/v7-only.svg)

Como solução aberta, o Adobe Campaign está pronto para a personalização e o desenvolvimento avançado de aplicativos.

## Qual é o modelo de dados do Campaign? {#what-is-the-campaign-data-model}

O modelo de dados conceituais do banco de dados do Adobe Campaign consiste em um conjunto de tabelas incorporadas e sua interação. A estrutura física e lógica dos dados transportados no aplicativo é descrita em XML. Ela obedece a uma gramática específica do Adobe Campaign, chamada de schema. Para saber mais sobre schemas do Adobe Campaign, [consulte esta seção](../../configuration/using/about-schema-edition.md).

[Clique aqui para saber mais sobre o datamodel do Campaign](https://helpx.adobe.com/br/campaign/kb/acc-datamodel.html).

As práticas recomendadas estão listadas [neste artigo](https://helpx.adobe.com/br/campaign/kb/acc-data-model-best-practices.html).

## Como trabalhar com esquemas do Campaign? {#how-to-work-with-campaign-schemas-}

No Adobe Campaign, os esquemas de dados são usados para:

* Definir como os objetos de dados no aplicativo estão vinculados às tabelas de banco de dados subjacentes.
* Definir links entre os diferentes objetos de dados no aplicativo Campaign.
* Definir e descrever os campos individuais incluídos em cada objeto.

Leia os [Primeiros passos com tabelas e esquemas](../../configuration/using/about-schema-edition.md) para entender como trabalhar com esquemas de dados, bem como estender e personalizar o Campaign para atender às suas necessidades.

## Como usar uma tabela de destinatários personalizada? {#how-to-use-a-custom-recipient-table-}

No Campaign, é possível criar e implementar uma tabela de destinatários não padrão para enviar suas mensagens.

[Clique aqui para saber mais](../../configuration/using/about-custom-recipient-table.md)

## Quais são as práticas recomendadas para definir consultas no Campaign? {#what-are-the-best-practices-to-define-queries-in-campaign-}

O editor de consulta do Adobe Campaign é uma ferramenta poderosa para explorar dados e criar segmentos.

A ferramenta de query do Adobe Campaign pode ser encontrada em vários níveis do software: para criar uma população do target, segmentação de clientes, logs de rastreamento de extração e filtragem, filtros de compilação etc.

Você pode consultar o banco de dados do Campaign usando o editor de consulta genérico. Ele é acessado no menu **Tools > Generic query editor...**. Ele permite extrair informações armazenadas em um banco de dados e organizar, agrupar, classificar etc. O usuário pode, por exemplo, recuperar destinatários que clicaram mais de &quot;n&quot; vezes no link de um boletim informativo em um determinado período. Essa ferramenta permite coletar, classificar e exibir resultados com base nas suas necessidades. Além disso, combina todas as possibilidades de query do Adobe Campaign. Ela permite, por exemplo, criar e salvar filtros de restrição. Isso significa que um filtro de usuário criado no Editor de query genérico pode ser usado na caixa Query de um workflow de direcionamento etc.

As consultas são criadas usando campos da tabela selecionada ou usando uma fórmula. Os princípios mais importantes para criar uma consulta no banco de dados do Campaign estão descritos [nesta página](../../platform/using/about-queries-in-campaign.md).

[Clique aqui](../../workflow/using/query.md) para conhecer o editor de consulta do Campaign.

## Como posso importar um pacote de dados? {#how-can-i-import-a-data-package-}

O Adobe Campaign permite exportar ou importar a configuração e os dados da plataforma por meio de um sistema de pacotes. Os pacotes de dados permitem que entidades do banco de dados do Adobe Campaign sejam exibidas por meio de arquivos no formato XML. Cada entidade contida em um pacote é representada com todos os seus dados.

O princípio de pacotes de dados é exportar uma configuração de dados e integrá-la a outro sistema do Adobe Campaign.

[Clique aqui](../../platform/using/working-with-data-packages.md) para saber como trabalhar com pacotes de dados para importar e exportar configurações do Campaign.

## Onde posso encontrar a lista de APIs do Campaign Classic? {#where-can-i-find-the-list-of-campaign-classic-apis}

Todas as APIs do Campaign, incluindo sua descrição completa, estão disponíveis nesta [documentação dedicada](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).
