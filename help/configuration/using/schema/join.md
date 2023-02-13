---
product: campaign
title: Elementos e atributos do schema - elemento de junção
description: elemento de junção
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 2%

---

# elemento de junção {#join--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-7}

join:==EMPTY

## Atributos {#attributes-7}

* @dstFilterExpr (cadeia de caracteres)
* @xpath-dst (cadeia de caracteres)
* @xpath-src (cadeia de caracteres)

## Pais {#parents-7}

`<element>`

## Filhos {#children-7}

nenhuma

## Descrição {#description-7}

Permite definir os campos que criam uma ligação entre tabelas SQL.

## Uso e contexto de uso {#use-and-context-of-use-5}

A `<join>`  só poderá ser usado se o elemento principal  `<element>`  é do tipo &quot;link&quot;. Isso significa que o elemento pai deve ter o atributo &quot;@type=link&quot; declarado.

Não é necessário especificar o nome e o namespace da tabela remota no `<join>`  elemento. Eles precisam ser especificados no pai  `<element>`.

Por convenção, os links são definidos no final do schema.

Se a variável `<join>` não é especificado quando o elemento de tipo de link é definido, o link será colocado automaticamente nas chaves primárias de ambas as tabelas.

## Descrição do atributo {#attribute-description-7}

* **dstFilterExpr (cadeia de caracteres)**: esse atributo permite restringir o número de valores elegíveis na tabela remota.
* **xpath-dst (cadeia de caracteres)**: este atributo recebe um Xpath (@name atributo da tabela remota).
* **xpath-src (cadeia de caracteres)**: este atributo recebe um Xpath (@name attribute no schema atual).

## Exemplos {#examples-6}

Link entre o campo &#39;email&#39; da tabela atual e o campo &quot;@company-id&quot; da tabela remota:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Link filtrado para a tabela &quot;cus:Country&quot; com base no conteúdo do campo &quot;@country&quot; que deve conter o valor &quot;EN&quot;:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
