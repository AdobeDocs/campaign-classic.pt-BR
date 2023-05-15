---
product: campaign
title: Estender um esquema
description: Saiba como estender um schema
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Schema Extension
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 9%

---

# Estender um esquema{#extending-a-schema}

>[!IMPORTANT]
>
>Alguns esquemas internos não devem ser estendidos: principalmente aqueles para os quais as seguintes configurações são definidas:\
>**dataSource=&quot;file&quot;** e **mappingType=&quot;xmlFile&quot;**.\
>Os seguintes esquemas não devem ser estendidos: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publicação**, **nl:monitoramento**, **nms:calendar**, **nms:remoteTracking**, **nms:userAgentRules**, **xtk:builder**, **xtk:conexões**, **xtk:dbInit**, **xtk:funcList**, **xtk:fusion**, **xtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, **xtk:scriptContext**, **xtk:session**, **xtk:sqlSchema**, **xtk:strings**.
>Esta lista não é exaustiva.

Há dois métodos para estender um schema existente:

1. Modificação direta do schema de origem.
1. Criação de outro schema com o mesmo nome, mas com um namespace diferente. A vantagem é que você pode estender uma tabela sem precisar modificar o schema original.

   O elemento raiz do schema deve conter a variável **extendedSchema** com o nome do schema a ser estendido como seu valor.

   Um schema de extensão não tem seu próprio schema: o schema gerado pelo schema de origem será preenchido com os campos do schema de extensão.

   >[!IMPORTANT]
   >
   >Você não tem permissão para modificar os schemas internos do aplicativo, mas sim o mecanismo de extensão do schema. Caso contrário, os schemas modificados não serão considerados no momento das atualizações futuras do aplicativo. Isso pode resultar em mau funcionamento durante o uso do Adobe Campaign.

   **Exemplo**: extensão do **nms:recipient** esquema.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   O **nms:recipient** o schema estendido é preenchido com o campo preenchido no schema de extensão:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   O **dependSchemas** no elemento raiz do schema faz referência às dependências dos schemas de extensão.

   O **pertenceTo** no campo preenche o schema em que é declarado.

>[!IMPORTANT]
>
>Para que as modificações sejam levadas em conta, é necessário regenerar schemas. Para obter mais informações, consulte [esta página](../../configuration/using/regenerating-schemas.md).\
>Se as modificações afetarem a estrutura do banco de dados, será necessário executar uma atualização. Para obter mais informações, consulte [esta página](../../configuration/using/updating-the-database-structure.md).
