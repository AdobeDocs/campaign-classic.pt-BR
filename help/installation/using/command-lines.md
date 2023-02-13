---
product: campaign
title: Linhas de comando
description: Linhas de comando
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---

# Linhas de comando{#command-lines}

![](../../assets/v7-only.svg)

As linhas de comando a seguir exigem a capacidade de acessar o servidor de aplicativos. Para implantações hospedadas pelo Adobe, esses comandos só podem ser executados pelo Adobe.

## Criar uma instância {#creating-an-instance}

A criação da instância pode ser executada usando linhas de comando, com a sintaxe:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

em que **eng** e **fra** são valores possíveis para a variável `[lang]` parameter)

O comando **nlserver config -addinstance:instance1/demo&#42;/eng** permite criar uma instância chamada **instance1** em inglês com a demonstração da máscara DNS&#42;.

## Declarar um banco de dados {#declaring-a-database}

Você pode associar um banco de dados existente a uma instância da linha de comando usando a seguinte sintaxe:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Os seguintes valores são possíveis para a variável **`[rdbms]`** parâmetro:

* **postgresql**: PostgreSQL,
* **oracle**: para Oracle,
* **mssql**: para o Microsoft SQL Server,
* **DB2**: para o motor DB2.

O comando a seguir configura a variável **demonstração** instância com o servidor do tipo SQL conhecido como **base6**, vinculado ao **campanha** e sua conta **senha** no **dbsrv** servidor:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
