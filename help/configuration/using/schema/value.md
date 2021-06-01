---
product: campaign
title: Elementos e atributos
description: Elementos e atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 5%

---

# elemento de valor {#value--element}

## Modelo de conteúdo {#content-model-16}

valor:==help

## Atributos {#attributes-16}

* @applicableIf (cadeia de caracteres)
* @desc (cadeia de caracteres)
* @enabledIf (cadeia de caracteres)
* @img (cadeia de caracteres)
* @label (cadeia de caracteres)
* @name (cadeia de caracteres)
* @value (cadeia de caracteres)

## Pais {#parents-16}

`<enumeration>`

## Filhos {#children-16}

`<help>`

## Descrição {#description-16}

Esse elemento permite definir os valores armazenados em uma enumeração.

## Descrição do atributo {#attribute-description-16}

* **applicableIf (cadeia de caracteres)**: esse atributo permite tornar um valor de enumeração opcional. Ele recebe uma expressão XTK.
* **desc (string)**: descrição do valor de enumeração.
* **enabledIf (sequência de caracteres)**: para ativar o valor de enumeração.
* **img (string)**: imagem vinculada à enumeração no formulário &quot;namespace:image_name&quot;. A imagem deve ser importada para o servidor de aplicativos.
* **label (string)**: do valor de enumeração.
* **name (sequência de caracteres)**: nome interno do valor de enumeração.
* **valor (string)**: valor do valor de enumeração. O tipo de valor é definido com base no tipo de enumeração. Se a enumeração for do tipo string de caracteres, ela só poderá conter valores do tipo string de caracteres.

## Exemplos {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
