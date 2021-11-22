---
product: campaign
title: Configuração da interface
description: Configuração da interface
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 6%

---

# Configuração da interface{#configuring-the-interface}

![](../../assets/v7-only.svg)

Para exibir e diálogo com a nova tabela de recipients na interface do Adobe Campaign, siga as etapas abaixo:

* Crie um novo formulário para editar o conteúdo da nova tabela de recipients.
* Insira um novo tipo na pasta da árvore do explorador.
* Crie um novo aplicativo da Web para acessar a tabela personalizada por meio da página inicial do Adobe Campaign.

O Adobe Campaign usa uma variável global &quot;Nms_DefaultRcpSchema&quot; para diálogo com o banco de dados do recipient padrão (nms:recipient). Portanto, essa variável precisa ser alterada.

1. Vá para o **[!UICONTROL Administration>Platform>Options]** nó do explorador.
1. Altere o valor da variável **Nms_DefaultRcpSchema** com o nome do schema que corresponde à tabela de recipients externos (neste caso: cus:individual).
1. Salve as alterações.

## Criação de um novo de formulário {#creating-a-new-form-}

A criação de um novo formulário permitirá exibir e editar os dados da tabela de destinatários externos.

>[!IMPORTANT]
>
>O nome do formulário deve ser idêntico ao nome do schema abordado.

1. Vá para o **Administração > Configuração > Formulários de entrada** nó do explorador.
1. Crie um novo **xtk:form** type **formulário** arquivo.
1. Descreva todos os campos e monitoramento necessários, dependendo do modelo da tabela.

   >[!NOTE]
   >
   >Para saber mais sobre **formulário** arquivos do tipo , consulte [esta página](../../configuration/using/identifying-a-form.md).

   No nosso exemplo atual, a variável **formulário** O arquivo deve ser baseado na variável **cus:individual** e, portanto, ter o seguinte layout:

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
1. Crie um novo **xtk:navtree** type **navarinha** documento.
1. Descreva todos os campos e monitoramento necessários, dependendo do modelo da tabela.

   >[!NOTE]
   >
   >Para obter mais informações **navarinha** arquivos do tipo , consulte [esta página](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

   No exemplo atual, a variável **navarinha** O arquivo deve ser baseado na variável **cus:individual** e, portanto, ter o seguinte formulário:

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
