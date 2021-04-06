---
solution: Campaign Classic
product: campaign
title: Acesso a um banco de dados externo
description: Saiba como acessar e processar dados em um banco de dados externo
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
translation-type: tm+mt
source-git-commit: 37802e52f1d1d38d9c3d59c439f23114a594bfef
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 50%

---

# Introdução ao Federated Data Access {#about-federated-data-access}

O Adobe Campaign oferece a opção **Federated Data Access** (FDA) para processar informações armazenadas em um ou mais bancos de dados externos: é possível acessá-los sem alterar a estrutura dos dados do Adobe Campaign.

## Pré-requisitos {#operating-principle}

A opção FDA permite estender o template de dados em um banco de dados de terceiros. Ele detectará automaticamente a estrutura das tabelas direcionadas e usará os dados das fontes SQL.

Para usar esse recurso, os pré-requisitos estão listados abaixo:

* **Configuração**: exceto para o Snowflake, é necessário um modelo  **no** local ou de hospedagem  **** híbrida para configurar o Federated Data Access. [Saiba mais](../../installation/using/hosting-models.md)
* **Versão** do banco de dados externo: é necessário ter um banco de dados externo compatível com o módulo FDA do Adobe Campaign. A lista de sistemas de banco de dados e versões compatíveis está detalhada no Campaign [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).
* **Permissões**: Os usuários do também devem ter as permissões  [ ](../../installation/using/remote-database-access-rights.md) necessárias no Adobe Campaign e no banco de dados externo.

