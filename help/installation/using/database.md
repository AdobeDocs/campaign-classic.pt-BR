---
title: Banco de dados
seo-title: Banco de dados
description: Banco de dados
seo-description: null
page-status-flag: never-activated
uuid: b318365c-8846-4c1d-b5f7-ece55fb8c4af
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1dcf01af-c2f3-4975-ba05-628d52952064
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 28614a6b0c45deef17d9b3275a16e65bdff4538b

---


# Banco de dados{#database}

O servidor de banco de dados pode ser executado em qualquer sistema operacional, independentemente do sistema operacional usado pelo servidor ou servidores de aplicativos, desde que haja conectividade de rede entre eles.

O sistema operacional do servidor de banco de dados não é importante, desde que a conectividade com os diferentes componentes do Adobe Campaign esteja disponível.

Verifique também a seção de camadas [de acesso ao](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) Banco de Dados.

## Microsoft SQL Server {#microsoft-sql-server}

O cliente nativo deve ser instalado nos servidores de aplicativos do Adobe Campaign.

Você pode verificar o cliente nativo no servidor por meio do painel de configuração do driver ODBC, em **SQL Native Client** (para clientes Microsoft SQL Server 2005), ou **SQL Server Native Client 10.0** (para clientes Microsoft SQL Server 2008 e 2008 R2) ou **SQL Server Native Client 11.0** (para Clientes do Microsoft SQL Server 2012).

As seguintes DLLs de acesso devem estar presentes:

* **sqlncli.dll** para o cliente Microsoft SQL Server 2005,
* **sqlncli10.dll** para clientes Microsoft SQL Server 2008 e 2008 R2,
* **sqlncli11.dll** para o cliente Microsoft SQL Server 2012.

   As DLLs de acesso são encontradas no site da Microsoft.

>[!NOTE]
>
>O acesso ao Microsoft SQL Server de um servidor de aplicativos em execução no Linux não é suportado.

## Oracle {#oracle}

>[!NOTE]
>
>Nomes de colunas com caracteres multibytes não são suportados.

Os parâmetros **NLS_NCHAR_CHARACTERSET** e **NLS_CHARACTERSET** precisam ser configurados corretamente para que o banco de dados funcione em Unicode ou ANSI.

O Adobe Campaign usa a codificação padrão Oracle. O uso de outra codificação pode causar problemas de compatibilidade: neste caso, entre em contato com o suporte técnico.

Para saber mais sobre sua codificação, use o seguinte comando **sqlplus** :

```
SELECT * FROM nls_database_parameters ;
```

* Para uma instalação Unicode, as codificações compatíveis são:

   ```
   NLS_NCHAR_CHARACTERSET         AL16UTF16
   NLS_CHARACTERSET         AL32UTF8
   ```

* Para uma instalação ANSI (não unicode), somente a seguinte codificação é suportada:

```
  NLS_CHARACTERSET WE8MSWIN1252
```

Para fazer logon no **sqlplus**, use o perfil de usuário Oracle:

```
su - oracle 
sqlplus 
[login] [password]
```

Você também pode fazer referência ao [Oracle Client no Linux](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

Recomendamos que você instale o suporte a UTF-8 ao instalar o mecanismo de banco de dados. Dessa forma, você poderá criar bancos de dados Unicode.

**Tópico relacionado**

* [Opção desconectada nas tabelas do Adobe Campaign Classic](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)