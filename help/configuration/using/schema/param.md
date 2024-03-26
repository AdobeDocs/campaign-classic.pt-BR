---
product: campaign
title: Elementos e atributos de esquema - elemento param
description: elemento param
feature: Schema Extension
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 7%

---

# elemento param {#param--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-12}

param:==help

## Atributos {#attributes-12}

* @_operation (string)
* @desc (string)
* @enum (string)
* @inout (string)
* @label (string)
* @localizable (string)
* @name (MNTOKEN)
* @namespace (MNTOKEN)
* @type (string)

## Pais {#parents-12}

`<parameters>`

## Filhos {#children-12}

`<help>`

## Descrição {#description-12}

Esse elemento permite definir um parâmetro para chamar um método SOAP.

## Descrição do atributo {#attribute-description-12}

* **desc (string)**: descrição que diz respeito ao `<param>` elemento.
* **inout (string)**: esse atributo define se o parâmetro está na entrada (in) ou saída (out) da chamada SOAP. Se esse atributo não for especificado, o parâmetro padrão será input (&quot;@inout=in&quot;).
* **rótulo (string)**: `<param>` rótulo
* **localizável (string)**: se estiver ativado, esse atributo informará à ferramenta de coleção para recuperar o valor do atributo &quot;@label&quot; para tradução (uso interno).
* **nome (MNTOKEN)**: nome interno da `<param>`
* **tipo (string)**: este atributo define o tipo de `<param>` element

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

## Exemplos {#examples-9}

Definição da configuração de entrada &quot;serviceName&quot; do tipo de cadeia de caracteres:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
