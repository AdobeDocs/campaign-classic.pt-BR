---
product: campaign
title: Configurar a interface
description: Saiba como configurar a interface do Campaign
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 3%

---

# Configurar a interface{#configuring-the-interface}



Para exibir e dialogar com a nova tabela de recipients na interface do Adobe Campaign, siga as etapas abaixo:

* Crie um novo formulário para editar o conteúdo da nova tabela de destinatários.
* Insira um novo tipo na pasta da árvore do explorador.
* Crie uma nova aplicação web para acessar a tabela personalizada através da página inicial do Adobe Campaign.

O Adobe Campaign usa uma variável global &quot;Nms_DefaultRcpSchema&quot; para dialogar com o banco de dados do recipient padrão (nms:recipient). Portanto, essa variável precisa ser alterada.

1. Vá para a **[!UICONTROL Administration>Platform>Options]** nó do explorador.
1. Altere o valor de **Nms_DefaultRcpSchema** com o nome do schema que corresponde à tabela do recipient externo (neste caso: cus:individual).
1. Salve as alterações.

## Criação de um novo de formulário {#creating-a-new-form-}

A criação de um novo formulário permitirá que você exiba e edite os dados da tabela de destinatários externos.

>[!IMPORTANT]
>
>O nome do formulário deve ser idêntico ao nome do schema relacionado.

1. Vá para a **Administração > Configuração > Formulários de entrada** nó do explorador.
1. Criar um novo **xtk:form** type **formulário** arquivo.
1. Descreva todos os monitoramentos e campos necessários dependendo do seu modelo de tabela.

   >[!NOTE]
   >
   >Para saber mais sobre **formulário** arquivos de tipo, consulte [esta página](../../configuration/using/identifying-a-form.md).

   No nosso exemplo atual, a variável **formulário** o arquivo deve se basear no **cus:individual** esquema e, portanto, têm o seguinte layout:

   ```
   <container colspan="2">
       <input xpath="@id"/>
       <static type="separator"/>
   </container>
   <container colcount="2">
       <input xpath="@lastName"/>
       <input xpath="@firstName"/>
       <input xpath="@email"/>
       <input xpath="@mobile"/>
   </container> 
   ```

1. Salve a criação.

## Criação de um novo tipo de pasta na hierarquia de navegação {#creating-a-new-type-of-folder-in-the-navigation-hierarchy}

1. Vá para o nó **[!UICONTROL Administration>Configuration>Navigation hierarchies]**
1. Criar um novo **xtk:navtree** type **navtree** documento.
1. Descreva todos os monitoramentos e campos necessários dependendo do seu modelo de tabela.

   >[!NOTE]
   >
   >Para obter mais informações, **navtree** arquivos de tipo, consulte [esta página](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

   No exemplo atual, a variável **navtree** o arquivo deve se basear no **cus:individual** esquema e, portanto, têm o seguinte formato:

   ```
    <model name="root">
       <nodeModel img="nms:usergrp.png" label="My recipient table" name="cusindividual">
         <view name="listdet" schema="cus:individual" type="listdet">
           <columns>
             <node xpath="@id"/>
             <node xpath="@lastName"/>
             <node xpath="@firstName"/>
             <node xpath="@email"/>
             <node xpath="@mobile"/>
           </columns>
         </view>
       </nodeModel>
   </model>
   ```

1. Salve a criação.
