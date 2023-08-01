---
product: campaign
title: Elementos e atributos - elemento de valor
description: Elementos e atributos
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 4%

---

# elemento value {#value--element}

![](../../../assets/v7-only.svg)

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

* **applicableIf (string)**: esse atributo permite que você torne um valor de enumeração opcional. Ele recebe uma expressão XTK.
* **desc (string)**: descrição do valor de enumeração.
* **enabledIf (cadeia de caracteres)**: condição para ativar o valor de enumeração.
* **img (string)**: imagem vinculada à enumeração no formulário &quot;namespace:image_name&quot;. A imagem deve ser importada para o servidor de aplicativos.
* **rótulo (string)**: rótulo do valor de enumeração.
* **nome (sequência de caracteres)**: nome interno do valor de enumeração.
* **value (string)**: valor do valor de enumeração. O tipo de valor é definido com base no tipo de enumeração. Se a enumeração for do tipo character string, ela só poderá conter valores do tipo character string.

## Exemplos {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
