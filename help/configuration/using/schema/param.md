---
solution: Campaign Classic
product: campaign
title: Elementos e atributos
description: Elementos e atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 6%

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

Esse elemento permite que você defina um parâmetro para chamar um método SOAP.

## Descrição do atributo {#attribute-description-12}

* **desc (string)**: descrição que diz respeito ao  `<param>` elemento.
* **inout (string)**: esse atributo define se o parâmetro está ou não na entrada (in) ou saída (fora) da chamada SOAP. Se este atributo não for especificado, o parâmetro padrão será input (&quot;@inout=in&quot;).
* **label (string)**:  `<param>` label
* **localizável (string)**: se estiver ativado, esse atributo informará a ferramenta de coleta para recuperar o valor do atributo &quot;@label&quot; para conversão (uso interno).
* **name (MNTOKEN)**: nome interno do  `<param>`
* **type (string)**: este atributo define o tipo de  `<param>` elemento

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

## Exemplos {#examples-9}

Definição da configuração de entrada &quot;serviceName&quot; do tipo de string de caractere:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
