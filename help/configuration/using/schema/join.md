---
product: campaign
title: Elementos e atributos de esquema - elemento join
description: elemento join
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 2%

---

# elemento join {#join--element}

![](../../../assets/v7-only.svg)

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

Permite definir os campos que criam uma ligação entre tabelas SQL.

## Uso e contexto de uso {#use-and-context-of-use-5}

A `<join>`  o elemento só pode ser usado se o pai  `<element>`  elemento é do tipo &#39;link&#39;. Isso significa que o elemento pai deve ter o atributo &quot;@type=link&quot; declarado.

Não é necessário especificar o nome e o namespace da tabela remota no `<join>`  elemento. Eles precisam ser especificados no pai  `<element>`.

Por convenção, os links são definidos no final do schema.

Se a variável `<join>` O elemento não é especificado quando o elemento de tipo de link é definido. O link será colocado automaticamente nas chaves primárias de ambas as tabelas.

## Descrição do atributo {#attribute-description-7}

* **dstFilterExpr (sequência de caracteres)**: este atributo permite restringir o número de valores qualificados na tabela remota.
* **xpath-dst (sequência de caracteres)**: este atributo recebe um Xpath (atributo @name da tabela remota).
* **xpath-src (sequência de caracteres)**: este atributo recebe um Xpath (atributo @name no esquema atual).

## Exemplos {#examples-6}

Link entre o campo &quot;email&quot; da tabela atual e o campo &quot;@compagny-id&quot; da tabela remota:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Link filtrado em direção à tabela &quot;cus:Country&quot; com base no conteúdo do campo &quot;@country&quot; que deve conter o valor &quot;EN&quot;:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
