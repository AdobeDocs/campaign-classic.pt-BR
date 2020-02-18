---
title: Seed addresses
seo-title: Seed addresses
description: Seed addresses
seo-description: null
page-status-flag: never-activated
uuid: 0ebdeb73-be67-4c34-9f59-9fd4fb5241ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 41338d32-b95c-45ae-bee6-17b2af5bd837
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Seed addresses{#seed-addresses}

Se a tabela do destinatário for uma tabela personalizada, configurações adicionais serão necessárias. O **[!UICONTROL nms:seedMember]** esquema deve ser estendido. Uma guia adicional é adicionada aos endereços semente para definir os campos adequados, como mostrado abaixo:

![](assets/s_ncs_user_seedlist_new_tab.png)

Para obter mais informações sobre como usar endereços semente, consulte [esta seção](../../delivery/using/about-seed-addresses.md).

## Implementação {#implementation}

O esquema **nms:sementeMember** e o formulário vinculado pronto para uso devem ser estendidos para a configuração do cliente, para fazer referência a todos os campos necessários. A definição do esquema contém comentários detalhando seu modo de configuração.

Definição do esquema estendido da tabela de destinatários:

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

1. Crie uma extensão do esquema **nms:sementeMember** . For more on this, refer to [Extending a schema](../../configuration/using/extending-a-schema.md).
1. Nesta nova extensão, adicione um novo elemento na raiz de **[!UICONTROL seedMember]** com os seguintes parâmetros:

   ```
   name="custom_customNamespace_customSchema"
   ```

   Esse elemento deve conter os campos necessários para exportar as campanhas. Esses campos devem ter o mesmo nome dos campos correspondentes no esquema externo. Por exemplo, se o esquema for **[!UICONTROL cus:person]** , o **[!UICONTROL nms:seedMember]** esquema deverá ser estendido da seguinte forma:

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
   >A extensão do esquema **nms:sementeMember** deve estar em conformidade com as estruturas de uma campanha e uma entrega no Adobe Campaign.

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * Durante a extensão, você deve especificar um nome **SQL (@sqlname)** para o campo &#39;email&#39;. O nome SQL deve ser diferente do &#39;sEmail&#39; reservado para o esquema do destinatário.
   >    * Você deve atualizar a estrutura do banco de dados com o esquema criado ao estender **nms:sementeMember**.
   >    * Na extensão **nms:sementeMember** , o campo que contém o endereço de email deve ter **name=&quot;email&quot;** como um atributo. O nome SQL deve ser diferente de &#39;sEmail&#39;, que já é usado para o esquema do destinatário. Esse atributo deve ser declarado imediatamente sob o **`<element name="custom_cus_person" />`** elemento.


1. Modifique o **[!UICONTROL seedMember]** formulário de acordo para definir uma nova guia &quot;Destinatário interno&quot; na **[!UICONTROL Seed addresses]** janela. For more on this, refer to [Form structure](../../configuration/using/form-structure.md).

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

Se todos os atributos do endereço semente não forem inseridos, o Adobe Campaign substituirá automaticamente os perfis: eles serão inseridos automaticamente durante a personalização usando dados de um perfil existente.
