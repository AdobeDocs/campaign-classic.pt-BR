---
product: campaign
title: Introdução ao Federated Data Access
description: Saiba como acessar e processar dados em um banco de dados externo
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 47%

---

# Introdução ao Federated Data Access {#about-federated-data-access}



O Adobe Campaign oferece a opção **Federated Data Access** (FDA) para processar informações armazenadas em um ou mais bancos de dados externos: é possível acessá-los sem alterar a estrutura dos dados do Adobe Campaign.

## Pré-requisitos {#operating-principle}

A opção FDA permite estender o template de dados em um banco de dados de terceiros. Ele detectará automaticamente a estrutura das tabelas direcionadas e usará os dados das fontes SQL.

Para usar esse recurso, os pré-requisitos estão listados abaixo:

* **Configuração**: a lista de bancos de dados externos compatíveis depende do [modelo de hospedagem](../../installation/using/hosting-models.md).
* **Versão do banco de dados externo**: é necessário ter um banco de dados externo compatível com o módulo FDA do Adobe Campaign.

   A lista de sistemas de banco de dados e versões compatíveis por modelo de hospedagem é detalhada no Campaign [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

* **Permissões**: os usuários também devem ter a [permissões necessárias](../../installation/using/remote-database-access-rights.md) no Adobe Campaign e no banco de dados externo.

