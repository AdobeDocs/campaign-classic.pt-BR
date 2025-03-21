---
product: campaign
title: Elementos e atributos - elemento de valor
description: Elementos e atributos
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 2%

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

## Derivados {#children-16}

`<help>`

## Descrição {#description-16}

Esse elemento permite definir os valores armazenados em uma enumeração.

## Descrição do atributo {#attribute-description-16}

* **applicableIf (string)**: este atributo permite que você torne um valor de enumeração opcional. Ele recebe uma expressão XTK.
* **desc (cadeia de caracteres)**: descrição do valor de enumeração.
* **enabledIf (cadeia de caracteres)**: condição para ativar o valor de enumeração.
* **img (string)**: imagem vinculada à enumeração no formulário &quot;namespace:image_name&quot;. A imagem deve ser importada para o servidor de aplicativos.
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
