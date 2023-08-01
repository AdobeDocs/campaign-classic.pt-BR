---
product: campaign
title: Target mapping
description: Saiba como criar um target mapping
feature: Application Settings
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
exl-id: 38333669-5598-4811-a121-b677c1413f56
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 3%

---

# Target mapping{#target-mapping}



A criação do target mapping é necessária em dois casos:

* se você usar uma tabela de recipients diferente da fornecida pelo Adobe Campaign,
* se você configurar uma dimensão de filtro diferente do targeting dimension padrão na tela target mapping.

O assistente de criação de target mapping ajudará você a criar todos os esquemas necessários para usar sua tabela personalizada.

## Criação e configuração de schemas vinculados à tabela personalizada {#creating-and-configuring-schemas-linked-to-the-custom-table}

Antes de criar um target mapping, várias configurações são necessárias para que o Adobe Campaign opere com um novo schema de dados de recipient.

Para fazer isso, siga as etapas abaixo:

1. Crie um novo esquema de dados que integre os campos da tabela personalizada que você deseja usar.

   Para obter mais informações, consulte [Referência de esquema (xtk:srcSchema)](../../configuration/using/about-schema-reference.md).

   Em nosso exemplo, criaremos um schema de cliente, uma tabela muito simples contendo os seguintes campos: ID, nome, sobrenome, endereço de email, número do telefone celular. O objetivo é poder enviar alertas de email ou SMS para as pessoas armazenadas nessa tabela.

   Exemplo de esquema (cus:individual)

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

1. Declare seu esquema como uma visualização externa usando o atributo =&quot;true&quot;. Consulte [O atributo de visualização](../../configuration/using/schema-characteristics.md#the-view-attribute).

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
1. Clique em **Novo** botão para abrir o assistente de criação de target mapping.
1. Insira o **Rótulo** e selecione o schema que acabou de criar na caixa **Dimensão de direcionamento** campo.

   ![](assets/mapping_diffusion_wizard_1.png)

1. No **Editar formulários de endereço** selecione os campos do schema que correspondem aos vários endereços de delivery. Aqui, podemos mapear o **@email** e **@mobile** campos.

   ![](assets/mapping_diffusion_wizard_2.png)

1. No seguinte **Armazenamento** , insira o **Sufixo dos esquemas de extensão** para diferenciar os novos esquemas dos esquemas prontos para uso fornecidos pela Adobe Campaign.

   Clique em **[!UICONTROL Define new additional fields]** para selecionar a dimensão que deseja direcionar no delivery.

   Por padrão, o gerenciamento de exclusão é armazenado na mesma tabela que as mensagens.

   Verifique a **Gerar um esquema de armazenamento para rastreamento** se desejar configurar o armazenamento para o rastreamento vinculado ao target mapping.

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!IMPORTANT]
   >
   >O Adobe Campaign não é compatível com vários esquemas de recipient, conhecidos como esquemas de direcionamento, vinculados aos mesmos esquemas de broadlog e/ou trackinglog. Caso contrário, isso pode levar a anomalias na reconciliação de dados posteriormente. Para obter mais informações, consulte [Recomendação e limitações](../../configuration/using/about-custom-recipient-table.md) página.

1. No **Extensões** selecione os esquemas opcionais que deseja gerar (a lista de esquemas disponíveis depende dos módulos instalados na plataforma Adobe Campaign).

   ![](assets/mapping_diffusion_wizard_4.png)

1. Clique em **Salvar** botão para fechar o assistente.

   O assistente usa o schema de início para criar todos os outros schemas necessários para fazer o novo target mapping funcionar.

   ![](assets/mapping_schema_list.png)

## Utilização do target mapping {#using-target-mapping}

Há duas maneiras de usar o novo schema como target de um delivery:

* Criar um ou mais modelos de entrega com base no mapeamento
* Selecione o mapeamento diretamente durante a seleção de target ao criar um delivery, conforme mostrado abaixo:

![](assets/mapping_selection_ciblage.png)
