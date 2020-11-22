---
solution: Campaign Classic
product: campaign
title: Edição
description: Edição
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 2%

---


# Edição{#edition}

A tela para criar e configurar os documentos de configuração da hierarquia de navegação pode ser acessada pelo **[!UICONTROL Administration > Configuration > Navigation hierarchies]** nó:

![](assets/d_ncs_integration_navigation_arbo.png)

A configuração da hierarquia de navegação é dividida em vários documentos XML. Funciona de acordo com um princípio semelhante ao da extensão do schema: todos os documentos são unidos para gerar um único documento contendo a configuração inteira. Este documento não pode ser editado e é exibido na guia &quot;Pré-visualização&quot;.

O campo de edição fornece o conteúdo do documento XML:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>O controle de edição &quot;Nome&quot; permite que você insira a chave do documento que consiste no nome e na namespace. The &quot;name&quot; and &quot;namespace&quot; attributes of the **`<navtree>`** element are automatically updated in the XML edit field of the schema.

A pré-visualização gera automaticamente o documento mesclado que contém a configuração completa:

![](assets/d_ncs_integration_navigation_preview.png)

