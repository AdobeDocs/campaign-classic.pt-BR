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
source-wordcount: '101'
ht-degree: 8%

---


# elemento keyfield {#keyfield--element}

## Modelo de conteúdo {#content-model-9}

campo de chaves:==VAZIO

## Atributos {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Pais {#parents-9}

`<key>`  ,  `<dbindex />`

## Filhos {#children-9}

nenhuma

## Descrição {#description-9}

Esse elemento define os campos a serem integrados em um índice ou chave.

## Descrição do atributo {#attribute-description-9}

* **xlink (MNTOKEN)**: permite referenciar automaticamente chaves estrangeiras definidas na junção para uma tabela de relação (link N-N).
* **xpath (MNTOKEN)**: definição de um índice ou chave em um  `<attribute>`  elemento. Esse atributo recebe um Xpath que define o caminho para o atributo do schema que define a chave ou o índice.

## Exemplos {#examples-}

Seleção do campo &quot;sName&quot; em um índice com um Xpath em &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
