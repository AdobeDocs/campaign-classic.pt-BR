---
product: campaign
title: Configurar a interface
description: Saiba como configurar a interface do Campaign
feature: Application Settings
role: Developer
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 5%

---

# Configurar a interface{#configuring-the-interface}

Para exibir e dialogar com a nova tabela de recipients na interface do Adobe Campaign, siga as etapas abaixo:

* Crie um novo formulário para editar o conteúdo da nova tabela de destinatários.
* Insira um novo tipo na pasta da árvore do explorador.
* Crie uma nova aplicação web para acessar a tabela personalizada através da página inicial do Adobe Campaign.

O Adobe Campaign usa uma variável global &quot;Nms_DefaultRcpSchema&quot; para diálogo com o banco de dados de recipient padrão (nms:recipient). Portanto, essa variável precisa ser alterada.

1. Vá para o nó **[!UICONTROL Administration>Platform>Options]** do explorador.
1. Altere o valor da variável **Nms_DefaultRcpSchema** com o nome do esquema que corresponde à tabela de destinatários externos (neste caso: cus:individual).
1. Salve as alterações.

## Criação de um novo formulário {#creating-a-new-form-}

A criação de um novo formulário permitirá que você exiba e edite os dados da tabela de destinatários externos.

>[!IMPORTANT]
>
>O nome do formulário deve ser idêntico ao nome do schema relacionado.

1. Vá para o nó **Administration > Configuration > Input forms** do explorador.
1. Crie um novo arquivo **xtk:form** tipo **formulário**.
1. Descreva todos os monitoramentos e campos necessários dependendo do seu modelo de tabela.

   >[!NOTE]
   >
   >Para saber mais sobre os arquivos do tipo **formulário**, consulte [esta página](../../configuration/using/identifying-a-form.md).

   No nosso exemplo atual, o arquivo **formulário** deve ser baseado no esquema **cus:individual** e, portanto, deve ter o seguinte layout:

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
1. Crie um novo documento **xtk:navtree** tipo **navtree**.
1. Descreva todos os monitoramentos e campos necessários dependendo do seu modelo de tabela.

   No exemplo atual, o arquivo **navtree** deve ser baseado no esquema **cus:individual** e, portanto, ter o seguinte formato:

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
