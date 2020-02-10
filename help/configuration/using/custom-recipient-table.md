---
title: Sobre o modelo de dados do Adobe Campaign Classic
description: Este documento descreve as noções básicas do modelo de dados do Adobe Campaign Classic.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 65affa58a66090c3bffc837fdbd85aa46338bd3e

---


# Uso de uma tabela de destinatários personalizada{#custom-recipient-table}

Ao projetar o modelo de dados do Adobe Campaign, você pode usar a tabela [Destinatário](../../configuration/using/default-recipient-table.md)predefinida ou decidir criar uma tabela de destinatários não padrão para armazenar seus perfis de marketing.

Na verdade, se o modelo de dados não se ajustar à estrutura centralizada no destinatário, você pode configurar outras tabelas como a dimensão de definição de metas no Adobe Campaign. Por exemplo, isso pode ser relevante quando você precisa direcionar famílias, contas (como telefones celulares) e empresas/sites, em vez de simplesmente destinatários.

>[!NOTE]
>
>Nesse caso, será necessário criar um novo mapeamento [de](../../configuration/using/target-mapping.md)destino.

Todos os princípios e etapas necessários ao usar uma tabela de destinatários personalizada são detalhados nesta [seção](../../configuration/using/about-custom-recipient-table.md).

Os benefícios do uso de uma tabela de Destinatários personalizada são os seguintes:

## Modelo de dados flexível {#flexible-data-model}

A tabela Destinatário predefinida é inútil se você não precisar da maioria dos campos da tabela Destinatário ou se o modelo de dados não for centrado no destinatário.

## Escalabilidade {#scalability}

Grandes volumes requerem uma tabela simplificada com poucos campos para um design eficiente. A tabela Destinatário predefinida teria muitos campos inúteis, o que poderia afetar o desempenho e a falta de eficiência.

## Local dos dados {#data-location}

Se os dados residirem em um banco de dados de marketing existente externo, pode ser necessário muito esforço para usar a tabela de Destinatário predefinida. Criar um novo baseado em uma estrutura existente é mais simples.

## Fácil migração {#easy-migration}

Nenhuma manutenção é necessária para verificar se todas as extensões ainda são válidas na atualização.

>[!IMPORTANT]
>
>O uso de uma tabela de destinatários personalizada é reservado para usuários avançados e está sujeito a algumas limitações. Para obter mais informações, consulte esta seção.
