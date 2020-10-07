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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 100%

---


# Sobre o Federated Data Access {#about-federated-data-access}

O Adobe Campaign oferece a opção **Federated Data Access** (FDA) para processar informações armazenadas em um ou mais bancos de dados externos: é possível acessá-los sem alterar a estrutura dos dados do Adobe Campaign.

>[!CAUTION]
>
>O acesso a um banco de dados externo via FDA só é possível para instalações no local ou híbridas, exceto com os conectores do Snowflake. Para obter mais informações, consulte esta [página](https://helpx.adobe.com/br/campaign/kb/acc-on-prem-vs-hosted.html).

## Princípio operacional {#operating-principle}

A opção FDA permite estender o template de dados em um banco de dados de terceiros. Ele detectará automaticamente a estrutura das tabelas direcionadas e usará os dados das fontes SQL.

Para usar essa funcionalidade, é necessário:

1. Ter um banco de dados externo compatível com o módulo FDA do Adobe Campaign. A lista de sistemas de banco de dados e versões compatíveis está detalhada na [matriz de compatibilidade](https://helpx.adobe.com/br/campaign/kb/compatibility-matrix.html). Os usuários também devem ter as [permissões necessárias](../../platform/using/remote-database-access-rights.md) no Adobe Campaign e no banco de dados externo.
1. [Instalar os drivers](../../platform/using/specific-configuration-database.md) que correspondem ao banco de dados no servidor do Adobe Campaign.
1. [Criar e configurar uma conta externa](../../platform/using/connecting-to-database.md) que permita estabelecer a conexão entre o Adobe Campaign e o banco de dados externo. Para obter mais informações sobre contas externas disponíveis, consulte esta [página](../../platform/using/external-accounts.md).
1. [Criar o schema](../../platform/using/creating-data-schema.md) do banco de dados externo no Adobe Campaign. Isso permite reconhecer a estrutura de dados do banco de dados externo.
1. Eventualmente, [crie um novo target mapping](../../platform/using/defining-data-mapping.md) do schema criado anteriormente, no caso em que os recipients de seus deliveries vêm do banco de dados externo. Isso apresenta determinadas limitações, principalmente em relação à personalização de deliveries.

Após a criação do schema de dados, é possível processar os dados nos workflows do Adobe Campaign. Para obter mais informações, consulte [esta seção](../../workflow/using/accessing-an-external-database--fda-.md).

## Bancos de dados externos disponíveis {#external-database}

Você pode encontrar abaixo a lista de cada banco de dados externo compatível com o módulo FDA do Adobe Campaign:

* Análise do Microsoft Azure Synapse. Para obter mais informações, consulte esta [seção](../../platform/using/specific-configuration-database.md#azure-external).
* Snowflake. Para obter mais informações, consulte esta [seção](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake).
* Hadoop. Para obter mais informações, consulte esta [seção](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3).
* Oracle. Para obter mais informações, consulte esta [seção](../../platform/using/specific-configuration-database.md#configure-access-to-oracle).
* Netezza. Para obter mais informações, consulte esta [seção](../../platform/using/specific-configuration-database.md#configure-access-to-netezza).
* Sybase IQ. Para obter mais informações, consulte esta [seção](../../platform/using/specific-configuration-database.md#configure-access-to-sybase-iq).
* Teradata. Para obter mais informações, consulte esta [seção](../../platform/using/specific-configuration-database.md#configure-access-to-teradata).
* SAP HANA. Para obter mais informações, consulte esta [seção](../../platform/using/specific-configuration-database.md).

## Práticas recomendadas {#best-practices-and-recommendations}

A opção FDA é feita para manipular os dados em bancos de dados externos em modo de lote em workflows. Usando o FDA em outro contexto, por exemplo, para operações unitárias, devem ser realizadas com precaução (personalização, interação, deliveries em tempo real e etc.).

Evite o máximo possível as operações que precisam usar o banco de dados tanto do Adobe Campaign quanto externo. Para fazer isso, é possível:

* Exportar o banco de dados do Adobe Campaign para o banco de dados externo e executar as operações somente do banco de dados externo antes de importar novamente os resultados para o Adobe Campaign.
* Coletar os dados do banco de dados externo do Adobe Campaign e executar as operações no local.

Se você quiser realizar a personalização de deliveries usando dados do banco de dados externo, colete os dados para usar em um workflow para torná-lo disponível em uma tabela temporária. Em seguida, use os dados da tabela temporária para personalizar seu delivery.

## Limitações {#limitations}

A opção FDA está sujeita à limitação do sistema de banco de dados externo que você usa.

Por motivos de desempenho, não recomendamos utilizar essa funcionalidade para realizar operações unitárias (personalização de delivery, módulo de interação, tempo real).
