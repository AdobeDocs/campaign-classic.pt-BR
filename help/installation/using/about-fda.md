---
product: campaign
title: Introdução ao Federated Data Access
description: Saiba como acessar e processar dados em um banco de dados externo
feature: Installation, Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
TQID: 'https://experienceleague.adobe.com/X-VyiKlGatskoXtPoLYhb8HrAgCRLLHxTbwXDFmg8jI'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: ee3dfd63-9a21-4961-9f24-ea3385284a21
    internal-label: Federated Data Access
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 47%
---
# Introdução ao Federated Data Access {#about-federated-data-access}



O Adobe Campaign oferece a opção **Federated Data Access** (FDA) para processar informações armazenadas em um ou mais bancos de dados externos: é possível acessá-los sem alterar a estrutura dos dados do Adobe Campaign.

## Pré-requisitos {#operating-principle}

A opção FDA permite estender o template de dados em um banco de dados de terceiros. Ele detectará automaticamente a estrutura das tabelas direcionadas e usará os dados das fontes SQL.

Para usar esse recurso, os pré-requisitos estão listados abaixo:

* **Configuração**: a lista de bancos de dados externos compatíveis depende do seu [modelo de hospedagem](../../installation/using/hosting-models.md).
* **Versão do banco de dados externo**: você precisa ter um banco de dados externo compatível com o módulo FDA do Adobe Campaign.

  A lista de sistemas de banco de dados e versões compatíveis por modelo de hospedagem está detalhada na [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA) do Campaign.

* **Permissões**: os usuários também devem ter as [permissões necessárias](../../installation/using/remote-database-access-rights.md) no Adobe Campaign e no banco de dados externo.

