---
product: campaign
title: Elementos e atributos - elemento compute-string
description: elemento compute-string
feature: Schema Extension
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
TQID: https://experienceleague.adobe.com/vLSA9oDdBg-0sElc6QlusY-YviNyRU8Fq6yXRrFrN1g
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 95
ht-degree: 5%

---

# elemento compute-string {#compute-string--element}


## Modelo de conteúdo {#content-model-1}

string de cálculo:==EMPTY

## Atributos {#attributes-1}

@expr

## Pais {#parents-1}

`<element>`

## Filhos {#children-1}

nenhuma

## Descrição {#description-1}

O elemento `<compute-string>` permite gerar uma cadeia de caracteres com base em uma expressão XTK para exibir um rótulo &quot;criado&quot; na interface com base em vários valores.

## Uso e contexto de uso {#use-and-context-of-use-1}

Quando nenhum `<compute-string>` é definido, um elemento `<compute-string>` é inserido por padrão com os valores da chave primária no esquema.

## Descrição do atributo {#attribute-description-1}

* **expr (cadeia de caracteres)**: expressão XTK e/ou Xpath

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
