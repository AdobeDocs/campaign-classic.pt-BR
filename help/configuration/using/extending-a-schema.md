---
title: Extensão de um esquema
seo-title: Extensão de um esquema
description: Extensão de um esquema
seo-description: null
page-status-flag: never-activated
uuid: 1767b9de-1d72-4ece-aeec-87f83862d81c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 1c9af980-4e6b-44dc-af61-dd284863ec7d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Extensão de um esquema{#extending-a-schema}

>[!IMPORTANT]
>
>Alguns esquemas incorporados não devem ser estendidos: principalmente aquelas para as quais são definidas as seguintes configurações:\
>**dataSource=&quot;file&quot;** e **mappingType=&quot;xmlFile&quot;**.\
>Não devem ser prolongados os seguintes regimes: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema********************************************, nncm:publishing, nl:monitor, intercalar:calendárioTrms:remoteTrms , nms:userAgentRules, xtk:builder, xtk:conexões, xtk:dbInit, xtk:funcList, xtk:fusion, xtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, ****************xtk:scriptContextContext, xtk:session, xtk:sxtk:Schema, xtk:strings.
>Esta lista não é exaustiva.

Há dois métodos para estender um esquema existente:

1. Modificando o esquema de origem diretamente.
1. Criando outro esquema com o mesmo nome, mas com um namespace diferente. A vantagem é que você pode estender uma tabela sem precisar modificar o esquema original.

   O elemento raiz do esquema deve conter o atributo **ExtendedSchema** com o nome do esquema a ser estendido como seu valor.

   Um esquema de extensão não tem seu próprio esquema: o esquema gerado do esquema de origem será preenchido com os campos do esquema de extensão.

   >[!IMPORTANT]
   >
   >Você não tem permissão para modificar os esquemas incorporados do aplicativo, mas sim o mecanismo de extensão do esquema. Caso contrário, os schemas modificados não serão considerados no momento das atualizações futuras do aplicativo. Isso pode resultar em falhas no uso do Adobe Campaign.

   **Exemplo**: extensão do esquema **nms:receipt** .

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   O esquema estendido **nms:customer** é preenchido com o campo preenchido no esquema de extensão:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   O atributo **dependendoEsquemas** no elemento raiz do esquema faz referência às dependências nos esquemas de extensão.

   O atributo **pertenceTo** no campo preenche o esquema em que é declarado.

>[!IMPORTANT]
>
>Para que as modificações sejam levadas em conta, é necessário regenerar esquemas. For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.\
>Se as modificações afetarem a estrutura do banco de dados, será necessário executar uma atualização. Para obter mais informações, consulte a seção [Atualização da estrutura](../../configuration/using/updating-the-database-structure.md) do banco de dados.

