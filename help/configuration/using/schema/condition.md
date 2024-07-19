---
product: campaign
title: Elementos e atributos de esquema - elemento de condição
description: elemento de condição
feature: Schema Extension
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 5%

---

# elemento de condição {#condition--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-2}

condition:==EMPTY

## Atributos {#attributes-2}

* @boolOperator (string)
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

* **boolOperator (string)**: se vários `<conditions>` estiverem definidos no mesmo elemento `<sysfilter>`, esse atributo permitirá que você os combine. Por padrão, o vínculo lógico entre `<condition>` elementos é &quot;AND&quot;. O atributo &quot;@boolOperator&quot; permite combinar links dos tipos &quot;OR&quot; e &quot;AND&quot;.
* **enabledIf (cadeia de caracteres)**: teste de ativação de condição.
* **expr (cadeia de caracteres)**: uma expressão XTK.

## Exemplos {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
