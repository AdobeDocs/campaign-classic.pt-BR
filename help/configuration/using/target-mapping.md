---
title: Target mapping
seo-title: Target mapping
description: Target mapping
seo-description: null
page-status-flag: never-activated
uuid: a7dad8eb-c191-4f10-b7d8-63e0699603b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ff7e6f72-7605-41ee-b25a-1e4618e674d7
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 3%

---


# Target mapping{#target-mapping}

A criação de target mapping é necessária em dois casos:

* se você usar uma tabela de recipient diferente da fornecida pela Adobe Campaign,
* se você configurar uma dimensão do filtro diferente do targeting dimension padrão na tela do target mapping.

O assistente de criação de target mapping o ajudará a criar todos os schemas necessários para usar sua tabela personalizada.

## Criação e configuração de schemas vinculados à tabela personalizada {#creating-and-configuring-schemas-linked-to-the-custom-table}

Antes de criar um target mapping, são necessárias várias configurações para que a Adobe Campaign funcione com um novo schema de dados do recipient.

Para fazer isso, siga as etapas abaixo:

1. Crie um novo schema de dados que integre os campos da tabela personalizada que você deseja usar.

   Para obter mais informações, consulte a referência ao [Schema (xtk:srcSchema)](../../configuration/using/about-schema-reference.md).

   Em nosso exemplo, criaremos um schema de cliente, uma tabela muito simples contendo os seguintes campos: ID, nome, sobrenome, endereço de email, número de telefone celular. O objetivo é poder enviar alertas por correio eletrônico ou SMS aos indivíduos armazenados nesta tabela.

   Schema de exemplo (cus:individual)

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

1. Declarar seu schema como uma visualização externa usando o atributo =&quot;true&quot;. Consulte [O atributo](../../configuration/using/schema-characteristics.md#the-view-attribute)visualização.

   ```
    <srcSchema desc="External recipient table" namespace="cus" view="true"....>
      ...
    </srcSchema>
   ```

1. Se precisar adicionar um endereço de mala direta, use o seguinte tipo de estrutura:

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
1. Digite o campo **Rótulo** e selecione o schema que você acabou de criar no campo **Targeting dimension** .

   ![](assets/mapping_diffusion_wizard_1.png)

1. Na janela **Editar formulários** de endereço, selecione os campos do schema que correspondem aos vários endereços do delivery. Aqui, podemos mapear os campos **@email** e **@mobile** .

   ![](assets/mapping_diffusion_wizard_2.png)

1. Na janela **Armazenamento** a seguir, digite o **Sufixo dos schemas de extensão** para diferenciar os novos schemas dos schemas prontos para uso fornecidos pela Adobe Campaign.

   Clique **[!UICONTROL Define new additional fields]** para selecionar a dimensão que deseja público alvo em seu delivery.

   Por padrão, o gerenciamento de exclusão é armazenado nas mesmas tabelas que as mensagens. Marque a caixa **Gerar um schema de armazenamento para rastreamento** se desejar configurar o armazenamento para o rastreamento vinculado ao target mapping.

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!IMPORTANT]
   >
   >A Adobe Campaign não suporta vários schemas de recipient, conhecidos como schemas de definição de metas, vinculados aos mesmos schemas de registro de transmissão e/ou rastreamento. Caso contrário, isso pode resultar em anomalias na reconciliação de dados posteriormente. Para obter mais informações sobre isso, consulte a página [Recomendações e limitações](../../configuration/using/about-custom-recipient-table.md) .

1. Na janela **Extensões** , selecione os schemas opcionais que deseja gerar (a lista dos schemas disponíveis depende dos módulos instalados na plataforma Adobe Campaign).

   ![](assets/mapping_diffusion_wizard_4.png)

1. Clique no botão **Salvar** para fechar o assistente.

   O assistente usa o schema do start para criar todos os outros schemas necessários para que o novo target mapping funcione.

   ![](assets/mapping_schema_list.png)

## Uso do target mapping {#using-target-mapping}

Há duas maneiras de usar o novo schema como público alvo de um delivery:

* Criar um ou mais templates do delivery com base no mapeamento
* Selecione o mapeamento diretamente durante a seleção do público alvo ao criar um delivery, como mostrado abaixo:

![](assets/mapping_selection_ciblage.png)

**Tópicos relacionados**

* [Responder rapidamente às solicitações do cliente para acessar seus dados](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Quicklyrespondtocustomerrequeststoaccesstheirdata)