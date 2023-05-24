---
product: campaign
title: Esquemas de dados
description: Introdução aos esquemas de dados do Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Schema Extension
exl-id: d4446035-3988-4d89-b7df-7b8528c2e371
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 2%

---

# Esquemas de dados{#data-schemas}

## Princípios {#principles}

Para editar, criar e configurar os esquemas, clique no link **[!UICONTROL Administration > Configuration > Data schemas]** do console do cliente Adobe Campaign.

>[!NOTE]
>
>Os esquemas de dados incorporados só podem ser excluídos por um administrador do console do Adobe Campaign Classic.

![](assets/d_ncs_integration_schema_navtree.png)

O campo de edição mostra o conteúdo XML do schema de origem:

![](assets/d_ncs_integration_schema_edition.png)

>[!NOTE]
>
>O controle de edição &quot;Name&quot; permite a inserção da chave do schema formada pelo nome e pelo namespace. Os atributos &quot;name&quot; e &quot;namespace&quot; do elemento raiz do schema são atualizados automaticamente na zona de edição XML.

A visualização gera automaticamente o schema estendido:

![](assets/d_ncs_integration_schema_edition2.png)

>[!NOTE]
>
>Quando o schema de origem é salvo, a geração do schema estendido é iniciada automaticamente.

Se precisar verificar a estrutura completa de um schema, você pode usar a guia preview. Se o esquema tiver sido estendido, você poderá visualizar todas as suas extensões. Como complemento, a guia Documentação exibe todos os atributos e elementos do esquema e suas propriedades (Campo SQL, tipo/comprimento, rótulo, descrição). A guia Documentação se aplica somente a esquemas gerados. Para obter mais informações, consulte [Regeneração de schemas](../../configuration/using/regenerating-schemas.md) seção.

## Exemplo: criação de uma tabela de contratos {#example--creating-a-contract-table}

No exemplo a seguir, queremos criar uma nova tabela para **contratos** no modelo do banco de dados Adobe Campaign. Essa tabela permite armazenar nomes e sobrenomes e endereços de email de titulares e cotitulares, para cada contrato.

Para fazer isso, é necessário criar o schema da tabela e atualizar a estrutura do banco de dados para gerar a tabela correspondente. Aplique as seguintes etapas:

1. Edite o **[!UICONTROL Administration > Configuration > Data schemas]** da árvore do Adobe Campaign e clique em **[!UICONTROL New]** .
1. Escolha o **[!UICONTROL Create a new table in the data model]** e clique em **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_create_new_schema.png)

1. Especifique um nome para a tabela e um namespace.

   ![](assets/s_ncs_configuration_create_new_param.png)

   >[!NOTE]
   >
   >Por padrão, os esquemas criados pelos usuários são armazenados no namespace &#39;cus&#39;. Para obter mais informações, consulte [Identificação de um esquema](../../configuration/using/about-schema-reference.md#identification-of-a-schema).

1. Crie o conteúdo da tabela. Recomendamos o uso do assistente de entrada para garantir que nenhuma configuração esteja ausente. Para fazer isso, clique no link **[!UICONTROL Insert]** e escolha o tipo de configuração a ser adicionada.

   ![](assets/s_ncs_configuration_create_new_content.png)

1. Definir as configurações da tabela de contratos:

   ```
   <srcSchema desc="Active contracts" img="ncm:channels.png" label="Contracts" labelSingular="Contract" mappingType="sql" name="Contracts" namespace="cus" xtkschema="xtk:srcSchema">
     <element desc="Active contracts" img="ncm:channels.png" label="Contracts" labelSingular="Contract"
              name="Contracts" autopk="true">
              <attribute name="holderName" label="Holder last name" type="string"/>
              <attribute name="holderFirstName" label="Holder first name" type="string"/>
              <attribute name="holderEmail" label="Holder email" type="string"/>
              <attribute name="co-holderName" label="Co-holder last name" type="string"/>           
              <attribute name="co-holderFirstName" label="Co-holder first name" type="string"/>           
              <attribute name="co-holderEmail" label="Co-holder email" type="string"/>    
              <attribute name="date" label="Subscription date" type="date"/>     
              <attribute name="noContract" label="Contract number" type="long"/>  
     </element>
   </srcSchema>
   ```

   Adicione o tipo de contrato e coloque um índice no número do contrato.

   ```
   <srcSchema _cs="Contracts (cus)" desc="Active contracts" entitySchema="xtk:srcSchema" img="ncm:channels.png"
              label="Contracts" labelSingular="Contract" name="Contracts" namespace="cus" xtkschema="xtk:srcSchema">
     <enumeration basetype="byte" name="typeContract">
       <value label="Home" name="home" value="0"/>
       <value label="Car" name="car" value="1"/>
       <value label="Health" name="health" value="2"/>
       <value label="Pension fund" name="pension fund" value="2"/>
     </enumeration>
     <element autopk="true" desc="Active contracts" img="ncm:channels.png" label="Contracts"
              labelSingular="Contract" name="Contracts">
       <attribute label="Holder last name" name="holderName" type="string"/>
       <attribute label="Holder first name" name="holderFirstName" type="string"/>
       <attribute label="Holder email" name="holderEmail" type="string"/>
       <attribute label="Co-holder last name" name="co-holderName" type="string"/>
       <attribute label="Co-holder first name" name="co-holderFirstName" type="string"/>
       <attribute label="Co-holder email" name="co-holderEmail" type="string"/>
       <attribute label="Subscription date" name="date" type="date"/>
      <attribute desc="Type of contract" enum="cus:Contracts:typeContract" label="Type of contract"
                  name="type" type="byte"/>
       <attribute label="Contract number" name="noContract" type="long"/>
       <dbindex name="noContract" unique="true">
         <keyfield xpath="@noContract"/>
       </dbindex>
     </element>
   </srcSchema>
   ```

1. Salve o schema para gerar a estrutura:

   ![](assets/s_ncs_configuration_structure.png)

1. Atualize a estrutura do banco de dados para criar a tabela à qual o schema será vinculado. Para obter mais informações, consulte [Atualização da estrutura do banco de dados](../../configuration/using/updating-the-database-structure.md).
