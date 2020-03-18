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
source-git-commit: 87966db35779f0e6a4b09a1a3ba1c30d4d002518

---


# Sobre o modelo de dados da Campanha{#about-data-model}

Esta seção descreve as noções básicas do modelo de dados do Adobe Campaign Classic, para obter uma melhor compreensão das tabelas incorporadas do Campaign e de suas interações.

O modelo de dados conceituais do banco de dados do Adobe Campaign consiste em um conjunto de tabelas incorporadas e sua interação.

Para acessar a descrição de cada tabela, vá para **[!UICONTROL Admin > Configuration > Data schemas]**, selecione um recurso da lista e clique na **[!UICONTROL Documentation]** guia.

![](assets/data-model_documentation-tab.png)

Para obter mais informações sobre a descrição padrão do modelo de dados do Campaign Classic, consulte esta [seção](../../configuration/using/data-model-description.md).

A estrutura física e lógica dos dados transportados no aplicativo é descrita em XML. Ele obedece a uma gramática específica do Adobe Campaign, chamada de esquema. Para obter mais informações sobre os esquemas do Adobe Campaign, leia esta [seção](../../configuration/using/about-schema-reference.md).

## Visão geral {#data-model-overview}

O Adobe Campaign depende de um banco de dados relacional que contém tabelas vinculadas. A estrutura básica do modelo de dados do Adobe Campaign pode ser descrita da seguinte maneira.

>[!NOTE]
>
>Para obter mais informações sobre a arquitetura do modelo de dados do Campaign e as práticas recomendadas relacionadas, consulte esta [seção](../../configuration/using/data-model-best-practices.md#data-model-architecture).

### Tabela do destinatário {#recipient-table}

O modelo de dados depende de uma tabela principal que é, por padrão, a tabela Destinatário (**NmsRecipient**). Esta tabela permite armazenar todos os perfis de marketing.

Para obter mais informações sobre a tabela Destinatário, consulte esta [seção](#default-recipient-table).

### Tabela de entrega {#delivery-table}

O modelo de dados também inclui uma peça dedicada a armazenar todas as atividades de marketing. Geralmente, é a tabela Entrega (**NmsDelivery**). Cada registro nesta tabela representa uma ação de entrega ou um modelo de entrega. Ele contém todos os parâmetros necessários para executar entregas, como destino, conteúdo etc.

### Tabelas de registros {#log-tables}

Outra parte do modelo de dados permite armazenar temporariamente todos os registros associados à execução das campanhas.

Todos os registros de entrega são mensagens enviadas para destinatários ou dispositivos em todos os canais. A tabela principal de registros de entrega (**NmsBroadLog**) contém os registros de entrega para todos os destinatários.
A tabela de registros de rastreamento principal (**NmsTrackingLog**) armazena os logs de rastreamento para todos os destinatários. Os registros de rastreamento se referem a reações de destinatários, como aberturas de email e cliques. Cada reação corresponde a um registro de acompanhamento.
Os registros de entrega e de rastreamento são excluídos após um determinado período, que é especificado no Adobe Campaign e pode ser modificado. Portanto, é altamente recomendável exportar os registros regularmente.

### Quadros técnicos {#technical-tables}

Por fim, parte do modelo de dados consiste em dados técnicos usados para o processo de aplicação, incluindo operadores e direitos de usuário (**NmsGroup**), pastas (**XtkFolder**).

## Uso da tabela Destinatário padrão {#default-recipient-table}

A tabela de destinatários predefinida no Adobe Campaign fornece um bom ponto de partida para a criação do modelo de dados. Ele tem vários campos predefinidos e links de tabela que podem ser facilmente estendidos. Isso é particularmente útil quando você está direcionando principalmente os destinatários, pois se encaixa em um modelo de dados simples centrado no destinatário.

Os benefícios do uso da tabela Destinatário padrão são os seguintes:

* Trabalhar prontamente com funcionalidades como assinaturas, listas de sementes, pesquisas, sociais e assim por diante.
* Fornecer um banco de dados de marketing com um modelo de dados centrado no destinatário.
* Implementação mais rápida.
* Manutenção fácil por meio de suporte e parceiros.

No entanto, é possível estender a tabela Destinatário, mas não para reduzir o número de campos ou links na tabela.

>[!IMPORTANT]
>
>É recomendável não excluir campos (mesmo que não sejam úteis) na tabela do destinatário, pois isso pode levar a erros nos módulos incorporados.

Além disso, como a tabela Destinatário é parte do produto, tanto a tabela quanto o formulário associado evoluem conforme o produto muda. Portanto, é necessária uma manutenção extra para verificar se as extensões ainda são válidas na atualização.

## Extensão do modelo de dados {#extending-data-model}

Ao iniciar com o Adobe Campaign, é necessário avaliar o modelo de dados padrão para verificar qual tabela é a mais adequada para armazenar seus dados de marketing.

Se relevante, você pode usar a tabela Destinatário padrão com os campos predefinidos, como descrito nesta [seção](#default-recipient-table).

Se necessário, você pode estendê-lo com dois mecanismos:

* Estende uma tabela existente com novos campos. Por exemplo, você pode adicionar um novo campo &quot;Fidelidade&quot; à tabela Destinatário.
* Crie uma nova tabela, por exemplo, uma tabela &quot;Compra&quot; que lista todas as compras feitas por cada perfil do banco de dados e a vincula à tabela Destinatário.

Para obter mais informações sobre como configurar esquemas de extensão para estender o modelo de dados conceituais, consulte [Sobre a edição](../../configuration/using/about-schema-edition.md)do esquema.

>[!IMPORTANT]
>
>A extensão do modelo de dados está reservada para usuários avançados.

## Uso de uma tabela de destinatários personalizada {#custom-recipient-table}

Ao projetar o modelo de dados do Adobe Campaign, você pode usar a tabela [Destinatário](#default-recipient-table)predefinida ou decidir criar uma tabela de destinatários não padrão para armazenar seus perfis de marketing.

Na verdade, se o modelo de dados não se ajustar à estrutura centralizada no destinatário, você pode configurar outras tabelas como a dimensão de definição de metas no Adobe Campaign. Por exemplo, isso pode ser relevante quando você precisa direcionar famílias, contas (como telefones celulares) e empresas/sites, em vez de simplesmente destinatários.

>[!NOTE]
>
>Nesse caso, será necessário criar um novo mapeamento [de](../../configuration/using/target-mapping.md)destino.

Todos os princípios e etapas necessários ao usar uma tabela de destinatários personalizada são detalhados nesta [seção](../../configuration/using/about-custom-recipient-table.md).

Os benefícios do uso de uma tabela de Destinatários personalizada são os seguintes:

### Modelo de dados flexível {#flexible-data-model}

A tabela Destinatário predefinida é inútil se você não precisar da maioria dos campos da tabela Destinatário ou se o modelo de dados não for centrado no destinatário.

### Escalabilidade {#scalability}

Grandes volumes requerem uma tabela simplificada com poucos campos para um design eficiente. A tabela Destinatário predefinida teria muitos campos inúteis, o que poderia afetar o desempenho e a falta de eficiência.

### Local dos dados {#data-location}

Se os dados residirem em um banco de dados de marketing existente externo, pode ser necessário muito esforço para usar a tabela de Destinatário predefinida. Criar um novo baseado em uma estrutura existente é mais simples.

### Fácil migração {#easy-migration}

Nenhuma manutenção é necessária para verificar se todas as extensões ainda são válidas na atualização.

>[!IMPORTANT]
>
>O uso de uma tabela de destinatários personalizada é reservado para usuários avançados e está sujeito a algumas limitações. Para obter mais informações, consulte esta seção.
