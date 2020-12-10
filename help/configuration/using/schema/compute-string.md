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
source-wordcount: '88'
ht-degree: 11%

---


# `<compute-string>` direcionado {#compute-string--element}

## Modelo de conteúdo {#content-model-1}

cadeia de caracteres de computação:==EMPTY

## Atributos {#attributes-1}

@expr

## Pais {#parents-1}

`<element>`

## Filhos {#children-1}

nenhuma

## Descrição {#description-1}

O elemento `<compute-string>` permite que você gere uma string com base em uma expressão XTK para exibir um rótulo &quot;criado&quot; na interface com base em vários valores.

## Uso e contexto de uso {#use-and-context-of-use-1}

Quando nenhum `<compute-string>` é definido, um elemento `<compute-string>` é inserido por padrão com os valores da chave primária no schema.

## Descrição do atributo {#attribute-description-1}

* **expr (string)**: Expressão XTK e/ou Xpath

## Exemplos {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Resultado da string calculada em um recipient: &quot;João da Silva (john.doe@aol.com)&quot;:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
