---
product: campaign
title: Editar árvore de navegação do Campaign Explorer
description: Editar árvore de navegação do Campaign Explorer
feature: Application Settings
badge-v7-only: label="v7" type="Informative" tooltip="Aplicável somente ao Campaign Classic v7"
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---


# Editar árvore de navegação do Campaign Explorer{#edition}

A tela para criar e configurar os documentos de configuração da hierarquia de navegação pode ser acessada por meio da **[!UICONTROL Administration > Configuration > Navigation hierarchies]** nó:

![](assets/d_ncs_integration_navigation_arbo.png)

A configuração da hierarquia de navegação é dividida em vários documentos XML. Ela opera em um princípio semelhante à extensão do schema: todos os documentos são mesclados para gerar um único documento que contém toda a configuração. Este documento não pode ser editado e é exibido por meio da guia &quot;Preview&quot;.

O campo de edição fornece o conteúdo do documento XML:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>O controle de edição &quot;Nome&quot; permite a inserção da chave do documento que consiste no nome e no namespace. Os atributos &quot;name&quot; e &quot;namespace&quot; da variável **`<navtree>`** Os elementos são atualizados automaticamente no campo de edição XML do schema.

A visualização gera automaticamente o documento mesclado que contém a configuração completa:

![](assets/d_ncs_integration_navigation_preview.png)
