---
title: Edição
seo-title: Edição
description: Edição
seo-description: null
page-status-flag: never-activated
uuid: df9298fc-5f62-4afb-8118-ca7e3987e81f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
discoiquuid: 820be231-af76-44ce-8f4d-cd5eae1eb169
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Edição{#edition}

A tela para criar e configurar os documentos de configuração da hierarquia de navegação pode ser acessada pelo **[!UICONTROL Administration > Configuration > Navigation hierarchies]** nó:

![](assets/d_ncs_integration_navigation_arbo.png)

A configuração da hierarquia de navegação é dividida em vários documentos XML. Ele opera com um princípio semelhante à extensão do esquema: todos os documentos são mesclados para gerar um único documento contendo a configuração inteira. Este documento não pode ser editado e é exibido por meio da guia &quot;Visualizar&quot;.

O campo de edição fornece o conteúdo do documento XML:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>O controle de edição &quot;Nome&quot; permite que você insira a chave do documento que consiste no nome e no namespace. The &quot;name&quot; and &quot;namespace&quot; attributes of the **`<navtree>`** element are automatically updated in the XML edit field of the schema.

A visualização gera automaticamente o documento unido que contém a configuração completa:

![](assets/d_ncs_integration_navigation_preview.png)

