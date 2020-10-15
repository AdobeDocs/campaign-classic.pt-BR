---
title: Sobre o modelo de dados da Adobe Campaign Classic
description: Saiba como estender o modelo de dados do Campaign, editar esquemas, usar APIs e muito mais.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 8%

---


# About the Campaign data model{#about-data-model}

Esta seção descreve as noções básicas do modelo de dados da Adobe Campaign Classic, para uma melhor compreensão das tabelas integradas da Campanha e de suas interações.

O modelo de dados conceituais do banco de dados do Adobe Campaign consiste em um conjunto de tabelas incorporadas e sua interação.

Para acessar a descrição de cada tabela, vá até **[!UICONTROL Admin > Configuration > Data schemas]**, selecione um recurso da lista e clique na **[!UICONTROL Documentation]** guia.

![](assets/data-model_documentation-tab.png)

Para obter mais informações sobre a descrição padrão do modelo de dados de Campaign Classic, consulte [esta seção](../../configuration/using/data-model-description.md).

A estrutura física e lógica dos dados transportados no aplicativo é descrita em XML. Ela obedece a uma gramática específica do Adobe Campaign, chamada de schema. For more on Adobe Campaign schemas, read out [this section](../../configuration/using/about-schema-reference.md).

## Visão geral {#data-model-overview}

A Adobe Campaign depende de um banco de dados relacional que contém tabelas vinculadas. A estrutura básica do modelo de dados da Adobe Campaign pode ser descrita da seguinte maneira.

>[!NOTE]
>
>Para obter mais informações sobre a arquitetura do modelo de dados de Campanha e as práticas recomendadas relacionadas, consulte [esta seção](../../configuration/using/data-model-best-practices.md#data-model-architecture).

### tabela recipient {#recipient-table}

O modelo de dados depende de uma tabela principal que é, por padrão, a tabela Recipient (**NmsRecipient**). Esta tabela permite armazenar todos os perfis de marketing.

Para obter mais informações sobre a tabela de Recipient, consulte [esta seção](#default-recipient-table).

### tabela delivery {#delivery-table}

O modelo de dados também inclui uma peça dedicada a armazenar todas as atividades de marketing. Geralmente, é a tabela do Delivery (**NmsDelivery**). Cada registro nesta tabela representa uma ação de delivery ou um template do delivery. Ele contém todos os parâmetros necessários para executar delivery como público alvo, conteúdo etc.

### Tabelas de registros {#log-tables}

Outra parte do modelo de dados permite armazenar temporariamente todos os registros associados à execução do campanha.

Logs do delivery são todas as mensagens enviadas a recipient ou dispositivos em todos os canais. A tabela Logs do delivery principal (**NmsBroadLog**) contém os logs do delivery para todos os recipient.
A tabela Logs de rastreamento principal (**NmsTrackingLog**) armazena os logs de rastreamento para todos os recipient. Os logs de rastreamento se referem a reações de recipient, como abertura de e-mail e cliques. Cada reação corresponde a um registro de acompanhamento.
Logs do delivery e logs de rastreamento são excluídos após um determinado período, que é especificado no Adobe Campaign e pode ser modificado. Portanto, é altamente recomendável exportar os registros regularmente.

### Quadros técnicos {#technical-tables}

Por fim, parte do modelo de dados consiste em dados técnicos usados para o processo de aplicação, incluindo operadores e direitos de usuário (**NmsGroup**), pastas (**XtkFolder**).

## Uso da tabela de Recipient padrão {#default-recipient-table}

A tabela de Recipient predefinida no Adobe Campaign fornece um bom ponto de partida para a criação do modelo de dados. Ele tem vários campos predefinidos e links de tabela que podem ser facilmente estendidos. Isso é particularmente útil quando você está direcionando principalmente recipient, pois se encaixa em um modelo de dados simples centrado em recipient.

Os benefícios da utilização da tabela de Recipient padrão são os seguintes:

* Trabalhar prontamente com funcionalidades como subscrições, listas de semente, pesquisas, sociais e assim por diante.
* Fornecer um banco de dados de marketing com um modelo de dados centrado em recipient.
* Implementação mais rápida.
* Manutenção fácil por meio de suporte e parceiros.

No entanto, é possível estender a tabela do Recipient, mas não reduzir o número de campos ou links na tabela.

>[!IMPORTANT]
>
>É recomendável não excluir campos (mesmo que não sejam úteis) na tabela recipient, pois isso pode levar a erros nos módulos incorporados.

Além disso, como a tabela de Recipient é parte do produto, tanto a tabela quanto o formulário associado evoluem conforme o produto muda. Portanto, é necessária uma manutenção extra para verificar se as extensões ainda são válidas na atualização.

## Extensão do modelo de dados {#extending-data-model}

Ao começar com a Adobe Campaign, é necessário avaliar o modelo de dados padrão para verificar qual tabela é a mais adequada para armazenar seus dados de marketing.

Se relevante, você pode usar a tabela de Recipient padrão com os campos predefinidos, como descrito na [presente seção](#default-recipient-table).

Se necessário, você pode estendê-lo com dois mecanismos:

* Estende uma tabela existente com novos campos. Por exemplo, você pode adicionar um novo campo &quot;Fidelidade&quot; à tabela de Recipient.
* Crie uma nova tabela, por exemplo, uma tabela &quot;Compra&quot; que lista todas as compras feitas por cada perfil do banco de dados e a vincula à tabela do Recipient.

Para obter mais informações sobre como configurar schemas de extensão para estender o modelo de dados conceituais, consulte [Sobre a edição](../../configuration/using/about-schema-edition.md)schema.

>[!IMPORTANT]
>
>A extensão do modelo de dados está reservada para usuários avançados.

## Uso de uma tabela personalizada de recipient {#custom-recipient-table}

Ao projetar seu modelo de dados Adobe Campaign, você pode usar a tabela [de Recipient](#default-recipient-table)pronta para uso ou decidir criar uma tabela de recipient não padrão para armazenar seus perfis de marketing.

Na verdade, se o modelo de dados não se ajustar à estrutura centrada no recipient, você pode configurar outras tabelas como o targeting dimension no Adobe Campaign. Por exemplo, isso pode ser relevante quando você precisa público alvo residências, contas (como telefones celulares) e empresas/sites, em vez de simplesmente recipient.

>[!NOTE]
>
>Nesse caso, será necessário criar um novo [target mapping](../../configuration/using/target-mapping.md).

Todos os princípios e etapas necessários ao usar uma tabela de recipient personalizada são detalhados [nesta seção](../../configuration/using/about-custom-recipient-table.md).

Os benefícios do uso de uma tabela de Recipient personalizada são os seguintes:

### Modelo de dados flexível {#flexible-data-model}

A tabela de Recipient predefinida é inútil se você não precisar da maioria dos campos da tabela de Recipient ou se o modelo de dados não for centrado no recipient.

### Escalabilidade {#scalability}

Grandes volumes requerem uma tabela simplificada com poucos campos para um design eficiente. A tabela de Recipient pronta para uso teria muitos campos inúteis, o que poderia afetar o desempenho e faltar eficiência.

### Local dos dados {#data-location}

Se os dados residirem em um banco de dados de marketing existente externo, pode ser necessário muito esforço para usar a tabela de Recipient predefinida. Criar um novo baseado em uma estrutura existente é mais simples.

### Fácil migração {#easy-migration}

Nenhuma manutenção é necessária para verificar se todas as extensões ainda são válidas na atualização.

>[!IMPORTANT]
>
>O uso de uma tabela de recipient personalizada é reservado para usuários avançados e está sujeito a algumas limitações. Para obter mais informações, consulte [esta seção](../../configuration/using/about-custom-recipient-table.md).
