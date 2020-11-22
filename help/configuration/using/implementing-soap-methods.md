---
solution: Campaign Classic
product: campaign
title: Implementação de métodos SOAP
description: Implementação de métodos SOAP
audience: configuration
content-type: reference
topic-tags: api
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 4%

---


# Implementação de métodos SOAP{#implementing-soap-methods}

## Introdução {#introduction}

É possível criar métodos SOAP no JavaScript. Essa função simplesmente habilita processos aplicáveis, pode evitar o desenvolvimento de JSPs e sua chamada nos formulários.

Esses métodos SOAP se comportam da mesma forma que os definidos nativamente no aplicativo. Os mesmos atributos são suportados: estático, apenas chave e const.

## Definição de uma biblioteca de métodos {#defining-a-method-library}

A criação de uma biblioteca de métodos envolve duas etapas:

* A declaração do método SOAP,
* Definição (ou implementação) em JavaScript.

### Declaração {#declaration}

Start declarando os métodos nos schemas (para obter mais informações sobre como criar e editar schemas, consulte [esta seção](../../configuration/using/about-schema-edition.md)).

A declaração é semelhante à dos métodos nativos, exceto que é necessário adicionar o atributo &#39;library&#39; especificando o nome da biblioteca de métodos na qual a definição está localizada.

Esse nome coincide com o nome (com a namespace) da entidade do tipo &#39;Código JavaScript&#39;.

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
>A namespace e o nome usados para a biblioteca são independentes do nome da namespace e do schema onde a declaração é encontrada.

### Definição {#definition}

Métodos SOAP são implementados na forma da função JavaScript agrupados em um script que representa uma biblioteca.

>[!NOTE]
>
>Uma biblioteca de métodos pode agrupar funções para vários schemas ou vice-versa, as funções de um schema podem ser definidas em bibliotecas separadas.

O script pode conter o código a ser executado durante o carregamento inicial da biblioteca.

**1. Nome**

O nome da função deve estar em conformidade com o seguinte formato:

```
 <schema-namespace>_<schema-name>_<method-name>
```

Exemplo:

A seguinte função JavaScript é a implementação do método descrito acima. Ela será definida na entidade do tipo &quot;Código JavaScript&quot; usando o nome &quot;cus:test&quot;.

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. Assinatura**

A assinatura da função deve incluir um argumento para cada parâmetro &quot;in&quot; ou &quot;inout&quot; da declaração.

Casos específicos:

* **métodos** não estáticos: a função deve incluir um argumento adicional primeiro, coincidindo com a entidade XML transmitida na forma de um objeto do tipo &#39;xml&#39; (E4X).
* **Métodos** do tipo &quot;chave somente&quot;: a função deve incluir um argumento adicional primeiro, coincidindo com a chave transmitida na forma de strings de caracteres.

**3. Valores retornados**

A função deve retornar um valor para cada parâmetro do tipo &quot;out&quot; ou &quot;inout&quot;. Caso específico: Se o método for declarado sem nenhum dos atributos &#39;static&#39;, &#39;key only&#39; ou &#39;const&#39;, o primeiro valor retornado deverá coincidir com a entidade modificada. É possível retornar um novo objeto ou retornar o primeiro parâmetro modificado.

Por exemplo:

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

Quando vários valores devem ser retornados, eles devem ser exibidos em uma tabela.

Exemplo:

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```

