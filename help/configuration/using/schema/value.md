---
solution: Campaign Classic
product: campaign
title: Elementos e atributos
description: Elementos e atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 6%

---


# `<value>` direcionado {#value--element}

## Modelo de conteúdo {#content-model-16}

value:==help

## Atributos {#attributes-16}

* @applyIf (string)
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

Esse elemento permite definir os valores armazenados em uma lista discriminada.

## Descrição do atributo {#attribute-description-16}

* **applyIf (string)**: esse atributo permite tornar um valor de lista discriminada opcional. Ele recebe uma expressão XTK.
* **desc (string)**: descrição do valor da lista discriminada.
* **enabledIf (string)**: para ativar o valor da lista discriminada.
* **img (string)**: imagem vinculada à lista discriminada no formulário &quot;namespace:image_name&quot;. A imagem deve ser importada para o servidor de aplicativos.
* **label (string)**: rótulo do valor da lista discriminada.
* **name (string)**: nome interno do valor da lista discriminada.
* **value (string)**: valor da lista discriminada. O tipo de valor é definido com base no tipo de lista discriminada. Se a lista discriminada for do tipo de string de caractere, ela só poderá conter valores do tipo string de caractere.

## Exemplos {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
