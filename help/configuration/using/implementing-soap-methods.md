---
product: campaign
title: Implementação de métodos SOAP
description: Implementação de métodos SOAP
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 441a0e5c-fa7f-46c8-a65a-5cca4c846d43
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 4%

---

# Implementar métodos SOAP{#implementing-soap-methods}



## Introdução {#introduction}

É possível criar métodos SOAP em JavaScript. Essa função simplesmente habilita processos aplicativos, pode evitar o desenvolvimento de JSPs e sua chamada nos formulários.

Esses métodos SOAP se comportam da mesma forma que os definidos nativamente no aplicativo. Os mesmos atributos são suportados: static, key only e const.

## Definir uma biblioteca de métodos {#defining-a-method-library}

A criação de uma biblioteca de métodos envolve dois estágios:

* A declaração do método SOAP,
* Definição (ou implementação) em JavaScript.

### Declaração {#declaration}

Comece declarando os métodos nos schemas (para obter mais informações sobre como criar e editar schemas, consulte [nesta seção](../../configuration/using/about-schema-edition.md)).

A declaração deles é semelhante à dos métodos nativos, exceto que é necessário adicionar o atributo &quot;biblioteca&quot; especificando o nome da biblioteca de métodos onde a definição está localizada.

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
>O namespace e o nome usado para a biblioteca são independentes do namespace e do nome do esquema em que a declaração é encontrada.

### Definição {#definition}

Os métodos SOAP são implementados na forma de função JavaScript agrupada em um script que representa uma biblioteca.

>[!NOTE]
>
>Uma biblioteca de métodos pode agrupar funções para vários esquemas, ou vice-versa. As funções de um esquema podem ser definidas em bibliotecas separadas.

O script pode conter código a ser executado durante o carregamento inicial da biblioteca.

**1. Nome**

O nome da função deve estar em conformidade com o seguinte formato:

```
 <schema-namespace>_<schema-name>_<method-name>
```

Exemplo:

A seguinte função do JavaScript é a implementação do método descrito acima. Deve ser definida na entidade de tipo &quot;JavaScript Code&quot; utilizando o nome &quot;cus:test&quot;.

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. Assinatura**

A assinatura da função deve incluir um argumento para cada parâmetro &#39;in&#39; ou &#39;inout&#39; da declaração.

Casos específicos:

* **métodos não estáticos**: a função deve incluir um argumento adicional primeiro, coincidindo com a entidade XML transmitida na forma de um objeto de tipo &quot;xml&quot; (E4X).
* **métodos do tipo &quot;somente chave&quot;**: a função deve incluir um argumento adicional primeiro, coincidindo com a chave transmitida na forma de cadeias de caracteres.

**3. Valores retornados**

A função deve retornar um valor para cada parâmetro de tipo &#39;out&#39; ou &#39;inout&#39;. Caso específico: se o método for declarado sem nenhum dos atributos &quot;static&quot;, &quot;key only&quot; ou &quot;const&quot;, o primeiro valor retornado deverá coincidir com a entidade modificada. É possível retornar um novo objeto ou retornar o primeiro parâmetro modificado.

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
