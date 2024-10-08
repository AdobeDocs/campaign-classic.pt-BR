---
product: campaign
title: Etapas de configuração
description: Etapas de configuração
feature: Configuration
role: Data Engineer, Developer
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 5%

---

# Etapas de configuração{#setup-stages}

O princípio básico é a inserção de tags de rastreamento Web em determinadas páginas do site.

Há dois tipos de tags:

* **WEB**: esta marca informa se a página foi visitada,
* **TRANSACTION**: funciona como uma marca da web, mas com a possibilidade de adicionar informações sobre o volume de negócios gerado, por exemplo (valor da transação, número de itens comprados etc.).

Siga as etapas abaixo para configurar essas tags:

1. Identifique as páginas que deseja rastrear e determine o tipo (WEB ou TRANSAÇÃO).
1. Determine quais informações adicionais você deseja coletar e estenda o esquema **nms:webTrackingLog** com a descrição dessas informações. Por padrão, esse esquema pode armazenar os valores de transação e o número de itens por transação.
1. Criação das tags de rastreamento Web. Há duas maneiras de fazer isso:

   * Insira as URLs correspondentes a essas páginas na plataforma Adobe Campaign e gere e extraia as tags de rastreamento Web associadas (do nó **[!UICONTROL Campaign execution>Resources>Web tracking tags]** do console do cliente).
   * Crie você mesmo as tags de rastreamento Web no modo de &quot;criação instantânea&quot;: os URLs correspondentes a essas páginas serão inseridos automaticamente na plataforma Adobe Campaign.

1. Adicione essas tags estática ou dinamicamente nas páginas que você deseja rastrear.

   >[!NOTE]
   >
   >Todas as tags do tipo Web podem ser adicionadas da mesma maneira que estão nas páginas do site. As tags TRANSACTION devem ser modificadas ou adicionadas dinamicamente para conter as informações adicionais (quantidade, itens, etc.).

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
