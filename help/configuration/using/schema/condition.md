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
source-wordcount: '92'
ht-degree: 10%

---


# `<condition>` direcionado {#condition--element}

## Modelo de conteúdo {#content-model-2}

condição:==VAZIA

## Atributos {#attributes-2}

* @boolOperador (string)
* @enabledIf (string)
* @expr (string)

## Pais {#parents-2}

`<sysfilter>`

## Filhos {#children-2}

nenhuma

## Descrição {#description-2}

Esse elemento permite definir uma condição de filtragem.

## Uso e contexto de uso {#use-and-context-of-use-2}

Um elemento `<sysfiler>` pode conter várias condições de filtragem.

## Descrição do atributo {#attribute-description-2}

* **boolOperador (string)**: se vários  `<conditions>` forem definidos dentro do mesmo   `<sysfilter>` elemento, esse atributo permitirá que você os combine. Por padrão, o link lógico está entre `<condition>` elementos é &quot;AND&quot;. O atributo &quot;@boolOperador&quot; permite combinar links de tipo &quot;OU&quot; e &quot;E&quot;.
* **enabledIf (string)**: teste de ativação de condição.
* **expr (string)**: uma expressão XTK.

## Exemplos {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
