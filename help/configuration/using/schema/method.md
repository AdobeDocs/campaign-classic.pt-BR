---
product: campaign
title: Elementos e atributos de esquema - elemento de método
description: elemento do método
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 1%

---

# elemento do método {#method--element}

![](../../../assets/v7-only.svg)

## Modelo de conteúdo {#content-model-10}

método:==( ajuda) | parâmetros)

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

Os métodos SOAP habilitam processos de aplicativo.

O &quot;@library&quot; é necessário para declarar um novo método (não nativo): o namespace e o nome usados para a biblioteca são independentes do namespace e do nome do schema em que a declaração é.

## Descrição do atributo {#attribute-description-10}

* **acesso (string)**: este atributo define o controle de acesso para usar o método. Se este atributo estiver ausente, a identificação é obrigatória. Os valores disponíveis são: &#39;anonymous&#39;, &#39;admin&#39; e &#39;sql&#39;.
* **const (booleano)**: se estiver ativado, esse atributo significa que o método declarado alterará a entidade
* **rótulo (string)**: rótulo do método.
* **biblioteca (sequência de caracteres)**: este método não é nativo do aplicativo. Esse atributo pega o valor da biblioteca de métodos onde a definição de método é encontrada (nms:mylibrary.js).
* **nome (MNTOKEN)**: nome de método exclusivo.
* **estático (booleano)**: se esse atributo for ativado, o método será considerado autônomo. Todos os parâmetros devem ser especificados para o método quando ele for chamado.

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
