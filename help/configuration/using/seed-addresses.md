---
product: campaign
title: Seed addresses
description: Seed addresses
role: Data Engineer, Developer
badge-v8: label="Também se aplica à versão v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Seed Address
exl-id: a16103bf-0498-4f59-ad96-8bfdeea26577
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 11%

---

# Seed addresses{#seed-addresses}



Se a tabela do recipient for uma tabela personalizada, configurações adicionais serão necessárias. O schema **[!UICONTROL nms:seedMember]** deve ser estendido. Uma guia adicional é adicionada aos seed addresses para definir os campos adequados, conforme mostrado abaixo:

![](assets/s_ncs_user_seedlist_new_tab.png)

Para obter mais informações sobre o uso de seed addresses, consulte [nesta seção](../../delivery/using/about-seed-addresses.md).

## Implementação {#implementation}

A variável **nms:seedMember** O schema e o formulário vinculado que vêm pronto para uso devem ser estendidos para configuração do cliente, para fazer referência a todos os campos necessários. A definição do schema contém comentários detalhando seu modo de configuração.

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

1. Crie uma extensão do **nms:seedMember** esquema. Para obter mais informações, consulte [esta seção](../../configuration/using/extending-a-schema.md).
1. Nesta nova extensão, adicione um novo elemento na raiz de **[!UICONTROL seedMember]** com os seguintes parâmetros:

   ```
   name="custom_customNamespace_customSchema"
   ```

   Esse elemento deve conter os campos necessários para exportar as campanhas. Esses campos devem ter o mesmo nome que os campos correspondentes no esquema externo. Por exemplo, se o schema for **[!UICONTROL cus:person]** , o **[!UICONTROL nms:seedMember]** O schema deve ser estendido da seguinte maneira:

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
   >A extensão do **nms:seedMember** O esquema deve estar em conformidade com as estruturas de uma campanha e um delivery no Adobe Campaign.

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * Durante a extensão, você deve especificar um **Nome SQL (@sqlname)** para o campo &quot;email&quot;. O nome SQL deve ser diferente do &#39;sEmail&#39; reservado para o esquema do recipient.
   >    * Você deve atualizar a estrutura do banco de dados com o schema criado ao estender **nms:seedMember**.
   >    * No **nms:seedMember** , o campo que contém o endereço de email deve ter **name=&quot;email&quot;** como um atributo. O nome SQL deve ser diferente de &#39;sEmail&#39;, que já é usado para o esquema do recipient. Este atributo deve ser declarado imediatamente sob o **`<element name="custom_cus_person" />`** elemento.
   >    
   >

1. Modifique o **[!UICONTROL seedMember]** formulário de acordo para definir uma nova guia &quot;Destinatário interno&quot; no **[!UICONTROL Seed addresses]** janela. Para obter mais informações, consulte [esta página](../../configuration/using/form-structure.md).

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
