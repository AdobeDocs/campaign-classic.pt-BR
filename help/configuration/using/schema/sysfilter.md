---
product: campaign
title: Elementos e atributos
description: Elementos e atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '43'
ht-degree: 20%

---

# elemento sysfilter {#sysfilter--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-15}

sysFilter:==condition

## Atributos {#attributes-15}

nenhuma

## Pais {#parents-15}

`<element>`

## Crianças {#children-15}

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
