---
title: Extensão de um schema
description: Saiba como estender um schema
page-status-flag: never-activated
uuid: 1767b9de-1d72-4ece-aeec-87f83862d81c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 1c9af980-4e6b-44dc-af61-dd284863ec7d
translation-type: tm+mt
source-git-commit: 30eaabba8962c518c734cc4e9ad27065cfe9d467
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 10%

---


# Extensão de um schema{#extending-a-schema}

>[!IMPORTANT]
>
>Alguns schemas incorporados não devem ser estendidos: principalmente aquelas para as quais são definidas as seguintes configurações:\
>**dataSource=&quot;file&quot;** e **mappingType=&quot;xmlFile&quot;**.\
>Os seguintes schemas não devem ser prolongados: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, ******************************************nen:publishing, nl:monitoramento, nms:calendário, nms:remoteTracking ,nms:userAgentRules, xtk:builder:conexõesxtk:dbInit:xtk:funcListxtk:fusion, xtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, ****************xtk:scriptContextContext, xtk:session, xtkEsquemaEsquemaEsquemaEsquema, ...
>Esta lista não é exaustiva.

Existem dois métodos para estender um schema existente:

1. Modificando o schema de origem diretamente.
1. Criação de outro schema com o mesmo nome, mas com uma namespace diferente. A vantagem é que você pode estender uma tabela sem precisar modificar o schema original.

   O elemento raiz do schema deve conter o atributo **ExtendedSchema** com o nome do schema a ser estendido como seu valor.

   Um schema de extensão não tem seu próprio schema: o schema gerado do schema de origem será preenchido com os campos do schema de extensão.

   >[!IMPORTANT]
   >
   >Você não tem permissão para modificar os schemas integrados do aplicativo, mas sim o mecanismo de extensão do schema. Caso contrário, os schemas modificados não serão considerados no momento das atualizações futuras do aplicativo. Isso pode levar a falhas no uso do Adobe Campaign.

   **Exemplo**: extensão do schema **nms:recipient** .

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   O schema **nms:recipient** Extended é preenchido com o campo preenchido no schema de extensão:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   O atributo **dependendoEsquemas** no elemento raiz do schema faz referência às dependências dos schemas de extensão.

   O atributo **pertenceTo** no campo é preenchido no schema onde é declarado.

>[!IMPORTANT]
>
>Para que as modificações sejam levadas em conta, é necessário regenerar schemas. For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.\
>Se as modificações afetarem a estrutura do banco de dados, será necessário executar uma atualização. Para obter mais informações, consulte a seção [Atualização da estrutura do banco de dados](../../configuration/using/updating-the-database-structure.md).

