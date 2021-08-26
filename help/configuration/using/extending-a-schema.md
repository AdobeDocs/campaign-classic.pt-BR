---
product: campaign
title: Extensão de um esquema
description: Saiba como estender um schema
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 10%

---

# Extensão de um esquema{#extending-a-schema}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
>Alguns esquemas internos não devem ser estendidos: principalmente aqueles para os quais as seguintes configurações são definidas:\
>**dataSource=&quot;file&quot;** e  **mappingType=&quot;xmlFile&quot;**.\
>Os seguintes esquemas não devem ser estendidos: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publishing**, **nl:monitoring**, **nms:calendar**, **nms:remoteTracking**, **nms:userAgentRules&lt;a 19/>,** xtk:builder **,** xtk:connections **,** xtk:dbInit **,** xtk:funcList **,** xtk:fusion **,** xtk: jst **,** xtk:navtree **,** xtk:queryDef **,** xtk:resourceMenu **,** xtk:schema&lt;a3 9/>, **xtk:scriptContext**, **xtk:session**, **xtk:sqlSchema**, **xtk:strings&lt;a47/ >.******
>Esta lista não é exaustiva.

Há dois métodos para estender um schema existente:

1. Modificação direta do schema de origem.
1. Criação de outro schema com o mesmo nome, mas com um namespace diferente. A vantagem é que você pode estender uma tabela sem precisar modificar o schema original.

   O elemento raiz do schema deve conter o atributo **ExtendedSchema** com o nome do schema a ser estendido como seu valor.

   Um schema de extensão não tem seu próprio schema: o schema gerado pelo schema de origem será preenchido com os campos do schema de extensão.

   >[!IMPORTANT]
   >
   >Você não tem permissão para modificar os schemas internos do aplicativo, mas sim o mecanismo de extensão do schema. Caso contrário, os schemas modificados não serão considerados no momento das atualizações futuras do aplicativo. Isso pode resultar em mau funcionamento durante o uso do Adobe Campaign.

   **Exemplo**: extensão do  **nms:** recipient entschema.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   O schema estendido **nms:recipient** é preenchido com o campo preenchido no schema de extensão:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   O atributo **dependSchemas** no elemento raiz do esquema faz referência às dependências nos esquemas de extensão.

   O atributo **pertenceTo** no campo preenche o schema em que é declarado.

>[!IMPORTANT]
>
>Para que as modificações sejam levadas em conta, é necessário regenerar schemas. Para obter mais informações, consulte a seção [Regenerating schemas](../../configuration/using/regenerating-schemas.md) .\
>Se as modificações afetarem a estrutura do banco de dados, será necessário executar uma atualização. Para obter mais informações, consulte a seção [Atualização da estrutura do banco de dados](../../configuration/using/updating-the-database-structure.md).
