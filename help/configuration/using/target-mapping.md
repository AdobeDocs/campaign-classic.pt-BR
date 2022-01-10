---
product: campaign
title: Target mapping
description: Saiba como criar um target mapping
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 38333669-5598-4811-a121-b677c1413f56
source-git-commit: 468a986d7cfb8a4c51229cf81b6656ca2d101f40
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 3%

---

# Target mapping{#target-mapping}

![](../../assets/common.svg)

A criação do target mapping é necessária em dois casos:

* se usar uma tabela de recipients diferente da fornecida pelo Adobe Campaign,
* se você configurar uma dimensão de filtro diferente do targeting dimension padrão na tela de target mapping.

O assistente de criação de target mapping ajudará você a criar todos os schemas necessários para usar sua tabela personalizada.

## Criação e configuração de schemas vinculados à tabela personalizada {#creating-and-configuring-schemas-linked-to-the-custom-table}

Antes de criar um target mapping, várias configurações são necessárias para que o Adobe Campaign funcione com um novo schema de dados de recipient.

Para fazer isso, siga as etapas abaixo:

1. Crie um novo schema de dados que integre os campos da tabela personalizada que deseja usar.

   Para obter mais informações, consulte [Referência de esquema (xtk:srcSchema)](../../configuration/using/about-schema-reference.md).

   Em nosso exemplo, criaremos um schema do cliente, uma tabela muito simples contendo os seguintes campos: ID, nome, sobrenome, endereço de email, número do celular. O objetivo é poder enviar alertas de email ou SMS para os indivíduos armazenados nesta tabela.

   Exemplo de schema (cus:individual)

   ```
   <srcSchema name="individual" namespace="cus" label="Individuals">
     <element name="individual">
       <key name="id" internal="true">
         <keyfield xpath="@id"/>
       </key>
       <attribute name="id" type="long" length="32"/>
       <attribute name="lastName" type="string" length="100"/>
       <attribute name="firstName" type="string" length="100"/>
       <attribute name="email" type="string" length="100"/>
       <attribute name="mobile" type="string" length="100"/>
     </element>
   </srcSchema>
   ```

1. Declare o schema como uma exibição externa usando o atributo =&quot;true&quot;. Consulte [O atributo de exibição](../../configuration/using/schema-characteristics.md#the-view-attribute).

   ```
    <srcSchema desc="External recipient table" namespace="cus" view="true"....>
      ...
    </srcSchema>
   ```

1. Se precisar adicionar um endereço de correspondência direta, use o seguinte tipo de estrutura:

   ```
   <element advanced="true" name="postalAddress" template="nms:common:postalAddress">
        <attribute expr="SubString(JuxtWords(Smart([../infos/@firstname]), Upper([../infos/@name])), 1, 80)"
                   name="line1"/>
        <attribute expr="Upper([../address/@line2])" name="line2"/>
        <attribute expr="Upper([../address/@line])" name="line3"/>
        <attribute expr="Upper([../address/@line])" name="line4"/>
        <attribute expr="Upper([../address/@line])" name="line5"/>
        <attribute expr="Upper([../address/@line])" name="line6"/>
        <attribute _operation="delete" name="line7"/>
        <attribute _operation="delete" name="addrErrorCount"/>
        <attribute _operation="delete" name="addrQuality"/>
        <attribute _operation="delete" name="addrLastCheck"/>
        <element expr="@line1+'n'+@line2+'n'+@line3+'n'+@line4+'n'+@line5+'n'+@line6"
                 name="serialized"/>
        <attribute expr="AllNonNull2([../address/@line], [../infos/@name])" name="addrDefined"/>
      </element>
   ```

1. Clique no nó **[!UICONTROL Administration > Campaign management > Target mappings]**.
1. Clique no botão **Novo** para abrir o assistente de criação de target mapping.
1. Insira o **Rótulo** e selecione o schema que acabou de criar no **Dimensão de direcionamento** campo.

   ![](assets/mapping_diffusion_wizard_1.png)

1. No **Editar formulários de endereço** selecione os campos do schema que correspondem aos vários endereços de delivery. Aqui, podemos mapear a variável **@email** e **@mobile** campos.

   ![](assets/mapping_diffusion_wizard_2.png)

1. No seguinte **Armazenamento** digite o **Sufixo dos schemas de extensão** para diferenciar os novos schemas dos esquemas prontos para uso fornecidos pelo Adobe Campaign.

   Clique em **[!UICONTROL Define new additional fields]** para selecionar a dimensão que deseja direcionar no delivery.

   Por padrão, o gerenciamento de exclusão é armazenado na mesma tabela que as mensagens.

   Verifique a **Gerar um esquema de armazenamento para rastreamento** se desejar configurar o armazenamento para o rastreamento vinculado ao target mapping.

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!IMPORTANT]
   >
   >O Adobe Campaign não oferece suporte a vários esquemas de recipient, conhecidos como esquemas de direcionamento, vinculados aos mesmos esquemas de broadlog e/ou de trackinglog. Caso contrário, isso pode levar a anomalias na reconciliação de dados posteriormente. Para obter mais informações sobre isso, consulte o [Recomendação e limitações](../../configuration/using/about-custom-recipient-table.md) página.

1. No **Extensões** selecione os schemas opcionais que deseja gerar (a lista de schemas disponíveis depende dos módulos instalados na plataforma Adobe Campaign).

   ![](assets/mapping_diffusion_wizard_4.png)

1. Clique no botão **Salvar** para fechar o assistente.

   O assistente usa o schema start para criar todos os outros schemas necessários para que o novo target mapping funcione.

   ![](assets/mapping_schema_list.png)

## Uso do target mapping {#using-target-mapping}

Há duas maneiras de usar o novo schema como target de um delivery:

* Criar um ou mais templates de delivery com base no mapeamento
* Selecione o mapeamento diretamente durante a seleção de target ao criar um delivery, conforme mostrado abaixo:

![](assets/mapping_selection_ciblage.png)

**Tópicos relacionados**

* [Responder rapidamente às solicitações do cliente para acessar seus dados](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Quicklyrespondtocustomerrequeststoaccesstheirdata)
