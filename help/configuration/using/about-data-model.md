---
solution: Campaign Classic
product: campaign
title: Introdução ao modelo de dados Campaign Classic
description: Saiba como estender o modelo de dados do Campaign, editar esquemas, usar APIs e muito mais
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 7%

---


# Introdução ao modelo de dados do Campaign {#about-data-model}

O modelo de dados conceituais do banco de dados do Adobe Campaign consiste em um conjunto de tabelas incorporadas e sua interação. As principais tabelas e conceitos estão listados nesta página.

## Visão geral {#data-model-overview}

A Adobe Campaign depende de um banco de dados relacional que contém tabelas vinculadas. A estrutura básica do modelo de dados Adobe Campaign pode ser descrita da seguinte forma.

### tabela recipient {#recipient-table}

O modelo de dados depende de uma tabela principal que é, por padrão, a tabela Recipient (**NmsRecipient**). Esta tabela permite armazenar todos os perfis de marketing.

Para obter mais informações sobre a tabela de Recipient, consulte [esta seção](#default-recipient-table).

### tabela delivery {#delivery-table}

O modelo de dados também inclui uma peça dedicada a armazenar todas as atividades de marketing. Geralmente é a tabela Delivery (**NmsDelivery**). Cada registro nesta tabela representa uma ação de delivery ou um template do delivery. Ele contém todos os parâmetros necessários para executar delivery como público alvo, conteúdo etc.

### Registra tabelas {#log-tables}

Outra parte do modelo de dados permite armazenar temporariamente todos os registros associados à execução do campanha.

Logs do delivery são todas as mensagens enviadas a recipient ou dispositivos em todos os canais. A tabela Logs do delivery principal (**NmsBroadLog**) contém os logs do delivery de todos os recipient.
A tabela Logs de rastreamento principal (**NmsTrackingLog**) armazena os logs de rastreamento para todos os recipient. Os logs de rastreamento se referem a reações de recipient, como abertura de e-mail e cliques. Cada reação corresponde a um registro de acompanhamento.
Logs do delivery e logs de rastreamento são excluídos após um determinado período, que é especificado no Adobe Campaign e pode ser modificado. Portanto, é altamente recomendável exportar os registros regularmente.

### Tabelas técnicas {#technical-tables}

Finalmente, parte do modelo de dados consiste em dados técnicos usados para o processo aplicativo, incluindo operadores e direitos de usuário (**NmsGroup**), pastas (**XtkFolder**).

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

Se relevante, você pode usar a tabela de Recipient padrão com os campos predefinidos, como descrito em [esta seção](#default-recipient-table).

Se necessário, você pode estendê-lo com dois mecanismos:

* Estende uma tabela existente com novos campos. Por exemplo, você pode adicionar um novo campo &quot;Fidelidade&quot; à tabela de Recipient.
* Crie uma nova tabela, por exemplo, uma tabela &quot;Compra&quot; que lista todas as compras feitas por cada perfil do banco de dados e a vincula à tabela do Recipient.

Para obter mais informações sobre como configurar schemas de extensão para estender o modelo de dados conceituais, consulte [Sobre a edição do schema](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>A extensão do modelo de dados está reservada para usuários avançados.

## Uso de uma tabela personalizada de recipient {#custom-recipient-table}

Ao projetar seu modelo de dados da Adobe Campaign, você pode usar a [tabela de Recipient predefinida](#default-recipient-table) ou decidir criar uma tabela de [recipient personalizada](../../configuration/using/about-custom-recipient-table.md) para armazenar seus perfis de marketing.

Na verdade, se o modelo de dados não se ajustar à estrutura centrada no recipient, você pode configurar outras tabelas como o targeting dimension no Adobe Campaign. Por exemplo, isso pode ser relevante quando você precisa público alvo residências, contas (como telefones celulares) e empresas/sites, em vez de simplesmente recipient.

>[!NOTE]
>
>Nesse caso, será necessário criar um novo [target mapping](../../configuration/using/target-mapping.md).

Todos os princípios e etapas necessários ao usar uma tabela de recipient personalizada estão detalhados em [esta seção](../../configuration/using/about-custom-recipient-table.md).

Os benefícios do uso de uma tabela de Recipient personalizada são os seguintes:

* **Modelo**  de dados flexível - A tabela de Recipient pronta para uso é inútil se você não precisar da maioria dos campos da tabela do Recipient ou se o modelo de dados não for centralizado no recipient.

* **Escalabilidade**  - Grandes volumes exigem uma tabela simplificada com poucos campos para um design eficiente. A tabela de Recipient pronta para uso teria muitos campos inúteis, o que poderia afetar o desempenho e faltar eficiência.

* **Localização**  de dados - se os dados residirem em um banco de dados de marketing existente externo, pode ser necessário muito esforço para usar a tabela de Recipient predefinida. Criar um novo baseado em uma estrutura existente é mais simples.

* **Fácil migração**  - Não é necessário manutenção para verificar se todas as extensões ainda são válidas na atualização.

>[!IMPORTANT]
>
>O uso de uma tabela de recipient personalizada é reservado para usuários avançados e está sujeito a algumas limitações. Para obter mais informações, consulte [esta seção](../../configuration/using/about-custom-recipient-table.md).

## Tópicos relacionados

Saiba mais sobre o modelo de dados de Campanha nestas seções:

* **Descrição das tabelas**  principais - Para obter mais informações sobre a descrição padrão do modelo de dados de Campaign Classic, consulte  [esta seção](../../configuration/using/data-model-description.md).

* **Descrição completa de cada tabela**  - Para acessar a descrição completa de cada tabela, acesse  **[!UICONTROL Admin > Configuration > Data schemas]**, selecione um recurso da lista e clique na  **[!UICONTROL Documentation]** guia.

   ![](assets/data-model_documentation-tab.png)


* **Schemas**  de campanha - A estrutura física e lógica dos dados carregados no aplicativo é descrita em XML. Ela obedece a uma gramática específica do Adobe Campaign, chamada de schema. Para obter mais informações sobre schemas Adobe Campaign, leia [esta seção](../../configuration/using/about-schema-reference.md).

* **Práticas**  recomendadas do modelo de dados - Conheça a arquitetura do modelo de dados da Campanha e as práticas recomendadas relacionadas,  [nesta seção](../../configuration/using/data-model-best-practices.md#data-model-architecture).
