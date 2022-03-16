---
product: campaign
title: Elementos e atributos do schema - elemento param
description: elemento param
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 3%

---

# elemento param {#param--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-12}

param:==help

## Atributos {#attributes-12}

* @_operation (cadeia de caracteres)
* @desc (cadeia de caracteres)
* @enum (cadeia de caracteres)
* @inout (cadeia de caracteres)
* @label (cadeia de caracteres)
* @localizable (cadeia de caracteres)
* @name (MNTOKEN)
* @namespace (MNTOKEN)
* @type (cadeia de caracteres)

## Pais {#parents-12}

`<parameters>`

## Crianças {#children-12}

`<help>`

## Descrição {#description-12}

Esse elemento permite definir um parâmetro para chamar um método SOAP.

## Descrição do atributo {#attribute-description-12}

* **desc (cadeia de caracteres)**: descrição que diz respeito à `<param>` elemento.
* **inout (string)**: esse atributo define se o parâmetro está ou não na entrada (in) ou saída (out) da chamada SOAP. Se este atributo não for especificado, o parâmetro padrão é input (&quot;@inout=in&quot;).
* **label (string)**: `<param>` label
* **localizável (string)**: se estiver ativado, esse atributo informará a ferramenta de coleta para recuperar o valor do atributo &quot;@label&quot; para tradução (uso interno).
* **name (MNTOKEN)**: nome interno da `<param>`
* **type (string)**: esse atributo define o tipo de `<param>` elemento

   Lista de tipos disponíveis:

   * ANY
   * compartimento
   * blob
   * booleano
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * data
   * DOMDocument
   * DOMElement
   * double
   * enum
   * float
   * html
   * int64
   * link
   * long
   * memorando
   * MNTOKEN
   * percent
   * chave primária
   * short
   * string
   * tempo
   * timespan
   * uuid

## Exemplos {#examples-9}

Definição da configuração de entrada &quot;serviceName&quot; do tipo string de caracteres:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
