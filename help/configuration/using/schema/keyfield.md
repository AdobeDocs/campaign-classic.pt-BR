---
product: campaign
title: Elementos e atributos de esquema - elemento keyfield
description: elemento keyfield
feature: Schema Extension
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
TQID: https://experienceleague.adobe.com/tVWLlgg97dREZZHvUW81FhDVhS-uNvUHlbhH0YBrAdY
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 104
ht-degree: 4%

---

# elemento keyfield {#keyfield--element}


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
* **xpath (MNTOKEN)**: definição de um índice ou uma chave em um elemento `<attribute>`. Este atributo recebe um Xpath que define o caminho para o atributo de esquema que define a chave ou o índice.

## Exemplos {#examples-}

Seleção do campo &quot;sName&quot; em um índice com um Xpath em &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
