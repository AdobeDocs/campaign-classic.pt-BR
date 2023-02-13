---
product: campaign
title: Elementos e atributos do schema - elemento de condição
description: elemento de condição
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 5%

---

# elemento de condição {#condition--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-2}

condição:==EMPTY

## Atributos {#attributes-2}

* @boolOperator (cadeia de caracteres)
* @enabledIf (cadeia de caracteres)
* @expr (cadeia de caracteres)

## Pais {#parents-2}

`<sysfilter>`

## Filhos {#children-2}

nenhuma

## Descrição {#description-2}

Esse elemento permite definir uma condição de filtragem.

## Uso e contexto de uso {#use-and-context-of-use-2}

One `<sysfiler>`  O elemento pode conter várias condições de filtragem.

## Descrição do atributo {#attribute-description-2}

* **boolOperator (cadeia de caracteres)**: se vários `<conditions>` são definidas no mesmo  `<sysfilter>` , esse atributo permite combiná-los. Por padrão, o link lógico está entre `<condition>` elementos é &quot;AND&quot;. O atributo &quot;@boolOperator&quot; permite combinar links do tipo &quot;OR&quot; e &quot;AND&quot;.
* **enabledIf (cadeia de caracteres)**: teste de ativação de condição.
* **expr (string)**: uma expressão XTK.

## Exemplos {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
