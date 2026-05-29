---
product: campaign
title: Alternar para Unicode
description: Alternar para Unicode
feature: Monitoring
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
TQID: https://experienceleague.adobe.com/aJOfEU2Pkyc2ekoYnT1duzyjn7XIU--WSHFWrJXwc-0
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 149
ht-degree: 20%

---

# Alternar para Unicode{#switching-to-unicode}



Para uma instância **prod** existente no Linux/PostgreSQL, as etapas para alternar para unicode são as seguintes:

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

   Adicione o caractere **u** na frente do valor relacionado ao identificador de banco de dados (**databaseId**):

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
