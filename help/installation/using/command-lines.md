---
solution: Campaign Classic
product: campaign
title: Linhas de comando
description: Linhas de comando
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: 95d0686c4ddeb4e25eb918ca92cbd6a0b1aa1f3c
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---


# Linhas de comando{#command-lines}

As linhas de comando a seguir exigem a capacidade de acessar o servidor de aplicativos. Para implantações hospedadas pelo Adobe, esses comandos só podem ser executados pelo Adobe.

## Criar uma instância {#creating-an-instance}

A criação da instância pode ser executada usando linhas de comando, com a sintaxe:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(onde **eng** e **fra** são valores possíveis para o parâmetro `[lang]`)

O comando **nlserver config -addinstance:instance1/demo*/eng** permite criar uma instância chamada **instance1** em inglês com a máscara de DNS demo*.

## Declarar um banco de dados {#declaring-a-database}

Você pode associar um banco de dados existente a uma instância da linha de comando usando a seguinte sintaxe:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Os seguintes valores são possíveis para o parâmetro **`[rdbms]`**:

* **postgresql**: PostgreSQL,
* **oracle**: para Oracle,
* **mssql**: para Microsoft SQL Server,
* **DB2**: para o motor DB2.

O comando a seguir configura a instância **demo** com o servidor tipo SQL conhecido como **base6**, vinculado à conta **campaign** e sua **senha** no servidor **dbsrv**:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

