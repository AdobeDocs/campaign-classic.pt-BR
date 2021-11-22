---
product: campaign
title: Etapas de configuração
description: Etapas de configuração
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 5%

---

# Etapas de configuração{#setup-stages}

![](../../assets/v7-only.svg)

O princípio básico é a inserção de tags de rastreamento Web em determinadas páginas do seu site.

Há dois tipos de tags:

* **WEB**: essa tag informa se a página foi visitada,
* **TRANSAÇÃO**: O funciona como uma tag da Web, mas com a possibilidade de adicionar informações sobre o volume de negócios gerado, por exemplo (valor da transação, número de itens comprados etc.).

Siga as etapas abaixo para configurar essas tags:

1. Identifique as páginas que deseja rastrear e determine seu tipo (WEB ou TRANSAÇÃO).
1. Determine quais informações adicionais você deseja coletar e estenda o **nms:webTrackingLog** com a descrição dessas informações. Por padrão, esse schema pode armazenar os valores da transação e o número de itens por transação.
1. Criação das tags de rastreamento Web. Há duas maneiras de fazer isso:

   * Insira os URLs correspondentes a essas páginas na plataforma Adobe Campaign, gere e extraia as tags de rastreamento Web associadas (do **[!UICONTROL Campaign execution>Resources>Web tracking tags]** do console do cliente).
   * Crie as tags de rastreamento web por conta própria no modo &quot;criação instantânea&quot;: os URLs correspondentes a essas páginas serão inseridos automaticamente na plataforma Adobe Campaign.

1. Adicione essas tags de forma estática ou dinâmica nas páginas que você deseja rastrear.

   >[!NOTE]
   >
   >Todas as tags do tipo WEB podem ser adicionadas como às páginas do site. As tags TRANSACTION devem ser modificadas ou adicionadas dinamicamente para conter as informações adicionais (quantidade, itens, etc.).

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
