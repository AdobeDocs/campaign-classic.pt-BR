---
product: campaign
title: Edição
description: Edição
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 1%

---

# Editar árvore de navegação do Campaign Explorer{#edition}

A tela para criar e configurar os documentos de configuração da hierarquia de navegação é acessível por meio do nó **[!UICONTROL Administration > Configuration > Navigation hierarchies]**:

![](assets/d_ncs_integration_navigation_arbo.png)

A configuração da hierarquia de navegação é dividida em vários documentos XML. Ela opera em um princípio semelhante à extensão do schema: todos os documentos são mesclados para gerar um único documento contendo toda a configuração. Este documento não pode ser editado e é exibido por meio da guia &quot;Preview&quot;.

O campo de edição fornece o conteúdo do documento XML:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>O controle de edição &quot;Name&quot; permite inserir a chave do documento que consiste no nome e no namespace. Os atributos &quot;name&quot; e &quot;namespace&quot; do elemento **`<navtree>`** são atualizados automaticamente no campo de edição XML do esquema.

A visualização gera automaticamente o documento mesclado contendo a configuração completa:

![](assets/d_ncs_integration_navigation_preview.png)
