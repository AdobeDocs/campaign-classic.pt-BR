---
title: Schemas de dados
seo-title: Schemas de dados
description: Schemas de dados
seo-description: null
page-status-flag: never-activated
uuid: 3327a38c-e44d-4581-a67b-bb60c1604a5f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: aeaa9475-3715-40a4-8864-29d126883272
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '548'
ht-degree: 100%

---


# Schemas de dados{#data-schemas}

Abaixo estão alguns princípios gerais sobre o uso de schemas de dados no Adobe Campaign.

Para saber mais sobre como criar e configurar schemas de dados no Adobe Campaign, consulte [esta seção](../../configuration/using/about-schema-edition.md).

## Estrutura de schema {#schema-structure}

O documento XML de um schema de dados deve conter o **`<srcschema>`** elemento raiz com os atributos **name** e **namespace** para preencher o nome e o namespace do schema.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

O ponto de entrada do schema é seu elemento principal. É fácil identificar porque ele tem o mesmo nome do schema e deve se originar do elemento raiz. A descrição do conteúdo começa com esse elemento.

Em um schema de gestão de conteúdo, o elemento principal é representado pela seguinte linha:

```
<element name="book" template="ncm:content" xmlChildren="true">
```

O atributo **template** digitado no elemento principal permite estender o schema com propriedades genéricas para todas as definições de conteúdo, como o nome, a data de criação, o autor, a cadeia de caracteres associada, etc.

Essas propriedades são descritas no schema **ncm:content**.

>[!NOTE]
>
>A presença do atributo **xmlChildren** indica que a estrutura de dados inserida por meio do elemento principal é armazenada em um documento XML da instância de conteúdo.

>[!CAUTION]
>
>Ao criar um novo schema ou durante uma extensão de schema, você precisa manter o mesmo valor de sequência da chave primária (@pkSequence) para todo o schema.

## Tipos de dados {#data-types}

Este é um exemplo de schema de gestão de conteúdo com os tipos preenchidos:

```
<srcSchema name="book" namespace="cus">
  <element name="book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string"/>
    <attribute name="date" type="date"/>
    <attribute name="language" type="string"/>
    <element name="chapter">
      <attribute name="name" type="string"/>
      <element name="page" type="string>
        <attribute name="number" type="short"/>
      </element>
    </element>
  </element>
</element>
```

## Propriedades {#properties}

Várias propriedades podem ser utilizadas para enriquecer os elementos **`<element>`** e **`<attribute>`** do schema de dados.

As principais propriedades utilizadas na gestão de conteúdo são as seguintes:

* **label**: descrição curta,
* **desc**: descrição longa,
* **default**: expressão que retorna um valor padrão na criação de conteúdo,
* **userEnum**: enumeração livre para armazenar e exibir os valores inseridos por meio desse campo,
* **enum**: enumeração fixa usada quando a lista de valores possíveis é conhecida antecipadamente.

Este é o nosso exemplo de schema com as propriedades preenchidas:

```
<srcSchema name="book" namespace="cus">
  <enumeration name="language" basetype="string" default="eng">    
    <value name="fra" label="French"/>    
    <value name="eng" label="English"/>   
  </enumeration>

  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string" label="Title" default="'New book'"/>
    <attribute name="date" type="date" default="GetDate()"/>
    <attribute name="language" type="string" label="Language" enum="language"/>
    <element name="chapter" label="Chapter">
      <attribute name="name" type="string" label="Name" desc="Name of chapter"/>
      <element name="page" type="string" label="Page" desc="Page content">
        <attribute name="number" type="short" label="Number" default="CounterValue('numPage')"/>
      </element>
    </element>
  </element>
</srcSchema>
```

## Elementos de coleção {#collection-elements}

Uma coleção é uma lista de elementos com o mesmo nome e o mesmo nível hierárquico.

No nosso exemplo, os itens **`<chapter>`** e **`<page>`** são elementos de coleção. Portanto, o atributo **unbound** deve ser adicionado à definição desses elementos:

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>A presença do atributo **ordered=&quot;true&quot;** permite a inserção dos elementos de coleção.

## Referência de elemento {#element-referencing}

A referência de elemento é usado em muitos schemas de conteúdo. Ela permite fatorar a definição de um elemento **`<element>`** para que ele possa ser referenciado em outros elementos com a mesma estrutura.

O atributo **ref** no elemento a ser referenciado deve ser preenchido com o caminho (XPath) do elemento de referência.

**Exemplo**: adição de uma seção do **Appendix** com a mesma estrutura do elemento **`<chapter>`** do nosso schema de exemplo.

```
<srcSchema name="book" namespace="cus">
  <element name="section">
    <attribute name="name" type="string" label="Name" desc="Name"/>
    <element name="page" type="string" label="Page" desc="Content of page">
      <attribute name="number" type="short" label="Number" default="CounterValue('numPage')"/>
    </element>

  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string" label="Title" default="'New book'"/>
    <attribute name="date" type="date" default="GetDate()"/>
    <attribute name="language" type="string" label="Language" enum="language"/>
    <element name="chapter" label="Chapter" ref="section"/>
    <element name="appendix" label="Appendix" ref="section"/>
  </element>
</srcSchema>
```

A estrutura do capítulo é movida para o elemento com o nome &quot;seção&quot; fora do elemento principal. O capítulo e a seção fazem referência ao elemento &quot;seção&quot;.

## Cálculo de cadeia de caracteres {#compute-string}

Um **Cálculo de cadeia de caracteres** é uma expressão XPath usada para criar uma cadeia de caracteres representando uma instância de conteúdo.

Aqui está nosso schema de exemplo com seu **Cálculo de cadeia de caracteres**:

```
<srcSchema name="book" namespace="cus">
  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <compute-string expr="@name"/>
    ...
  </element>
</srcSchema>
```

## Edição de schemas {#editing-schemas}

O campo de edição permite a inserção do conteúdo XML do schema de origem:

![](assets/d_ncs_integration_schema_edition.png)

Quando o schema de origem é salvo, a geração do schema estendido é iniciada automaticamente.

>[!NOTE]
>
>O controle de edição **Name** permite a inserção da chave do schema, que consiste no nome e no namespace. Os atributos **name** e **namespace** do elemento raiz do schema são atualizados automaticamente no campo de edição XML.
