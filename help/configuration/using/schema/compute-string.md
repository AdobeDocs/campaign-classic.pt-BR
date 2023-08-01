---
product: campaign
title: Elementos e atributos - elemento compute-string
description: elemento compute-string
feature: Schema Extension
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 5%

---

# elemento compute-string {#compute-string--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-1}

string de cálculo:==VAZIO

## Atributos {#attributes-1}

@expr

## Pais {#parents-1}

`<element>`

## Filhos {#children-1}

nenhuma

## Descrição {#description-1}

A variável `<compute-string>` element permite gerar uma cadeia de caracteres com base em uma expressão XTK para exibir um rótulo &quot;criado&quot; na interface com base em vários valores.

## Uso e contexto de uso {#use-and-context-of-use-1}

Quando não `<compute-string>` for definida, uma `<compute-string>` element é inserido por padrão com os valores da chave primária no schema.

## Descrição do atributo {#attribute-description-1}

* **expr (string)**: expressão XTK e/ou Xpath

## Exemplos {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Resultado da cadeia de caracteres calculada em um destinatário: &quot;John Doe (john.doe@aol.com)&quot;:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
