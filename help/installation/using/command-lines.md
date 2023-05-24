---
product: campaign
title: Linhas de comando
description: Linhas de comando
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---

# Linhas de comando{#command-lines}



As linhas de comando a seguir exigem a capacidade de acessar o servidor de aplicativos. Para implantações hospedadas pelo Adobe, esses comandos só podem ser executados pelo Adobe.

## Criar uma instância {#creating-an-instance}

A criação de instâncias pode ser executada usando linhas de comando, com a sintaxe:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(onde **eng** e **fra** são valores possíveis para o `[lang]` parameter)

O comando **configuração nlserver -addinstance:instance1/demo&#42;/eng** permite criar uma instância chamada **instance1** em inglês, com a demonstração da máscara DNS&#42;.

## Declarar um banco de dados {#declaring-a-database}

Você pode associar um banco de dados existente a uma instância da linha de comando usando a seguinte sintaxe:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Os seguintes valores são possíveis para o **`[rdbms]`** parâmetro:

* **postgresql**: para PostgreSQL,
* **oracle**: para Oracle,
* **mssql**: para Microsoft SQL Server,
* **DB2**: para o mecanismo DB2.

O comando a seguir configura o **demonstração** com o servidor de tipo SQL conhecido como **base6**, vinculado à **campaign** conta e seus **senha** no **dbsrv** servidor:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
