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
source-wordcount: '43'
ht-degree: 20%

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
