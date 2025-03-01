---
product: campaign
title: Elementos e atributos de esquema - elemento de enumeração
description: elemento de enumeração
feature: Schema Extension
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 8%

---

# elemento de enumeração {#enumeration--element}


## Modelo de conteúdo {#content-model-5}

enumeração:==(ajuda| value)

## Atributos {#attributes-5}

* @basetype (string)
* @default (string)
* @desc (string)
* @label (string)
* @name (string)
* @template (string)

## Pais {#parents-5}

`<srcschema>`

## Derivados {#children-5}

* `<help>`
* `<value>`

## Descrição {#description-5}

Esse elemento permite definir uma enumeração de valor. Uma enumeração pertence ao schema que está definido em, mas é acessível por meio de outro schema.

## Uso e contexto de uso {#use-and-context-of-use-4}

Enumerações são definidas no início de um esquema (antes de o elemento principal ser definido).

## Descrição do atributo {#attribute-description-5}

* **basetype (string)**: tipo dos valores armazenados na enumeração.

  Lista de tipos disponíveis:

   * QUALQUER UMA
   * compartimento
   * blob
   * booleano
   * byte
   * CDATA
   * data e hora
   * datetimetz
   * datetimenotz
   * data
   * Documento DOM
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
   * por cento
   * primarykey
   * curto
   * sequência de caracteres
   * tempo
   * intervalo de tempo
   * uuid

* **padrão (cadeia de caracteres)**: valor padrão. O valor padrão também pode ser um dos valores definidos na lista discriminada.
* **desc (cadeia de caracteres)**: descrição da enumeração.
* **rótulo (cadeia de caracteres)**: rótulo de enumeração.
* **nome (cadeia de caracteres)**: nome interno da enumeração.
* **modelo (cadeia de caracteres)**: este atributo define uma referência a um elemento `<enumeration>` compartilhado por vários esquemas. A definição é copiada automaticamente para o esquema atual.

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
