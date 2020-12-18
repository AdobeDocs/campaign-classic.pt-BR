---
solution: Campaign Classic
product: campaign
title: Linhas de comando
description: Linhas de comando
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---


# Linhas de comando{#command-lines}

As seguintes linhas de comando exigem a capacidade de acessar o servidor de aplicativos. Para implantações hospedadas pelo Adobe, esses comandos só podem ser executados por Adobe.

## Criação de uma instância {#creating-an-instance}

A criação de instâncias pode ser executada usando linhas de comando, com a sintaxe:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(onde **eng** e **fra** são valores possíveis para o parâmetro `[lang]`)

O comando **nlserver config -addinstance:instance1/demo*/eng** permite que você crie uma instância chamada **instance1** em inglês com a máscara de DNS demo*.

## Declaração de um banco de dados {#declaring-a-database}

É possível associar um banco de dados existente a uma instância da linha de comando usando a seguinte sintaxe:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Os seguintes valores são possíveis para o parâmetro **`[rdbms]`**:

* **posgresql**: PostgreSQL,
* **oracle**: para Oracle,
* **mssql**: para o Microsoft SQL Server,
* **DB2**: para o motor DB2.

O seguinte comando configura a instância **demo** com o servidor de tipo SQL conhecido como **base6**, ligado à conta **campanha** e à respectiva **password** no servidor **dbsrv**:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

