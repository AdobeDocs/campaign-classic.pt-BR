---
product: campaign
title: Estender um esquema
description: Saiba como estender um esquema
role: Data Engineer, Developer
feature: Schema Extension
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 9%

---

# Estender um esquema{#extending-a-schema}

>[!IMPORTANT]
>
>Alguns esquemas internos não devem ser estendidos: principalmente aqueles para os quais as seguintes configurações são definidas:\
>**dataSource=&quot;file&quot;** e **mappingType=&quot;xmlFile&quot;**.\
>Os seguintes esquemas não devem ser estendidos: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publishing**, **nl:monitoring**, **nms:calendar**, **nms:remoteTracking**, **nms:userAgentRules**, **xtk:builder**, **xtk:connections**, **xtk:dbInit**, **xtk:funcList**, **xtk:fusion**, **xtk: jst**, **xtk:fusion árvore**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, **xtk:scriptContext**, **xtk:session**, **xtk:sqlSchema**, **xtk:sqlSchema**.
>Esta lista não é exaustiva.

Há dois métodos para estender um schema existente:

1. Modificação direta do esquema de origem.
1. Criar outro schema com o mesmo nome, mas um namespace diferente. A vantagem é que você pode estender uma tabela sem precisar modificar o esquema original.

   O elemento raiz do esquema deve conter o atributo **extendedSchema** com o nome do esquema a ser estendido como seu valor.

   Um esquema de extensão não tem seu próprio esquema: o esquema gerado pelo esquema de origem será preenchido com os campos do esquema de extensão.

   >[!IMPORTANT]
   >
   >Você não tem permissão para modificar os esquemas internos do aplicativo, mas sim o mecanismo de extensão de esquema. Caso contrário, os schemas modificados não serão considerados no momento das atualizações futuras do aplicativo. Isso pode resultar no mau funcionamento do uso do Adobe Campaign.

   **Exemplo**: extensão do esquema **nms:recipient**.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   O esquema estendido **nms:recipient** é preenchido com o campo preenchido no esquema de extensão:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   O atributo **dependsSchemas** no elemento raiz do esquema faz referência às dependências nos esquemas de extensão.

   O atributo **belongingTo** no campo preenche o esquema em que é declarado.

>[!IMPORTANT]
>
>Para que as modificações sejam consideradas, é necessário gerar os esquemas novamente. Para obter mais informações, consulte [esta página](../../configuration/using/regenerating-schemas.md).\
>Se as modificações afetarem a estrutura do banco de dados, será necessário executar uma atualização. Para obter mais informações, consulte [esta página](../../configuration/using/updating-the-database-structure.md).
