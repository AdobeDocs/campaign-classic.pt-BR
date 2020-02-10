---
title: Schemas de dados
seo-title: Schemas de dados
description: Schemas de dados
seo-description: null
page-status-flag: never-activated
uuid: 9f08750a-e125-4531-8c2c-1ab218190210
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: b65e8d27-f427-464e-ad42-51c0a88eee86
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Schemas de dados{#data-schemas}

## Princípios {#principles}

Para editar, criar e configurar os esquemas, clique no **[!UICONTROL Administration > Configuration > Data schemas]** nó do console do cliente Adobe Campaign.

>[!NOTE]
>
>Os esquemas de dados prontos para uso só podem ser excluídos por um administrador do console do Adobe Campaign Classic.

![](assets/d_ncs_integration_schema_navtree.png)

O campo de edição mostra o conteúdo XML do esquema de origem:

![](assets/d_ncs_integration_schema_edition.png)

>[!NOTE]
>
>O controle de edição &quot;Nome&quot; permite que você insira a chave do esquema composta pelo nome e pelo namespace. Os atributos &quot;name&quot; e &quot;namespace&quot; do elemento raiz do esquema são automaticamente atualizados na zona de edição XML do esquema.

A visualização gera automaticamente o esquema estendido:

![](assets/d_ncs_integration_schema_edition2.png)

>[!NOTE]
>
>Quando o esquema de origem é salvo, a geração do esquema estendido é iniciada automaticamente.

Se for necessário verificar a estrutura completa de um esquema, use a guia de visualização. Se o esquema tiver sido estendido, você poderá visualizar todas as suas extensões. Como complemento, a guia Documentação exibe todos os atributos e elementos do esquema e suas propriedades (Campo SQL, tipo/comprimento, rótulo, descrição). A guia Documentação se aplica somente aos esquemas gerados. For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.

## Exemplo: criar uma tabela de contrato {#example--creating-a-contract-table}

No exemplo a seguir, queremos criar uma nova tabela para **contratos** no modelo de banco de dados do banco de dados do Adobe Campaign. Esta tabela permite que você armazene o nome e o sobrenome e os endereços de email de titulares e co-detentores, para cada contrato.

Para fazer isso, é necessário criar o esquema da tabela e atualizar a estrutura do banco de dados para gerar a tabela correspondente. Aplique as seguintes etapas:

1. Edite o **[!UICONTROL Administration > Configuration > Data schemas]** nó da árvore do Adobe Campaign e clique em **[!UICONTROL New]** .
1. Escolha a **[!UICONTROL Create a new table in the data model]** opção e clique em **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_create_new_schema.png)

1. Especifique um nome para a tabela e um namespace.

   ![](assets/s_ncs_configuration_create_new_param.png)

   >[!NOTE]
   >
   >Por padrão, os esquemas criados pelos usuários são armazenados no namespace &#39;cus&#39;. Para obter mais informações, consulte [Identificação de um esquema](../../configuration/using/about-schema-reference.md#identification-of-a-schema).

1. Crie o conteúdo da tabela. Recomendamos usar o assistente de entrada para garantir que nenhuma configuração esteja ausente. Para fazer isso, clique no **[!UICONTROL Insert]** botão e escolha o tipo de configuração a ser adicionada.

   ![](assets/s_ncs_configuration_create_new_content.png)

1. Defina as configurações para a tabela do contrato:

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

   Adicione o tipo de contrato e insira um índice no número do contrato.

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

1. Salve o esquema para gerar a estrutura:

   ![](assets/s_ncs_configuration_structure.png)

1. Atualize a estrutura do banco de dados para criar a tabela à qual o esquema será vinculado. Para obter mais informações, consulte [Atualização da estrutura](../../configuration/using/updating-the-database-structure.md)do banco de dados.

