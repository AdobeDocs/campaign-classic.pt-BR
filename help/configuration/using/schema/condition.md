---
product: campaign
title: Elementos e atributos
description: Elementos e atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 9%

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

## Crianças {#children-2}

nenhuma

## Descrição {#description-2}

Esse elemento permite definir uma condição de filtragem.

## Uso e contexto de uso {#use-and-context-of-use-2}

Um elemento `<sysfiler>` pode conter várias condições de filtragem.

## Descrição do atributo {#attribute-description-2}

* **boolOperator (sequência)**: se várias  `<conditions>` forem definidas no mesmo   `<sysfilter>` elemento, esse atributo permitirá combiná-las. Por padrão, o link lógico está entre os elementos `<condition>` é &quot;AND&quot;. O atributo &quot;@boolOperator&quot; permite combinar links do tipo &quot;OR&quot; e &quot;AND&quot;.
* **enabledIf (sequência de caracteres)**: teste de ativação de condição.
* **expr (string)**: uma expressão XTK.

## Exemplos {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
