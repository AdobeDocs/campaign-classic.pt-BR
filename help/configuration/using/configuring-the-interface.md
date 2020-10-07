---
title: Configuração da interface
seo-title: Configuração da interface
description: Configuração da interface
seo-description: null
page-status-flag: never-activated
uuid: 101ba02f-da43-4dcc-b9ff-6e5ca848fc5d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 8fb9ff23-17a7-4425-9195-738d6fd914dc
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 7%

---


# Configuração da interface{#configuring-the-interface}

Para visualização e diálogo com a nova tabela de recipient na interface do Adobe Campaign, aplique as seguintes etapas:

* Crie um novo formulário para editar o conteúdo da nova tabela de recipient.
* Digite um novo tipo na pasta da árvore do explorador.
* Crie um novo aplicativo da Web para acessar a tabela personalizada por meio do home page Adobe Campaign.

A Adobe Campaign usa uma variável global &quot;Nms_DefaultRcpSchema&quot; para dialogar com o banco de dados do recipient padrão (nms:recipient). Esta variável deve, por conseguinte, ser alterada.

1. Vá para o **[!UICONTROL Administration>Platform>Options]** nó do explorador.
1. Altere o valor da variável **Nms_DefaultRcpSchema** pelo nome do schema que corresponde à tabela do recipient externo (neste caso: cus:individual).
1. Salve as alterações.

## Criação de um novo de formulário{#creating-a-new-form-}

A criação de um novo formulário permitirá que você visualização e edite os dados da tabela de recipient externos.

>[!IMPORTANT]
>
>O nome do formulário deve ser idêntico ao nome do schema a que se refere.

1. Vá até o nó **Administração > Configuração > Formulários** de entrada do explorador.
1. Crie um novo arquivo **xtk:form** type **form** .
1. Descreva todos os monitoramentos e campos necessários, dependendo do modelo da tabela.

   >[!NOTE]
   >
   >Para saber mais sobre arquivos de tipo de **formulário** , consulte [esta página](../../configuration/using/identifying-a-form.md).

   Em nosso exemplo atual, o arquivo de **formulário** deve ser baseado no schema **cus:individual** e, portanto, ter o seguinte layout:

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
1. Crie um novo documento **xtk:navtree** tipo **navtree** .
1. Descreva todos os monitoramentos e campos necessários, dependendo do modelo da tabela.

   >[!NOTE]
   >
   >Para obter mais informações sobre arquivos **navtree** , consulte [esta página](../../configuration/using/about-navigation-hierarchy.md).

   No exemplo atual, o arquivo **navtree** deve ter por base o schema **cus:individual** e, portanto, ter a seguinte forma:

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

