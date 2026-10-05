---
product: campaign
title: Elementos e atributos - elemento de valor
description: Elementos e atributos
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
TQID: 'https://experienceleague.adobe.com/rGaA--VHVGxCBHX5SgZUQQ9AwMgOTYWqMYGpYWU4-WY'
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
source-wordcount: '147'
ht-degree: 4%
---
# elemento value {#value--element}


## Modelo de conteúdo {#content-model-16}

value:==help

## Atributos {#attributes-16}

* @applicableIf (string)
* @desc (string)
* @enabledIf (string)
* @img (string)
* @label (string)
* @name (string)
* @value (string)

## Pais {#parents-16}

`<enumeration>`

## Filhos {#children-16}

`<help>`

## Descrição {#description-16}

Esse elemento permite definir os valores armazenados em uma enumeração.

## Descrição do atributo {#attribute-description-16}

* **applicableIf (string)**: este atributo permite que você torne um valor de enumeração opcional. Ele recebe uma expressão XTK.
* **desc (cadeia de caracteres)**: descrição do valor de enumeração.
* **enabledIf (cadeia de caracteres)**: condição para ativar o valor de enumeração.
* **img (cadeia de caracteres)**: imagem vinculada à enumeração no formulário &quot;namespace:image_name&quot;. A imagem deve ser importada para o servidor de aplicativos.
* **rótulo (cadeia de caracteres)**: rótulo do valor de enumeração.
* **nome (cadeia de caracteres)**: nome interno do valor de enumeração.
* **valor (cadeia de caracteres)**: valor do valor de enumeração. O tipo de valor é definido com base no tipo de enumeração. Se a enumeração for do tipo character string, ela só poderá conter valores do tipo character string.

## Exemplos {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
