---
product: campaign
title: Elementos e atributos de esquema - elemento join
description: elemento join
feature: Schema Extension
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
TQID: 'https://experienceleague.adobe.com/qze6zOBr1DxBIClCPPjIAZ2BeS7mMwnTFuoMw2-d9Cw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 2%
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

Permite definir os campos que criam uma ligação entre tabelas SQL.

## Uso e contexto de uso {#use-and-context-of-use-5}

Um elemento `<join>` só poderá ser usado se o elemento `<element>` pai for do tipo &#39;link&#39;. Isso significa que o elemento pai deve ter o atributo &quot;@type=link&quot; declarado.

Não é necessário especificar o nome e o namespace da tabela remota no elemento `<join>`. Eles precisam ser especificados no pai `<element>`.

Por convenção, os links são definidos no final do schema.

Se o elemento `<join>` não for especificado quando o elemento de tipo de link for definido, o link será colocado automaticamente nas chaves primárias de ambas as tabelas.

## Descrição do atributo {#attribute-description-7}

* **dstFilterExpr (string)**: este atributo permite restringir o número de valores qualificados na tabela remota.
* **xpath-dst (string)**: este atributo recebe um Xpath (atributo @name da tabela remota).
* **xpath-src (cadeia de caracteres)**: este atributo recebe um Xpath (atributo @name no esquema atual).

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
