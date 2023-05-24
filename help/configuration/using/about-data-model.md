---
product: campaign
title: Introdução ao modelo de dados do Campaign Classic
description: Saiba como estender o modelo de dados, editar esquemas, usar APIs e muito mais no Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Data Model
exl-id: 655b5928-b005-442f-b026-2f1b0c1abb99
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 6%

---

# Introdução ao modelo de dados do Campaign {#about-data-model}

O modelo de dados conceituais do banco de dados do Adobe Campaign consiste em um conjunto de tabelas incorporadas e sua interação. As principais tabelas e conceitos estão listados nesta página.

## Visão geral {#data-model-overview}

O Adobe Campaign depende de um banco de dados relacional contendo tabelas vinculadas. A estrutura básica do modelo de dados do Adobe Campaign pode ser descrita da seguinte maneira.

### Tabela de destinatários {#recipient-table}

O modelo de dados depende de uma tabela principal que é, por padrão, a tabela Recipient (**NmsRecipient**). Esta tabela permite armazenar todos os perfis de marketing.

Para obter mais informações sobre a tabela Recipient, consulte [nesta seção](#default-recipient-table).

### Tabela de entrega {#delivery-table}

O modelo de dados também inclui uma parte dedicada ao armazenamento de todas as atividades de marketing. Normalmente, é a tabela Delivery (**NmsDelivery**). Cada registro nessa tabela representa uma ação de entrega ou um modelo de entrega. Ele contém todos os parâmetros necessários para executar deliveries, como target, conteúdo etc.

### Registra tabelas {#log-tables}

Outra parte do modelo de dados permite armazenar temporariamente todos os logs associados à execução das campanhas.

Os logs do delivery são todas as mensagens enviadas aos recipients ou dispositivos em todos os canais. A tabela principal de Logs do delivery (**NmsBroadLog**) contém os logs do delivery para todos os recipients.
A tabela Principal de logs de rastreamento (**NmsTrackingLog**) armazena os logs de rastreamento de todos os recipients. Os logs de rastreamento se referem às reações dos recipients, como aberturas e cliques de email. Cada reação corresponde a um log de rastreamento.
Os logs do delivery e os logs de rastreamento são excluídos após um determinado período, que é especificado no Adobe Campaign e pode ser modificado. Portanto, é altamente recomendável exportar os logs regularmente.

### Tabelas técnicas {#technical-tables}

Por último, parte do modelo de dados consiste em dados técnicos utilizados para o processo de candidatura, incluindo operadores e direitos de utilizador (**NmsGroup**), pastas (**XtkFolder**).

## Uso da tabela de Recipient integrada {#default-recipient-table}

A tabela de Destinatários integrada no Adobe Campaign fornece um bom ponto de partida para a criação do modelo de dados. Ele tem vários campos predefinidos e links de tabela que podem ser facilmente estendidos. Isso é particularmente útil quando você está direcionando principalmente recipients, pois se encaixa em um modelo de dados simples centrado no recipient.

Os benefícios de usar a tabela Recipient integrada são os seguintes:

* Trabalhar integrado com funcionalidades como assinaturas, listas de propagação e muito mais.
* Fornecer um banco de dados de marketing com um modelo de dados centrado no recipient.
* Implementação mais rápida.
* Fácil manutenção por parte do suporte e dos parceiros.

No entanto, é possível estender a tabela Recipient, mas não reduzir o número de campos ou links na tabela.

>[!IMPORTANT]
>
>É recomendável não excluir campos (mesmo que sejam inúteis) na tabela de recipients, pois isso pode levar a erros nos módulos integrados.

Além disso, como a tabela Recipient faz parte do produto, tanto a tabela quanto seu formulário associado evoluem à medida que o produto muda. Portanto, é necessária uma manutenção extra para verificar se as extensões ainda são válidas na atualização.

## Extensão do modelo de dados  {#extending-data-model}

Ao começar com o Adobe Campaign, é necessário avaliar o modelo de dados padrão para verificar qual tabela é a mais adequada para armazenar seus dados de marketing.

Se relevante, você pode usar a tabela Recipient padrão com os campos prontos para uso, como descrito em [nesta seção](#default-recipient-table).

Se necessário, você pode estendê-lo com dois mecanismos:

* Estender uma tabela existente com novos campos. Por exemplo, é possível adicionar um novo campo &quot;Fidelidade&quot; à tabela Recipient.
* Crie uma nova tabela, por exemplo, uma tabela &quot;Purchase&quot; listando todas as compras feitas por cada perfil do banco de dados, e vincule-a à tabela Recipient.

Para obter mais informações sobre como configurar schemas de extensão para estender o modelo de dados conceituais, consulte [Sobre a edição de esquema](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>A extensão do modelo de dados é reservada para usuários avançados.

## Uso de uma tabela personalizada de recipient {#custom-recipient-table}

Ao projetar seu modelo de dados do Adobe Campaign, você pode usar o [tabela interna de recipient](#default-recipient-table)ou decida criar uma [tabela de recipient personalizada](../../configuration/using/about-custom-recipient-table.md) tabela para armazenar seus perfis de marketing.

Na verdade, se o modelo de dados não se ajustar à estrutura centrada no recipient, você poderá configurar outras tabelas como o targeting dimension no Adobe Campaign. Por exemplo, isso pode ser relevante quando você precisa direcionar famílias, contas (como telefones celulares) e empresas/sites, em vez de simplesmente recipients.

>[!NOTE]
>
>Nesse caso, será necessário criar um novo [target mapping](../../configuration/using/target-mapping.md).

Todos os princípios e etapas necessários ao usar uma tabela de recipient personalizada são detalhados em [nesta seção](../../configuration/using/about-custom-recipient-table.md).

Os benefícios de usar uma tabela de Recipient personalizada são os seguintes:

* **Modelo de dados flexível** - A tabela de recipients integrada é inútil se você não precisar da maioria dos campos da tabela Recipients ou se o modelo de dados não for centrado no recipient.

* **Escalabilidade** - Grandes volumes exigem uma tabela simplificada com poucos campos para um design eficiente. A tabela de recipients integrada teria muitos campos inúteis, o que poderia afetar o desempenho e a eficiência.

* **Local dos dados** - Se os dados residirem em um banco de dados de marketing existente externo, talvez seja necessário muito esforço para usar a tabela de recipients integrada. Criar um novo com base em uma estrutura existente é mais simples.

* **Fácil migração** - Nenhuma manutenção é necessária para verificar se todas as extensões ainda são válidas na atualização.

>[!IMPORTANT]
>
>O uso de uma tabela de recipient personalizada é reservado para usuários avançados e está sujeito a algumas limitações. Para obter mais informações, consulte [esta seção](../../configuration/using/about-custom-recipient-table.md).

## Tópicos relacionados

Saiba mais sobre o modelo de dados do Campaign nestas seções:

* **Descrição dos principais quadros** - Para obter mais informações sobre a descrição do modelo de dados Campaign Classic padrão, consulte [nesta seção](../../configuration/using/data-model-description.md).

* **Descrição completa de cada tabela** - Para acessar a descrição completa de cada tabela, vá para **[!UICONTROL Admin > Configuration > Data schemas]**, selecione um recurso na lista e clique no botão **[!UICONTROL Documentation]** guia.

   ![](assets/data-model_documentation-tab.png)


* **Esquemas de campanha** - A estrutura física e lógica dos dados transportados no aplicativo é descrita em XML. Ela obedece a uma gramática específica do Adobe Campaign, chamada de schema. Para obter mais informações sobre esquemas do Adobe Campaign, leia [nesta seção](../../configuration/using/about-schema-reference.md).

* **Práticas recomendadas do modelo de dados** - Conheça a arquitetura do modelo de dados do Campaign e as práticas recomendadas relacionadas, em [nesta seção](../../configuration/using/data-model-best-practices.md#data-model-architecture).
