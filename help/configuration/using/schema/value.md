---
product: campaign
title: Elementos e atributos
description: Elementos e atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 5%

---

# elemento de valor {#value--element}

![](../../../assets/v7-only.svg)

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

## Crianças {#children-16}

`<help>`

## Descrição {#description-16}

Esse elemento permite definir os valores armazenados em uma enumeração.

## Descrição do atributo {#attribute-description-16}

* **applicableIf (cadeia de caracteres)**: esse atributo permite tornar um valor de enumeração opcional. Ele recebe uma expressão XTK.
* **desc (cadeia de caracteres)**: descrição do valor de enumeração.
* **enabledIf (cadeia de caracteres)**: para ativar o valor de enumeração.
* **img (string)**: imagem vinculada à enumeração no formulário &quot;namespace:image_name&quot;. A imagem deve ser importada para o servidor de aplicativos.
* **label (string)**: do valor de enumeração.
* **name (string)**: nome interno do valor de enumeração.
* **valor (string)**: valor do valor de enumeração. O tipo de valor é definido com base no tipo de enumeração. Se a enumeração for do tipo de string de caracteres, ela só poderá conter valores do tipo string de caracteres.

## Exemplos {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
