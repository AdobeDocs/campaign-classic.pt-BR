---
product: campaign
title: Elementos e atributos do schema - elemento de enumeração
description: elemento de enumeração
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 6%

---

# elemento de enumeração {#enumeration--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-5}

enumeração:==(help| value)

## Atributos {#attributes-5}

* @basetype (cadeia de caracteres)
* @default (cadeia de caracteres)
* @desc (cadeia de caracteres)
* @label (cadeia de caracteres)
* @name (cadeia de caracteres)
* @template (cadeia de caracteres)

## Pais {#parents-5}

`<srcschema>`

## Filhos {#children-5}

* `<help>`
* `<value>`

## Descrição {#description-5}

Esse elemento permite definir uma enumeração de valor. Uma enumeração pertence ao schema no qual está definida, mas é acessível por meio de outro schema.

## Uso e contexto de uso {#use-and-context-of-use-4}

As enumerações são definidas no início de um schema (antes do elemento principal ser definido).

## Descrição do atributo {#attribute-description-5}

* **basetype (cadeia de caracteres)**: tipo dos valores armazenados na enumeração.

   Lista de tipos disponíveis:

   * QUALQUER UMA
   * compartimento
   * blob
   * booleano
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * DOMDocument
   * DOMElement
   * double
   * enum
   * float
   * html
   * int64
   * Link 
   * long
   * memorando
   * MNTOKEN
   * percent
   * chave primária
   * short
   * sequência de caracteres
   * tempo
   * timespan
   * uuid

* **padrão (string)**: Valor padrão. O valor padrão também pode ser um dos valores definidos na enumeração.
* **desc (cadeia de caracteres)**: descrição da enumeração.
* **label (string)**: rótulo da enumeração.
* **name (string)**: nome interno da enumeração.
* **template (string)**: esse atributo define uma referência a um `<enumeration>` elemento compartilhado por vários schemas. A definição é copiada automaticamente para o schema atual.

## Exemplos {#examples-4}

Exemplo de valores de enumeração cujos valores são armazenados no banco de dados:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

Definição de uma enumeração com um valor padrão:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```
