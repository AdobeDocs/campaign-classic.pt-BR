---
product: campaign
title: Alternar para Unicode
description: Alternar para Unicode
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 7%

---

# Alternar para Unicode{#switching-to-unicode}

![](../../assets/v7-only.svg)

Para um **prod** no Linux/PostgreSQL, as etapas para alternar para unicode são as seguintes:

1. Pare os processos de gravação no banco de dados:

   ```
   su - neolane
   nlserver shutdown
   ```

1. Despeje o banco de dados:

   ```
   su - postgres
   pg_dump mydatabase > mydatabase.sql
   ```

1. Criar um banco de dados Unicode:

   ```
   createdb -E UNICODE mydatabase_unicode
   ```

1. Restaure o banco de dados:

   ```
   psql mydatabase_unicode < mydatabase.sql
   ```

1. Atualize a opção indicando que o banco de dados é Unicode:

   ```
   psql mydatabase_unicode
   update XtkOption set sStringValue = 'u'||sStringValue where sName='XtkDatabaseId' and sStringValue not like 'u%';
   ```

1. Nos servidores de rastreamento:

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Adicione o **u** na frente do valor relativo ao identificador do banco de dados (**databaseId**):

   ```
   <web>
    <redirection databaseId="u7F0000010554364C" trackingPassword="myPassword="/>
   </web>
   ```

1. Nos servidores que chamam o banco de dados:

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Modifique a referência do banco de dados:

   ```
   <dataSource name="default">
    <dbcnx encrypted="1" 
    login="<dbuser>:<base_unicode>" password="xxxx="
    provider="postgresql" server="yyyy"/>
   </dataSource>
   ```

1. Reinicialize todas as máquinas:

   ```
   /etc/init.d/apache stop
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   /etc/init.d/apache start
   ```

1. Confirme o switch. Para fazer isso, conecte-se através do console Adobe Campaign e:

   * verificar se os dados são exibidos corretamente, em especial os caracteres acentuados:
   * inicie um delivery e verifique se a recuperação de rastreamento funciona.
