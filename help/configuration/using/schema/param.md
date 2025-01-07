---
product: campaign
title: Elementos e atributos de esquema - elemento param
description: elemento param
feature: Schema Extension
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 9%

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

## Derivados {#children-12}

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
