---
product: campaign
title: Elementos e atributos
description: Elementos e atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 10%

---

# elemento de cadeia de caracteres de computação {#compute-string--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-1}

compute-string:==EMPTY

## Atributos {#attributes-1}

@expr

## Pais {#parents-1}

`<element>`

## Crianças {#children-1}

nenhuma

## Descrição {#description-1}

O elemento `<compute-string>` permite gerar uma string com base em uma expressão XTK para exibir um rótulo &quot;construído&quot; na interface com base em vários valores.

## Uso e contexto de uso {#use-and-context-of-use-1}

Quando nenhum `<compute-string>` é definido, um elemento `<compute-string>` é inserido por padrão com os valores da chave primária no schema.

## Descrição do atributo {#attribute-description-1}

* **expr (string)**: Expressão XTK e/ou Xpath

## Exemplos {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Resultado da string calculada em um recipient: &quot;John Doe (john.doe@aol.com)&quot;:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
