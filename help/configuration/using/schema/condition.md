---
product: campaign
title: Elementos e atributos de esquema - elemento de condição
description: elemento de condição
feature: Schema Extension
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
TQID: 'https://experienceleague.adobe.com/Jx8bLCt1UEqAZDm0cSuexx25js-e5xTsvkeSMzVCUHw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 5%
---
# elemento de condição {#condition--element}


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
