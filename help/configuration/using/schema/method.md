---
product: campaign
title: Elementos e atributos
description: Elementos e atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 3%

---

# elemento de método {#method--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-10}

método:==( help | parâmetros)

## Atributos {#attributes-10}

* @_operation (cadeia de caracteres)
* @access (cadeia de caracteres)
* @const (booleano)
* @hidden (boolean)
* @label (cadeia de caracteres)
* @library (cadeia de caracteres)
* @name (MNTOKEN)
* @pkonly (booleano)
* @static (booleano)

## Pais {#parents-10}

`<methods>`  ,  `<interface />`

## Crianças {#children-10}

* `<help>`
* `<parameters>`

## Descrição {#description-10}

Esse elemento permite definir um método SOAP.

## Uso e contexto de uso {#use-and-context-of-use-7}

Métodos SOAP habilitam processos de aplicativo.

A &quot;@library&quot; é necessária para declarar um novo método (não nativo): o namespace e o nome usado para a biblioteca são independentes do namespace e do nome do schema em que a declaração está.

## Descrição do atributo {#attribute-description-10}

* **access (string)**: esse atributo define o controle de acesso para usar o método . Se este atributo estiver faltando, a identificação é obrigatória. Os valores disponíveis são: &#39;anonymous&#39;, &#39;admin&#39; e &#39;sql&#39;.
* **const (booleano)**: se estiver ativado, esse atributo significa que o método declarado alterará a entidade
* **label (string)**: rótulo do método.
* **biblioteca (string)**: esse método não é nativo do aplicativo. Esse atributo usa o valor da biblioteca de métodos, onde a definição do método é encontrada (nms:mylibrary.js).
* **nome (MNTOKEN)**: nome exclusivo do método.
* **estático (booleano)**: se este atributo estiver ativado, o método é considerado autônomo, todos os parâmetros devem ser especificados para o método quando for chamado.

## Exemplos {#examples-7}

Definição do método &quot;Subscribe&quot; pronto para uso:

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>
```
