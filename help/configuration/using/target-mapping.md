---
title: Mapeamento de destino
seo-title: Mapeamento de destino
description: Mapeamento de destino
seo-description: null
page-status-flag: never-activated
uuid: a7dad8eb-c191-4f10-b7d8-63e0699603b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ff7e6f72-7605-41ee-b25a-1e4618e674d7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8b3ab02d1fd90c3f14314508a8fa7d99df82436c

---


# Mapeamento de destino{#target-mapping}

A criação do mapeamento de destino é necessária em dois casos:

* se você usar uma tabela de destinatários diferente da fornecida pelo Adobe Campaign,
* se você configurar uma dimensão de filtragem diferente da dimensão de direcionamento padrão na tela de mapeamento de destino.

O assistente de criação de mapeamento de destino o ajudará a criar todos os esquemas necessários para usar sua tabela personalizada.

## Criação e configuração de esquemas vinculados à tabela personalizada {#creating-and-configuring-schemas-linked-to-the-custom-table}

Antes de criar um mapeamento de destino, várias configurações são necessárias para que o Adobe Campaign funcione com um novo esquema de dados do destinatário.

Para fazer isso, siga as etapas abaixo:

1. Crie um novo esquema de dados que integre os campos da tabela personalizada que você deseja usar.

   Para obter mais informações, consulte a referência [Esquema (xtk:srcSchema)](../../configuration/using/about-schema-reference.md).

   Em nosso exemplo, criaremos um esquema de cliente, uma tabela muito simples contendo os seguintes campos: ID, nome, sobrenome, endereço de email, número de telefone celular. O objetivo é poder enviar alertas por correio eletrônico ou SMS aos indivíduos armazenados nesta tabela.

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

1. Declare o esquema como uma exibição externa usando o atributo =&quot;true&quot;. Consulte [O atributo](../../configuration/using/schema-characteristics.md#the-view-attribute)de exibição.

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

1. Clique no **[!UICONTROL Administration > Campaign management > Target mappings]** nó.
1. Clique no botão **Novo** para abrir o assistente de criação de mapeamento de destino.
1. Informe o campo **Rótulo** e selecione o esquema que você acabou de criar no campo de dimensão **** Direcionamento.

   ![](assets/mapping_diffusion_wizard_1.png)

1. Na janela **Editar formulários** de endereço, selecione os campos do esquema que correspondem aos vários endereços de entrega. Aqui, podemos mapear os campos **@email** e **@mobile** .

   ![](assets/mapping_diffusion_wizard_2.png)

1. Na seguinte janela **Armazenamento** , digite o **Sufixo do campo de esquemas** de extensão para diferenciar os novos esquemas dos esquemas predefinidos fornecidos pelo Adobe Campaign.

   Clique **[!UICONTROL Define new additional fields]** para selecionar a dimensão que deseja direcionar na entrega.

   Por padrão, o gerenciamento de exclusão é armazenado nas mesmas tabelas que as mensagens. Marque a caixa **Gerar um esquema de armazenamento para rastreamento** se desejar configurar o armazenamento para o rastreamento vinculado ao mapeamento de destino.

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!CAUTION]
   >
   >O Adobe Campaign não oferece suporte a vários esquemas de destinatários, conhecidos como esquemas de definição de metas, vinculados aos mesmos esquemas de registro de transmissão e/ou rastreamento. Caso contrário, isso pode resultar em anomalias na reconciliação de dados posteriormente. Para obter mais informações sobre isso, consulte a página [Recomendações e limitações](../../configuration/using/about-custom-recipient-table.md) .

1. Na janela **Extensões** , selecione os esquemas opcionais que deseja gerar (a lista de esquemas disponíveis depende dos módulos instalados na plataforma Adobe Campaign).

   ![](assets/mapping_diffusion_wizard_4.png)

1. Clique no botão **Salvar** para fechar o assistente.

   O assistente usa o esquema de início para criar todos os outros esquemas necessários para que o novo mapeamento de destino funcione.

   ![](assets/mapping_schema_list.png)

## Uso do mapeamento de destino {#using-target-mapping}

Há duas maneiras de usar o novo esquema como destino de uma entrega:

* Criar um ou mais modelos de entrega com base no mapeamento
* Selecione o mapeamento diretamente durante a seleção de destino ao criar uma entrega, como mostrado abaixo:

![](assets/mapping_selection_ciblage.png)

**Tópico relacionado**

* [Responder rapidamente às solicitações do cliente para acessar seus dados](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Quicklyrespondtocustomerrequeststoaccesstheirdata)