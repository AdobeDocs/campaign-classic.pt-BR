---
solution: Campaign Classic
product: campaign
title: Acesso a um banco de dados externo
description: Saiba como acessar e processar dados em um banco de dados externo
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 41%

---


# Introdução ao Federated Data Acces {#about-federated-data-access}

O Adobe Campaign oferece a opção **Federated Data Access** (FDA) para processar informações armazenadas em um ou mais bancos de dados externos: é possível acessá-los sem alterar a estrutura dos dados do Adobe Campaign.

## Pré-requisitos {#operating-principle}

A opção FDA permite estender o template de dados em um banco de dados de terceiros. Ele detectará automaticamente a estrutura das tabelas direcionadas e usará os dados das fontes SQL.

Para usar esse recurso, os pré-requisitos estão listados abaixo:

* **Configuração**: exceto para o Snowflake, você precisa de um modelo  **no** local ou de  **** hibridação para configurar o Federated Data Acces. [Saiba mais](../../installation/using/hosting-models.md)
* **Versão** do banco de dados externo: é necessário ter um banco de dados externo compatível com o módulo Adobe Campaign FDA. A lista de sistemas de banco de dados e versões compatíveis é detalhada na Campanha [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).
* **Permissões**: os usuários também devem ter as  [permissões ](../../installation/using/remote-database-access-rights.md) necessárias no Adobe Campaign e no banco de dados externo.

## Limitações {#limitations}

A opção FDA é feita para manipular os dados em bancos de dados externos em modo de lote em workflows. Para evitar problemas de desempenho, não é recomendável usar o módulo FDA no contexto de operações unitárias, como: personalização, interação, mensagens em tempo real etc.

Evite o máximo possível as operações que precisam usar o banco de dados tanto do Adobe Campaign quanto externo. Para fazer isso, é possível:

* Exportar o banco de dados do Adobe Campaign para o banco de dados externo e executar as operações somente do banco de dados externo antes de importar novamente os resultados para o Adobe Campaign.

* Coletar os dados do banco de dados externo do Adobe Campaign e executar as operações no local.

Se você quiser realizar a personalização de deliveries usando dados do banco de dados externo, colete os dados para usar em um workflow para torná-lo disponível em uma tabela temporária. Em seguida, use os dados da tabela temporária para personalizar seu delivery.

A opção FDA está sujeita às limitações do sistema de banco de dados externo que você usa.

## Recomendações {#recommendations}

### Criar schemas temporários {#create-temporary-schemas}

Você pode gerenciar vários acessos ao banco de dados externo do Greenplum por meio de FDA. Uma opção dedicada permite que você crie um schema ativo diretamente ao configurar a conta externa.

![](assets/fda_work_table.png)

>[!NOTE]
>
>Essa opção só está disponível com o PostgreSQL Greenplum.

### Otimizar a personalização do email com dados externos {#optimizing-email-personalization-with-external-data}

Você pode pré-processar a personalização de mensagens em um fluxo de trabalho dedicado. Para fazer isso, use a opção **[!UICONTROL Prepare the personalization data with a workflow]**, disponível na guia **[!UICONTROL Analysis]** das propriedades do delivery.

Durante a análise do delivery, essa opção cria e executa automaticamente um fluxo de trabalho que armazena todos os dados vinculados ao público alvo em uma tabela temporária, incluindo dados de tabelas vinculadas em um banco de dados externo.

Essa opção melhora significativamente o desempenho ao executar a etapa de personalização.

### Usar dados de um banco de dados externo em um fluxo de trabalho {#using-data-from-an-external-database-in-a-workflow}

Em várias atividades de fluxo de trabalho da Adobe Campaign, você pode usar os dados armazenados em um banco de dados externo.

* **Filtrar em dados**  externos - A  [](../../workflow/using/targeting-data.md#selecting-data) atividade de consulta permite que você adicione dados externos e os utilize nas configurações de filtro definidas. Para obter mais informações, consulte [esta página](../../workflow/using/targeting-data.md#selecting-data).

* **Criar subconjuntos**  - A  [](../../workflow/using/split.md) Divitatividade permite criar subconjuntos. Você pode usar dados externos para definir os critérios de filtragem a serem usados. Para obter mais informações, consulte [esta página](../../workflow/using/split.md).

* **Carregar banco de dados**  externo - você pode usar os dados externos na atividade  [de carregamento](../../workflow/using/data-loading--rdbms-.md)  de dados (RDBMS). Saiba mais [nesta página](../../workflow/using/data-loading--rdbms-.md).

* **Adicionar informações e links**  - A  [](../../workflow/using/enrichment.md) Enriquecimento permite que você adicione dados adicionais à tabela de trabalho do fluxo de trabalho e links para uma tabela externa. Neste contexto, ele pode usar dados de um banco de dados externo. Saiba mais [nesta página](../../workflow/using/enrichment.md).
