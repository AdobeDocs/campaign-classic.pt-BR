---
product: campaign
title: Elementos e atributos de esquema - elemento keyfield
description: elemento keyfield
feature: Schema Extension
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 4%

---

# elemento keyfield {#keyfield--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-9}

campo-chave:==EMPTY

## Atributos {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Pais {#parents-9}

`<key>`  ,  `<dbindex />`

## Filhos {#children-9}

nenhuma

## Descrição {#description-9}

Esse elemento define os campos que serão integrados em um índice ou em uma chave.

## Descrição do atributo {#attribute-description-9}

* **xlink (MNTOKEN)**: permite referenciar automaticamente chaves estrangeiras definidas na associação para uma tabela de relação (link N-N).
* **xpath (MNTOKEN)**: definição de um índice ou de uma chave em um `<attribute>`  elemento. Este atributo recebe um Xpath que define o caminho para o atributo de esquema que define a chave ou o índice.

## Exemplos {#examples-}

Seleção do campo &quot;sName&quot; em um índice com um Xpath em &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
