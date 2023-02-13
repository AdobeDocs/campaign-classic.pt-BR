---
product: campaign
title: Elementos e atributos do schema - elemento-chave
description: elemento principal
exl-id: 3d0ef574-27a3-40f2-91a0-70e9583d9980
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 8%

---

# elemento principal {#key--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-8}

tecla:==keyfield

## Atributos {#attributes-8}

* @allowEmptyPart (booleano)
* @applicableIf (cadeia de caracteres)
* @internal (booleano)
* @label (cadeia de caracteres)
* @name (MNTOKEN)
* @noDbIndex (booleano)

## Pais {#parents-8}

`<element>`

## Filhos {#children-8}

`<keyfield>`

## Descrição {#description-8}

Esse elemento permite definir uma chave para identificar um registro na tabela.

Uma tabela deve ter pelo menos uma chave.

## Uso e contexto de uso {#use-and-context-of-use-6}

Como regra, as chaves são declaradas após o elemento principal do esquema e os índices.

Uma chave é conhecida como composta se incluir vários campos (ou seja, vários `<keyfield>` crianças). Não use uma chave composta para definir uma chave primária.

Se o elemento principal do schema contiver o atributo &quot;@autopk=true&quot;, a chave primária será exclusiva. Só podemos ter uma chave primária por esquema.

Os primeiros 1000 identificadores são reservados, portanto, se uma faixa de valores precisar ser definida para chaves, comece em 1000.

## Descrição do atributo {#attribute-description-8}

* **allowEmptyPart (booleano)**: no caso de uma chave composta, se esse atributo estiver ativado, a chave será considerada válida se pelo menos uma de suas chaves não estiver vazia. Se esse for o caso, o valor vazio da noção é &quot;0&quot; (booleano ou para todos os tipos de dados numéricos). Por padrão, todas as chaves que compõem uma chave composta precisam ser inseridas.
* **applicableIf (cadeia de caracteres)**: esse atributo permite tornar a chave opcional. Ela define a condição de acordo com a qual a definição de chave será aplicada. Esse atributo recebe uma expressão XTK.
* **interno (booleano)**: se estiver ativado, esse atributo informará o Adobe Campaign que a chave é primária.
* **label (string)**: da chave.
* **name (MNTOKEN)**: nome interno da chave.
* **noDbIndex (booleano)**: se estiver ativado (noDbIndex=&quot;true&quot;), o campo correspondente à chave não será indexado.

## Exemplos {#examples-------}

Declaração de uma chave composta que autoriza o campo &quot;@expr&quot; ou &quot;alias&quot; a ficar vazio:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Declaração de uma chave primária no campo &quot;Nome&quot; do tipo STRING em um `<srcschema>`  e a consulta SQL correspondente:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
