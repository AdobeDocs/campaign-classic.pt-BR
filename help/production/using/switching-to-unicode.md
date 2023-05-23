---
product: campaign
title: Alternar para Unicode
description: Alternar para Unicode
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 7%

---

# Alternar para Unicode{#switching-to-unicode}



Para um existente **prod** no Linux/PostgreSQL, as etapas para alternar para unicode são as seguintes:

1. Interrompa os processos gravando no banco de dados:

   ```
   su - neolane
   nlserver shutdown
   ```

1. Despejar o banco de dados:

   ```
   su - postgres
   pg_dump mydatabase > mydatabase.sql
   ```

1. Criar um banco de dados Unicode:

   ```
   createdb -E UNICODE mydatabase_unicode
   ```

1. Restaurar o banco de dados:

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

   Adicione o **u** caractere na frente do valor relacionado ao identificador do banco de dados (**databaseId**):

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

1. Reinicializar todos os computadores:

   ```
   /etc/init.d/apache stop
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   /etc/init.d/apache start
   ```

1. Confirme o switch. Para fazer isso, conecte-se por meio do console do Adobe Campaign e:

   * verifique se os dados são exibidos corretamente, em especial os caracteres acentuados:
   * inicie um delivery e verifique se a recuperação do rastreamento funciona.
