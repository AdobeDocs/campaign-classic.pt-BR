---
product: campaign
title: Elementos e atributos do schema - elemento do campo-chave
description: elemento do campo de chaves
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 2%

---

# elemento do campo de chaves {#keyfield--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-9}

keyfield:==EMPTY

## Atributos {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Pais {#parents-9}

`<key>`  ,  `<dbindex />`

## Crianças {#children-9}

nenhuma

## Descrição {#description-9}

Esse elemento define os campos a serem integrados em um índice ou chave.

## Descrição do atributo {#attribute-description-9}

* **xlink (MNTOKEN)**: permite referenciar automaticamente chaves estrangeiras definidas na junção para uma tabela de relação (link N-N).
* **xpath (MNTOKEN)**: definição de um índice ou chave em um `<attribute>`  elemento. Esse atributo recebe um Xpath que define o caminho para o atributo schema que define a chave ou o índice.

## Exemplos {#examples-}

Seleção do campo &quot;sName&quot; em um índice com um Xpath em &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
