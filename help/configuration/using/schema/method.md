---
solution: Campaign Classic
product: campaign
title: Elementos e atributos
description: Elementos e atributos
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 3%

---


# elemento de método {#method--element}

## Modelo de conteúdo {#content-model-10}

método:==( help | parâmetros)

## Atributos {#attributes-10}

* @_operation (string)
* @access (string)
* @const (booleano)
* @hidden (booleano)
* @label (string)
* @library (string)
* @name (MNTOKEN)
* @pkonly (booleano)
* @static (booleano)

## Pais {#parents-10}

`<methods>`  ,  `<interface />`

## Filhos {#children-10}

* `<help>`
* `<parameters>`

## Descrição {#description-10}

Esse elemento permite definir um método SOAP.

## Uso e contexto de uso {#use-and-context-of-use-7}

Métodos SOAP habilitam processos de aplicativo.

A &quot;@library&quot; é necessária para declarar um novo método (não nativo): a namespace e o nome usados para a biblioteca são independentes da namespace e do nome do schema onde está a declaração.

## Descrição do atributo {#attribute-description-10}

* **access (string)**: esse atributo define o controle de acesso para o uso do método. Se este atributo estiver faltando, a identificação é obrigatória. Os valores disponíveis são: &quot;anônimo&quot;, &quot;admin&quot; e &quot;sql&quot;.
* **const (booleano)**: se estiver ativado, este atributo significa que o método declarado alterará a entidade
* **label (string)**: rótulo do método.
* **biblioteca (string)**: esse método não é nativo do aplicativo. Esse atributo obtém o valor da biblioteca de métodos na qual a definição do método é encontrada (nms:mylibrary.js).
* **name (MNTOKEN)**: nome do método exclusivo.
* **estático (booleano)**: se esse atributo estiver ativado, o método for considerado autônomo, todos os parâmetros deverão ser especificados para o método quando ele for chamado.

## Exemplos {#examples-7}

Definição do método &quot;Assinar&quot; na caixa:

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
