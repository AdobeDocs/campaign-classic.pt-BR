---
title: Alternar para Unicode
seo-title: Alternar para Unicode
description: Alternar para Unicode
seo-description: null
page-status-flag: never-activated
uuid: 5f15b285-7377-453a-aa98-ca4cf14a4c80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: 0f5399a8-860d-4a1b-86a9-9011b973346b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 9%

---


# Alternar para Unicode{#switching-to-unicode}

Para uma instância **prod** existente em Linux/PostgreSQL, as etapas para alternar para unicode são as seguintes:

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

   Adicione o caractere **u** na frente do valor relacionado ao identificador do banco de dados (**databaseId**):

   ```
   <web>
    <redirection databaseId="u7F0000010554364C" trackingPassword="myPassword="/>
   </web>
   ```

1. Em servidores que chamam o banco de dados:

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

1. Reinicialize todos os computadores:

   ```
   /etc/init.d/apache stop
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   /etc/init.d/apache start
   ```

1. Confirme o switch. Para fazer isso, conecte-se pelo console do Adobe Campaign e:

   * verificar se os dados são apresentados corretamente, em especial os caracteres acentuados:
   * inicie um delivery e verifique se a recuperação de rastreamento funciona.

