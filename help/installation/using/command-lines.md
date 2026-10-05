---
product: campaign
title: Linhas de comando
description: Linhas de comando
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
TQID: 'https://experienceleague.adobe.com/e85vFL0iZ586ICGGH1CP6fgqGU717W1aPDWqmj40-3s'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 4%
---
# Linhas de comando{#command-lines}



As linhas de comando a seguir exigem a capacidade de acessar o servidor de aplicativos. Para implantações hospedadas pelo Adobe, esses comandos só podem ser executados pelo Adobe.

## Criar uma instância {#creating-an-instance}

A criação de instâncias pode ser executada usando linhas de comando, com a sintaxe:

```sql
nlserver config -addinstance:instance/masques DNS[/lang]
```

(onde **eng** e **fra** são valores possíveis para o parâmetro `[lang]`)

O comando **nlserver config -addinstance:instance1/demo&#42;/eng** permite criar uma instância chamada **instance1** em inglês com a demonstração de máscara DNS&#42;.

## Declarar um banco de dados {#declaring-a-database}

Você pode associar um banco de dados existente a uma instância da linha de comando usando a seguinte sintaxe:

```sql
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Os seguintes valores são possíveis para o parâmetro **`[rdbms]`**:

* **postgresql**: para PostgreSQL,
* **oracle**: para Oracle,
* **mssql**: para Microsoft SQL Server,

O comando a seguir configura a instância **demo** com o servidor de tipo SQL conhecido como **base6**, vinculado à conta **campaign** e sua **senha** no servidor **dbsrv**:

```sql
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
