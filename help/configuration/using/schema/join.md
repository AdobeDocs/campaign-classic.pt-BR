---
solution: Campaign Classic
product: campaign
title: Elementos e atributos
description: Elementos e atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 4%

---


# elemento join {#join--element}

## Modelo de conteúdo {#content-model-7}

join:==EMPTY

## Atributos {#attributes-7}

* @dstFilterExpr (string)
* @xpath-dst (string)
* @xpath-src (string)

## Pais {#parents-7}

`<element>`

## Filhos {#children-7}

nenhuma

## Descrição {#description-7}

Permite definir os campos que criam uma junção entre tabelas SQL.

## Uso e contexto de uso {#use-and-context-of-use-5}

Um elemento `<join>` só pode ser usado se o elemento pai `<element>` for do tipo &#39;link&#39;. Isso significa que o elemento pai deve ter o atributo &quot;@type=link&quot; declarado.

Não é necessário especificar o nome e a namespace da tabela remota no elemento `<join>`. Eles precisam ser especificados no pai `<element>`.

Por convenção, os links são definidos no final do schema.

Se o elemento `<join>` não for especificado quando o elemento de tipo de link for definido, o link será colocado automaticamente nas chaves primárias de ambas as tabelas.

## Descrição do atributo {#attribute-description-7}

* **dstFilterExpr (string)**: esse atributo permite restringir o número de valores elegíveis na tabela remota.
* **xpath-dst (string)**: este atributo recebe um Xpath (@name atributo da tabela remota).
* **xpath-src (string)**: este atributo recebe um atributo Xpath (@name no schema atual).

## Exemplos {#examples-6}

Link entre o campo &#39;email&#39; da tabela atual e o campo &quot;@compagny-id&quot; da tabela remota:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Link filtrado para a tabela &quot;cus:Country&quot; com base no conteúdo do campo &quot;@country&quot; que deve conter o valor &#39;EN&#39;:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
