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
translation-type: tm+mt
source-git-commit: a0698ad55afb391bdc652a00b43b20df6fb9851b

---


# Sobre o Federated Data Access {#about-federated-data-access}

O Adobe Campaign oferece a opção de **Federated Data Access** (FDA) para processar as informações armazenadas em um ou mais bancos de dados externos: é possível acessar os dados externos sem alterar a estrutura dos dados do Adobe Campaign.

>[!CAUTION]
>
>O acesso a um banco de dados externo via FDA só é possível para instalações no local ou híbridas, exceto com os conectores Snowflake. Para obter mais informações, consulte esta [página](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## Princípio operacional {#operating-principle}

A opção FDA permite estender seu modelo de dados em um banco de dados de terceiros. Ele detectará automaticamente a estrutura das tabelas direcionadas e usará os dados das fontes SQL.


Para usar essa funcionalidade, é necessário:

1. Ter um banco de dados externo compatível com o módulo FDA do Adobe Campaign. A lista de sistemas de banco de dados e versões compatíveis está detalhada na [matriz de compatibilidade](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html). Os usuários também devem ter as [permissões necessárias](#remote-database-access-rights) no Adobe Campaign e no banco de dados externo.
1. [Instalar os drivers](#specific-configurations-by-database-type) que correspondem ao banco de dados no servidor do Adobe Campaign.
1. [Criar e configurar uma conta externa](#connecting-to-the-database) que permita estabelecer a conexão entre o Adobe Campaign e o banco de dados externo. Para obter mais informações sobre contas externas disponíveis, consulte esta [página](../../platform/using/external-accounts.md).
1. [Crie o esquema](#creating-the-data-schema) do banco de dados externo no Adobe Campaign. Isso permite reconhecer a estrutura de dados do banco de dados externo.
1. Eventualmente, [crie um novo target mapping](#defining-data-mapping) do schema criado anteriormente, no caso em que os recipients de seus deliveries vêm do banco de dados externo. Isso apresenta determinadas limitações, principalmente em relação à personalização de deliveries.

Depois que o esquema de dados é criado, os dados podem ser processados nos fluxos de trabalho do Adobe Campaign. Para obter mais informações, consulte [esta seção](../../workflow/using/executing-a-workflow.md#architecture).

## Práticas recomendadas {#best-practices-and-recommendations}

A opção FDA é feita para manipular os dados em bancos de dados externos em modo de lote em workflows. Usando o FDA em outro contexto, por exemplo, para operações unitárias, devem ser realizadas com precaução (personalização, interação, deliveries em tempo real e etc.).

Evite o máximo possível as operações que precisam usar o banco de dados tanto do Adobe Campaign quanto externo. Para fazer isso, é possível:

* Exportar o banco de dados do Adobe Campaign para o banco de dados externo e executar as operações somente do banco de dados externo antes de importar novamente os resultados para o Adobe Campaign.
* Coletar os dados do banco de dados externo do Adobe Campaign e executar as operações no local.

Se você quiser realizar a personalização de deliveries usando dados do banco de dados externo, colete os dados para usar em um workflow para torná-lo disponível em uma tabela temporária. Em seguida, use os dados da tabela temporária para personalizar seu delivery.

## Limitações {#limitations}

A opção FDA está sujeita à limitação do sistema de banco de dados externo que você usa.

Por motivos de desempenho, não recomendamos utilizar essa funcionalidade para realizar operações unitárias (personalização de delivery, módulo de interação, tempo real).
