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
source-wordcount: '42'
ht-degree: 23%

---


# `<sysfilter>` direcionado {#sysfilter--element}

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
