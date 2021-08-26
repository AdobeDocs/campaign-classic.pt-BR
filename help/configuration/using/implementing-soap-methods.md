---
product: campaign
title: Implementação de métodos SOAP
description: Implementação de métodos SOAP
audience: configuration
content-type: reference
topic-tags: api
exl-id: 441a0e5c-fa7f-46c8-a65a-5cca4c846d43
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 4%

---

# Implementação de métodos SOAP{#implementing-soap-methods}

![](../../assets/v7-only.svg)

## Introdução {#introduction}

É possível criar métodos SOAP em JavaScript. Essa função simplesmente habilita processos aplicáveis, pode evitar o desenvolvimento de JSPs e sua chamada nos formulários.

Esses métodos SOAP se comportam da mesma forma que os definidos nativamente no aplicativo. Os mesmos atributos são suportados: estático, somente chave e const.

## Definição de uma biblioteca de métodos {#defining-a-method-library}

A criação de uma biblioteca de métodos envolve duas etapas:

* A declaração do método SOAP,
* Definição (ou implementação) no JavaScript.

### Declaração {#declaration}

Comece declarando os métodos nos schemas (para obter mais informações sobre como criar e editar schemas, consulte [esta seção](../../configuration/using/about-schema-edition.md)).

A declaração deles é semelhante à dos métodos nativos, exceto que é necessário adicionar o atributo &quot;library&quot; especificando o nome da biblioteca de métodos na qual a definição está localizada.

Esse nome coincide com o nome (com o namespace) da entidade do tipo &quot;Código JavaScript&quot;.

Exemplo:

O método testLog(msg) é declarado em uma extensão nms:recipient

```
<method name="testLog" static="true" library="cus:test">
     <parameters>
       <param name="message" type="string" inout="in"/>
     </parameters>
   </method>
```

>[!NOTE]
>
>O namespace e o nome usado para a biblioteca são independentes do namespace e do nome do schema, onde a declaração é encontrada.

### Definição {#definition}

Métodos SOAP são implementados no formato de função JavaScript agrupada em um script que representa uma biblioteca.

>[!NOTE]
>
>Uma biblioteca de métodos pode agrupar funções para vários schemas ou vice-versa, as funções de um schema podem ser definidas em bibliotecas separadas.

O script pode conter o código a ser executado durante o carregamento da biblioteca inicial.

**1. Nome**

O nome da função deve estar em conformidade com o seguinte formato:

```
 <schema-namespace>_<schema-name>_<method-name>
```

Exemplo:

A seguinte função do JavaScript é a implementação do método descrito acima. Ele deve ser definido na entidade do tipo &quot;JavaScript Code&quot; usando o nome &quot;cus:test&quot;.

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. Assinatura**

A assinatura da função deve incluir um argumento para cada parâmetro &quot;in&quot; ou &quot;inout&quot; da declaração.

Casos específicos:

* **métodos** não estáticos: a função deve incluir um argumento adicional primeiro, coincidindo com a entidade XML transmitida no formato de um objeto do tipo &#39;xml&#39; (E4X).
* **Métodos** do tipo &quot;somente chave&quot;: a função deve incluir um argumento adicional primeiro, coincidindo com a chave transmitida no formato das cadeias de caracteres.

**3. Valores retornados**

A função deve retornar um valor para cada parâmetro de tipo &quot;out&quot; ou &quot;inout&quot;. Caso específico: Se o método for declarado sem qualquer um dos atributos &#39;static&#39;, &#39;key only&#39; ou &#39;const&#39;, o primeiro valor retornado deverá coincidir com a entidade modificada. É possível retornar um novo objeto ou o primeiro parâmetro modificado.

Por exemplo:

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

Quando vários valores forem retornados, eles deverão ser exibidos em uma tabela.

Exemplo:

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```
