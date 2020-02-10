---
title: Etapas de configuração
seo-title: Etapas de configuração
description: Etapas de configuração
seo-description: null
page-status-flag: never-activated
uuid: 4111a805-95ab-4e26-be51-2db1e5c20f57
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 76174374-af73-4da0-b62b-6979bca0102b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Etapas de configuração{#setup-stages}

O princípio básico é a inserção de tags de rastreamento da Web em determinadas páginas do site.

Há dois tipos de tags:

* **WEB**: esta tag informa se a página foi visitada,
* **TRANSAÇÃO**: opera como uma tag da Web, mas com a possibilidade de adicionar informações sobre o volume de negócios gerado, por exemplo (valor da transação, número de itens comprados etc.).

Aplique as seguintes etapas para configurar essas tags:

1. Identifique as páginas que deseja rastrear e determine seu tipo (WEB ou TRANSAÇÃO).
1. Determine quais informações adicionais você deseja coletar e estenda o esquema **nms:webTrackingLog** com a descrição dessas informações. Por padrão, esse esquema pode armazenar as quantias da transação e o número de itens por transação.
1. Criação de tags de rastreamento da Web. Há duas maneiras de fazer isso:

   * Insira os URLs correspondentes a essas páginas na plataforma do Adobe Campaign e gere e extraia as tags de rastreamento da Web associadas (do **[!UICONTROL Campaign execution>Resources>Web tracking tags]** nó do console do cliente).
   * Crie as tags de rastreamento da Web você mesmo no modo &quot;criação instantânea&quot;: os URLs correspondentes a essas páginas serão inseridos automaticamente na plataforma do Adobe Campaign.

1. Adicione essas tags de forma estática ou dinâmica nas páginas que deseja rastrear.

   >[!NOTE]
   >
   >Todas as tags do tipo WEB podem ser adicionadas como estão às páginas do site. As tags TRANSACTION devem ser modificadas ou adicionadas dinamicamente para conter as informações adicionais (quantidade, itens, etc.).

**Exemplo**:

```
<script type="text/javascript">
var _f = "nmsWebTracking"
var _t = window.location.href.match(/.*://[^/]*(/[^?#&]*)/)[1] + "|w|" + _f
document.write("<img height='0' width='0' alt='' src='" +
window.location.protocol + "//tsupport/r/" +
Math.random().toString() + "?tagid=" + escape(_t) + "'/>")
</script>
```

