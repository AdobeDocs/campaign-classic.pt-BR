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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Linhas de comando{#command-lines}

As seguintes linhas de comando exigem a capacidade de acessar o servidor de aplicativos. Para implantações hospedadas pela Adobe, esses comandos só podem ser executados pela Adobe.

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

O comando a seguir configura a instância de **demonstração** com o servidor tipo SQL conhecido como **base6**, vinculado à conta da **campanha** e à sua **senha** no servidor **dbsrv** :

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

