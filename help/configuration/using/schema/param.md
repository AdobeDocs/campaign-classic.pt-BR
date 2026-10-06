---
product: campaign
title: Elementos e atributos de esquema - elemento param
description: elemento param
feature: Schema Extension
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
TQID: 'https://experienceleague.adobe.com/fiMkJtGU90FP-G6BJhTnIrgBJ39uIJaakqKD49EhXS0'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 12%
---
# elemento param {#param--element}


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

* **desc (cadeia de caracteres)**: descrição que afeta o elemento `<param>`.
* **inout (string)**: este atributo define se o parâmetro está ou não na entrada (in) ou saída (out) da chamada SOAP. Se esse atributo não for especificado, o parâmetro padrão será input (&quot;@inout=in&quot;).
* **rótulo (cadeia de caracteres)**: `<param>` rótulo
* **localizable (string)**: se estiver ativado, este atributo informa à ferramenta de coleção para recuperar o valor do atributo &quot;@label&quot; para tradução (uso interno).
* **nome (MNTOKEN)**: nome interno do `<param>`
* **tipo (cadeia de caracteres)**: este atributo define o tipo de elemento `<param>`

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
  * longo
  * nota
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
