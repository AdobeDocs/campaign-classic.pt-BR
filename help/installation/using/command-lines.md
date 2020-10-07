---
title: Linhas de comando
seo-title: Linhas de comando
description: Linhas de comando
seo-description: null
page-status-flag: never-activated
uuid: fa897d6a-0326-4922-8936-2471af2f213c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: 3621d4ec-8839-40c3-a574-486c408f79ba
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 5%

---


# Linhas de comando{#command-lines}

As seguintes linhas de comando exigem a capacidade de acessar o servidor de aplicativos. Para implantações hospedadas pelo Adobe, esses comandos só podem ser executados por Adobe.

## Criação de uma instância {#creating-an-instance}

A criação de instâncias pode ser executada usando linhas de comando, com a sintaxe:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(onde **eng** e **fra** são valores possíveis para o `[lang]` parâmetro)

O comando **nlserver config -addinstance:instance1/demo*/eng** permite criar uma instância chamada **instance1** em inglês com a máscara de DNS demo*.

## Declaração de uma base de dados {#declaring-a-database}

É possível associar um banco de dados existente a uma instância da linha de comando usando a seguinte sintaxe:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Os seguintes valores são possíveis para o **`[rdbms]`** parâmetro:

* **posgresql**: PostgreSQL,
* **oráculo**: Oracle,
* **mssql**: para o Microsoft SQL Server,
* **DB2**: para o motor DB2.

O comando a seguir configura a instância de **demonstração** com o servidor tipo SQL conhecido como **base6**, vinculado à conta de **campanha** e à sua **senha** no servidor **dbsrv** :

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

