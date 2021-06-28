---
product: campaign
title: Introdução ao modelo de dados do Campaign Classic
description: Saiba como estender o modelo de dados do Campaign, editar esquemas, usar APIs e muito mais
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 655b5928-b005-442f-b026-2f1b0c1abb99
source-git-commit: ee3d643e4ba607b3d7ca816eabf862b867d1f3f4
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 6%

---

# Introdução ao modelo de dados do Campaign {#about-data-model}

O modelo de dados conceituais do banco de dados do Adobe Campaign consiste em um conjunto de tabelas incorporadas e sua interação. As tabelas e os conceitos principais estão listados nesta página.

## Visão geral {#data-model-overview}

O Adobe Campaign depende de um banco de dados relacional contendo tabelas vinculadas. A estrutura básica do modelo de dados Adobe Campaign pode ser descrita da seguinte maneira.

### Tabela de recipients {#recipient-table}

O modelo de dados depende de uma tabela principal que é, por padrão, a tabela Recipient (**NmsRecipient**). Essa tabela permite armazenar todos os perfis de marketing.

Para obter mais informações sobre a tabela Recipient, consulte [esta seção](#default-recipient-table).

### Tabela de delivery {#delivery-table}

O modelo de dados também inclui uma parte dedicada ao armazenamento de todas as atividades de marketing. Geralmente é a tabela Delivery (**NmsDelivery**). Cada registro nesta tabela representa uma ação de delivery ou um template de delivery. Ele contém todos os parâmetros necessários para executar deliveries, como target, conteúdo, etc.

### Tabelas de logs {#log-tables}

Outra parte do modelo de dados permite armazenar temporariamente todos os logs associados à execução das campanhas.

Todos os logs do delivery são mensagens enviadas a recipients ou dispositivos em todos os canais. A tabela principal Delivery logs (**NmsBroadLog**) contém os logs de delivery para todos os recipients.
A tabela principal Tracking logs (**NmsTrackingLog**) armazena os logs de rastreamento para todos os recipients. Os logs de rastreamento se referem a reações de recipients, como aberturas de email e cliques. Cada reação corresponde a um log de rastreamento.
Os logs de delivery e de rastreamento são excluídos após um determinado período, que é especificado no Adobe Campaign e pode ser modificado. Portanto, é altamente recomendável exportar os logs regularmente.

### Tabelas técnicas {#technical-tables}

Finalmente, parte do modelo de dados consiste em dados técnicos usados para o processo do aplicativo, incluindo operadores e direitos de usuário (**NmsGroup**), pastas (**XtkFolder**).

## Uso da tabela incorporada Recipient {#default-recipient-table}

A tabela de Recipient integrada no Adobe Campaign fornece um bom ponto de partida para a criação do modelo de dados. Ela tem vários campos predefinidos e links de tabela que podem ser facilmente estendidos. Isso é particularmente útil quando você está direcionando recipients principalmente porque se encaixa em um modelo de dados simples centrado em recipients.

Os benefícios de usar a tabela de Recipient integrada são os seguintes:

* Trabalho integrado com funcionalidades como assinaturas, listas de propagação e muito mais.
* Fornecimento de um banco de dados de marketing com um modelo de dados centrado no recipient.
* Implementação mais rápida.
* Manutenção fácil por suporte e parceiros.

No entanto, é possível estender a tabela Recipient, mas não para reduzir o número de campos ou links na tabela.

>[!IMPORTANT]
>
>É recomendável não excluir campos (mesmo que não sejam úteis) na tabela de recipients, pois isso pode levar a erros nos módulos incorporados.

Além disso, como a tabela Recipient faz parte do produto, tanto a tabela quanto seu formulário associado evoluem conforme o produto muda. Portanto, é necessária uma manutenção extra para verificar se as extensões ainda são válidas na atualização.

## Extensão do modelo de dados  {#extending-data-model}

Ao começar com o Adobe Campaign, é necessário avaliar o modelo de dados padrão para verificar qual tabela é a mais adequada para armazenar seus dados de marketing.

Se relevante, você pode usar a tabela Recipient padrão com os campos prontos para uso, como descrito em [this section](#default-recipient-table).

Se necessário, você pode estendê-lo com dois mecanismos:

* Estende uma tabela existente com novos campos. Por exemplo, você pode adicionar um novo campo &quot;Fidelidade&quot; à tabela Recipient .
* Crie uma nova tabela, por exemplo, uma tabela &quot;Purchase&quot; que lista todas as compras feitas por cada perfil do banco de dados e a vincula à tabela Recipient .

Para obter mais informações sobre como configurar schemas de extensão para estender o modelo de dados conceituais, consulte [Sobre a edição do schema](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>A extensão do modelo de dados é reservada para usuários avançados.

## Uso de uma tabela personalizada de recipient {#custom-recipient-table}

Ao projetar seu modelo de dados Adobe Campaign, você pode usar a [tabela de Recipient pronta para uso](#default-recipient-table) ou decidir criar uma tabela de [recipient personalizada](../../configuration/using/about-custom-recipient-table.md) para armazenar seus perfis de marketing.

Na verdade, se o modelo de dados não se ajustar à estrutura centrada no recipient, é possível configurar outras tabelas como o targeting dimension no Adobe Campaign. Por exemplo, isso pode ser relevante quando você precisa direcionar as famílias, as contas (como telefones celulares) e as empresas/sites, em vez de simplesmente os recipients.

>[!NOTE]
>
>Nesse caso, será necessário criar um novo [target mapping](../../configuration/using/target-mapping.md).

Todos os princípios e etapas necessários ao usar uma tabela de recipient personalizada são detalhados em [this section](../../configuration/using/about-custom-recipient-table.md).

Os benefícios de usar uma tabela de Recipient personalizada são os seguintes:

* **Modelo de dados flexível**  - A tabela de Recipient pronta para uso é inútil se você não precisar da maioria dos campos da tabela Recipient ou se o modelo de dados não for centrado no recipient.

* **Escalabilidade**  - Grandes volumes exigem uma tabela simplificada com poucos campos para um design eficiente. A tabela de Recipient pronta para uso teria muitos campos inúteis, o que poderia afetar o desempenho e faltar eficiência.

* **Local dos dados**  - se os dados residirem em um banco de dados de marketing existente externo, pode ser necessário muito esforço para usar a tabela Recipient pronta para uso. Criar um novo com base em uma estrutura existente é mais simples.

* **Fácil migração**  - Nenhuma manutenção é necessária para verificar se todas as extensões ainda são válidas na atualização.

>[!IMPORTANT]
>
>O uso de uma tabela de recipient personalizada é reservado para usuários avançados e está sujeito a algumas limitações. Para obter mais informações, consulte [esta seção](../../configuration/using/about-custom-recipient-table.md).

## Tópicos relacionados

Saiba mais sobre o modelo de dados do Campaign nestas seções:

* **Descrição das tabelas principais**  - Para obter mais informações sobre a descrição padrão do modelo de dados do Campaign Classic, consulte  [esta seção](../../configuration/using/data-model-description.md).

* **Descrição completa de cada tabela**  - Para acessar a descrição completa de cada tabela, acesse  **[!UICONTROL Admin > Configuration > Data schemas]**, selecione um recurso na lista e clique na  **[!UICONTROL Documentation]** guia .

   ![](assets/data-model_documentation-tab.png)


* **Esquemas de campanha**  - A estrutura física e lógica dos dados transportados no aplicativo é descrita em XML. Ela obedece a uma gramática específica do Adobe Campaign, chamada de schema. Para obter mais informações sobre schemas Adobe Campaign, leia [esta seção](../../configuration/using/about-schema-reference.md).

* **Práticas recomendadas do modelo de dados**  - Conheça a arquitetura do modelo de dados do Campaign e as práticas recomendadas relacionadas,  [nesta seção](../../configuration/using/data-model-best-practices.md#data-model-architecture).
