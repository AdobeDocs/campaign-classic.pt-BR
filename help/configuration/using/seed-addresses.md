---
product: campaign
title: Seed addresses
description: Seed addresses
role: Developer
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Seed Address
level: Intermediate, Experienced
exl-id: a16103bf-0498-4f59-ad96-8bfdeea26577
TQID: 'https://experienceleague.adobe.com/xEP-TmMNJ0On70jE2PdjywSXeXw5oF0LVeCDiA7nKB8'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
subfeature_v2:
  - id: f852274f-9e3d-5d58-ae48-3ec2fd81baf0
    internal-label: Seed Address
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 10%
---
# Seed addresses{#seed-addresses}



Se a tabela do recipient for uma tabela personalizada, configurações adicionais serão necessárias. O esquema **[!UICONTROL nms:seedMember]** deve ser estendido. Uma guia adicional é adicionada aos seed addresses para definir os campos adequados, conforme mostrado abaixo:

![](assets/s_ncs_user_seedlist_new_tab.png)

Para obter mais informações sobre como usar seed addresses, consulte [esta seção](../../delivery/using/about-seed-addresses.md).

## Implementação {#implementation}

O esquema **nms:seedMember** e o formulário vinculado prontos para uso devem ser estendidos para configuração do cliente, para fazer referência a todos os campos necessários. A definição do schema contém comentários detalhando seu modo de configuração.

Definição do schema estendido da tabela de recipients:

```
<srcSchema label="Person" name="person" namespace="cus">
  <element autopk="true" label="Person" name="person">
      <attribute label="LastName" name="lastname" type="string"/>
      <attribute label="FirstName" name="firstname" type="string"/>
    <element label="Address" name="address">
      <attribute label="Email" name="addrEnv" type="string"/>
    </element>
    <attribute label="Code Offer" name="codeOffer" type="string"/>
  </element>
</srcSchema>
```

Siga as etapas abaixo:

1. Crie uma extensão do esquema **nms:seedMember**. Para obter mais informações, consulte [esta seção](../../configuration/using/extending-a-schema.md).
1. Nesta nova extensão, adicione um novo elemento na raiz de **[!UICONTROL seedMember]** com os seguintes parâmetros:

   ```
   name="custom_customNamespace_customSchema"
   ```

   Esse elemento deve conter os campos necessários para exportar as campanhas. Esses campos devem ter o mesmo nome que os campos correspondentes no esquema externo. Por exemplo, se o esquema for **[!UICONTROL cus:person]** , o esquema **[!UICONTROL nms:seedMember]** deverá ser estendido da seguinte maneira:

   ```
     <srcSchema extendedSchema="nms:seedMember" label="Seed addresses" labelSingular="Seed address" name="seedMember" namespace="cus">
     <element name="common">
       <element name="custom_cus_person">
         <attribute name="lastname" template="cus:person:person/@lastname"/>
         <attribute name="firstname" template="cus:person:person/@firstname"/>
         <attribute name="email" sqlname="myEmailField" template="cus:person:person/address/@addrEnv" xml="false"/>
       </element>
     </element>
     <element name="seedMember">
      <element aggregate="cus:seedMember:common"/>
     </element>
   </srcSchema>
   ```

   >[!NOTE]
   >
   >A extensão do esquema **nms:seedMember** deve estar em conformidade com as estruturas de uma campanha e uma entrega no Adobe Campaign.

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * Durante a extensão, você deve especificar um **nome SQL (@sqlname)** para o campo &#39;email&#39;. O nome SQL deve ser diferente do &#39;sEmail&#39; reservado para o esquema do recipient.
   >    * Você deve atualizar a estrutura do banco de dados com o esquema criado ao estender **nms:seedMember**.
   >    * Na extensão **nms:seedMember**, o campo contendo o endereço de email deve ter **name=&quot;email&quot;** como um atributo. O nome SQL deve ser diferente de &#39;sEmail&#39;, que já é usado para o esquema do recipient. Este atributo deve ser declarado imediatamente sob o elemento **`<element name="custom_cus_person" />`**.
   >    
   >

1. Modifique o formulário **[!UICONTROL seedMember]** de acordo para definir uma nova guia &quot;Destinatário interno&quot; na janela **[!UICONTROL Seed addresses]**. Para obter mais informações, consulte [esta página](../../configuration/using/form-structure.md).

   ```
   <container colcount="2" label="Internal recipient" name="internal"
                xpath="custom_cus_person">
       <input colspan="2" editable="true" nolabel="true" type="treeEdit">
         <container label="Recipient (cus:person)">
           <input xpath="@last name"/>
           <input xpath="@first name"/>
           <input xpath="@email"/>
         </container>
       </input>
     </container>
   ```

Se todos os atributos do seed address não forem inseridos, o Adobe Campaign substituirá automaticamente os perfis: eles serão inseridos automaticamente durante a personalização usando dados de um perfil existente.
