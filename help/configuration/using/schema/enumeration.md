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
source-wordcount: '195'
ht-degree: 6%

---


# `<enumeration>` direcionado {#enumeration--element}

## Modelo de conteúdo {#content-model-5}

lista discriminada:==(ajuda| valor)

## Atributos {#attributes-5}

* @basetype (string)
* @default (string)
* @desc (string)
* @label (string)
* @name (string)
* @template (string)

## Pais {#parents-5}

`<srcschema>`

## Filhos {#children-5}

* `<help>`
* `<value>`

## Descrição {#description-5}

Esse elemento permite definir uma lista discriminada de valor. Uma lista discriminada pertence ao schema no qual está definida, mas pode ser acessada por meio de outro schema.

## Uso e contexto de uso {#use-and-context-of-use-4}

As listas discriminadas são definidas no start de um schema (antes de o elemento principal ser definido).

## Descrição do atributo {#attribute-description-5}

* **basetype (string)**: tipo dos valores armazenados na lista discriminada.

   Lista de tipos disponíveis:

   * ANY
   * compartimento
   * mancha
   * booleano
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * DOMDocument
   * DOMElement
   * duplo
   * enum
   * flutuante
   * html
   * int64
   * link
   * long
   * memorando
   * MNTOKEN
   * percent
   * primário
   * short
   * string
   * tempo
   * tempo
   * uuid

* **padrão (string)**: Valor padrão. O valor padrão também pode ser um dos valores definidos na lista discriminada.
* **desc (string)**: Descrição da lista discriminada.
* **label (string)**: Etiqueta da lista discriminada.
* **name (string)**: nome interno da lista discriminada.
* **template (string)**: esse atributo define uma referência a um  `<enumeration>` elemento compartilhado por vários schemas. A definição é copiada automaticamente para o schema atual.

## Exemplos {#examples-4}

Exemplo de valores de lista discriminada cujos valores são armazenados no banco de dados:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

Definição de uma lista discriminada com um valor padrão:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```
