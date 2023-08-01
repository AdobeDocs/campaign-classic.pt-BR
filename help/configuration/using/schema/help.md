---
product: campaign
title: Elementos e atributos de esquema - elemento de ajuda
description: elemento de ajuda
feature: Schema Extension
exl-id: 8207868c-25ff-4ca9-afdd-41b324c7ac0d
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 12%

---

# elemento de ajuda {#help--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-6}

help:==EMPTY

## Atributos {#attributes-6}

nenhuma

## Pais {#parents-6}

`<srcschema>`  ,  `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />`

## Filhos {#children-6}

nenhuma

## Descrição {#description-6}

Esse elemento permite descrever um `<element>`  ou  `<attribute>`   elemento. Ele só pode conter texto e é armazenado em XML no banco de dados.

## Descrição do atributo {#attribute-description-6}

Este elemento não tem atributos.

## Exemplos {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```
