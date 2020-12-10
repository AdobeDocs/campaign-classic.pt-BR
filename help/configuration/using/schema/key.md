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
source-wordcount: '316'
ht-degree: 2%

---


# `<key>` direcionado {#key--element}

## Modelo de conteúdo {#content-model-8}

key:==keyfield

## Atributos {#attributes-8}

* @allowEmptyPart (booleano)
* @applyIf (string)
* @internal (booleano)
* @label (string)
* @name (MNTOKEN)
* @noDbIndex (booleano)

## Pais {#parents-8}

`<element>`

## Filhos {#children-8}

`<keyfield>`

## Descrição {#description-8}

Esse elemento permite que você defina uma chave para identificar um registro na tabela.

Uma tabela deve ter pelo menos uma chave.

## Uso e contexto de uso {#use-and-context-of-use-6}

Como regra, as chaves são declaradas após o elemento principal do schema e os índices.

Uma chave é conhecida como composta se incluir vários campos (ou seja, vários `<keyfield>` filhos). Não use uma chave composta para definir uma chave primária.

Se o elemento principal do schema contiver o atributo &quot;@autopk=true&quot;, a chave primária será exclusiva. Só podemos ter uma chave primária por schema.

Os primeiros 1000 identificadores são reservados, portanto, se uma faixa de valores precisar ser definida para chaves, start em 1000.

## Descrição do atributo {#attribute-description-8}

* **allowEmptyPart (booleano)**: no caso de uma chave composta, se esse atributo estiver ativado, a chave será considerada válida se pelo menos uma de suas chaves não estiver vazia. Se esse for o caso, o valor vazio da noção é &quot;0&quot; (booleano ou para todos os tipos de dados numéricos). Por padrão, todas as teclas que compõem uma chave composta precisam ser inseridas.
* **applyIf (string)**: esse atributo permite tornar a chave opcional. Define a condição de acordo com a qual a definição de chave será aplicada. Este atributo recebe uma expressão XTK.
* **interno (booleano)**: se estiver ativado, esse atributo informará a Adobe Campaign que a chave é primária.
* **label (string)**: rótulo da chave.
* **name (MNTOKEN)**: nome interno da chave.
* **noDbIndex (booleano)**: se estiver ativado (noDbIndex=&quot;true&quot;), o campo que corresponde à chave não será indexado.

## Exemplos {#examples-------}

Declaração de uma chave composta que autoriza que o campo &quot;@expr&quot; ou &quot;alias&quot; esteja vazio:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Declaração de uma chave primária no campo &quot;Nome&quot; do tipo STRING em `<srcschema>` e o query SQL correspondente:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
