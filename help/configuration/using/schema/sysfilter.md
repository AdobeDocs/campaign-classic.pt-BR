---
product: campaign
title: Elementos e atributos - elemento sysfilter
description: Elementos e atributos
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
TQID: https://experienceleague.adobe.com/hjsD-JSGBPnwyj1IsLDo-tUy-63apy0-6kT9vngaaQk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 45
ht-degree: 17%

---

# elemento sysfilter {#sysfilter--element}


## Modelo de conteúdo {#content-model-15}

sysFilter:==condition

## Atributos {#attributes-15}

nenhuma

## Pais {#parents-15}

`<element>`

## Filhos {#children-15}

`<condition>`

## Descrição {#description-15}

Esse elemento permite definir um filtro.

## Descrição do atributo {#attribute-description-15}

Este elemento não tem atributos.

## Exemplos {#examples-12}

Definição de um filtro com uma condição no atributo @name:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
