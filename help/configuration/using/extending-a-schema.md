---
product: campaign
title: Estender um esquema
description: Saiba como estender um esquema
role: Developer
feature: Schema Extension
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
TQID: https://experienceleague.adobe.com/w-Pe9dOgxIRB0KnOggStMDqzaNkCFGsh-5sOISc-t2E
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 304
ht-degree: 10%

---

# Estender um esquema{#extending-a-schema}

>[!IMPORTANT]
>
>Alguns esquemas internos não devem ser estendidos: principalmente aqueles para os quais as seguintes configurações são definidas:\
>**dataSource=&quot;file&quot;** e **mappingType=&quot;xmlFile&quot;**.\
>Os seguintes esquemas não devem ser estendidos: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publishing**, **nl:monitoring**, **nms:calendar**, **nms:remoteTracking**, **nms:userAgentRules**, **xtk:builder**, **xtk:connections**, **xtk:dbInit**, **xtk:funcList**, **xtk:fusion**, **xtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, **xtk:scriptContext**, **xtk:session**, **xtk:sqlSchema**, **xtk:strings**.
>Esta lista não é exaustiva.

Há dois métodos para estender um schema existente:

1. Modificação direta do esquema de origem.
1. Criar outro schema com o mesmo nome, mas um namespace diferente. A vantagem é que você pode estender uma tabela sem precisar modificar o esquema original.

   O elemento raiz do esquema deve conter o atributo **extendedSchema** com o nome do esquema a ser estendido como seu valor.

   Um esquema de extensão não tem seu próprio esquema: o esquema gerado pelo esquema de origem será preenchido com os campos do esquema de extensão.

   >[!IMPORTANT]
   >
   >Você não tem permissão para modificar os esquemas internos do aplicativo, mas sim o mecanismo de extensão de esquema. Caso contrário, os esquemas modificados não serão considerados no momento das atualizações futuras do aplicativo. Isso pode resultar no mau funcionamento do uso do Adobe Campaign.

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
