---
product: campaign
title: Recomendações do banco de dados do Campaign Classic
description: Recomendações do banco de dados
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 2%

---

# Banco de dados{#database}



O servidor de banco de dados pode ser executado em qualquer sistema operacional, independentemente do sistema operacional usado pelo servidor ou servidores de aplicativos, desde que haja conectividade de rede entre eles.

O sistema operacional do servidor de banco de dados não é importante, desde que a conectividade com os diferentes componentes do Adobe Campaign esteja disponível.

Verifique também a [Camadas de acesso ao banco de dados](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) seção.

## Microsoft SQL Server {#microsoft-sql-server}

O cliente nativo deve ser instalado nos servidores de aplicativos da Adobe Campaign.

Você pode verificar o cliente nativo no servidor por meio do painel de configuração do driver ODBC, em **SQL Server Native Client 11.0**.

A seguinte DLL de acesso deve estar presente: **sqlncli11.dll**.

As DLLs de acesso são encontradas no site do Microsoft.

>[!NOTE]
>
>O acesso ao Microsoft SQL Server a partir de um servidor de aplicativos em execução no Linux não é suportado.

## Oracle {#oracle}

>[!NOTE]
>
>Nomes de colunas com caracteres multibyte não são suportados.

O **NLS_NCHAR_CHARACTERSET** e **NLS_CHARACTERSET** os parâmetros precisam ser configurados corretamente para que o banco de dados funcione em Unicode ou ANSI.

O Adobe Campaign usa a codificação padrão de Oracles. O uso de outra codificação pode gerar problemas de compatibilidade: neste caso, entre em contato com o suporte técnico.

Para saber mais sobre sua codificação, use o seguinte **sqlplus** comando:

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

Para fazer logon no **sqlplus**, use o perfil de usuário do Oracle:

```
su - oracle 
sqlplus 
[login] [password]
```

Também é possível fazer referência a [Cliente Oracle no Linux](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

Recomendamos que você instale o suporte UTF-8 ao instalar o mecanismo de banco de dados. Dessa forma, você poderá criar bancos de dados Unicode.

**Tópicos relacionados**

* [Opção desconectada nas tabelas do Adobe Campaign Classic](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
