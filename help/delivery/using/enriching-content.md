---
title: Enriquecimento de conteúdo
seo-title: Enriquecimento de conteúdo
description: Enriquecimento de conteúdo
seo-description: null
page-status-flag: never-activated
uuid: 6f1bce9f-88ed-4ad3-987f-79f6c68264d2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: 4404c21e-0a89-4762-af20-384ad7071916
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Enriquecimento de conteúdo{#enriching-content}

Agregadores permitem enriquecer o conteúdo com dados externos. Esses dados vêm de queries genéricos ou tabelas vinculadas.

## Queries genéricos {#generic-queries}

Queries are configured via the publication template in the **[!UICONTROL Aggregator]** tab.

Os dados recuperados enriquecem o documento de saída XML por meio de seu elemento principal.

Exemplo de retorno de um query no schema do recipient (**nms:recipient**):

```
<book name="Content Management">
  ...
  <collection-recipient>
    <recipient lastName="Doe" firstName="John" email="john.doe@aolf.com">
    ...
  </collection-recipient>
</book>
```

The **`<collection-recipient>`** element represents the input element of the document resulting from a query. Os dados recuperados são retornados sob este elemento; em nosso exemplo, uma lista de recipients.

### Adição de um query {#adding-a-query}

Os parâmetros de query são editados por um assistente.

1. Na primeira página, especifique o rótulo e o schema que contém os dados a serem recuperados.

   ![](assets/d_ncs_content_query1.png)

   >[!NOTE]
   >
   >O campo de edição **Caminho** é usado para renomear o elemento de saída do query.

1. A próxima página permite que você selecione os dados a serem recuperados.

   ![](assets/d_ncs_content_query2.png)

1. A próxima página define a condição do filtro.

   ![](assets/d_ncs_content_query3.png)

1. A última página inicia uma pré-visualização dos dados retornados pelo query.

   ![](assets/d_ncs_content_query4.png)

## Tabelas vinculadas {#linked-tables}

Os links permitem recuperar dados externos vinculados ao conteúdo.

Existem dois tipos de dados vinculados:

* Links de conteúdo: esse é o modo de gestão de conteúdo nativo. O conteúdo do link é automaticamente integrado no documento de saída XML.
* Links para tabelas externas dão acesso a todas as outras tabelas do banco de dados com a restrição de recuperar os dados do link selecionado com um agregador.

### Link para um schema de conteúdo {#link-to-a-content-schema}

Um link de conteúdo é declarado no schema de dados da seguinte maneira:

```
<element expandSchemaTarget="cus:chapter" label="Main chapter" name="mainChapter" type="string"/>
```

The definition of the link is populated on a **string**-type **`<element>`**, and the **expandSchemaTarget** attribute references the target schema (&quot;cus:chapter&quot; in our example). O schema referenciado deve ser um schema de conteúdo.

The content of the targeted element enriches the link element, i.e. the **`<chapter>`** element in our example schema:

```
<mainChapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</mainChapter>
```

>[!NOTE]
>
>A **Cálculo de cadeia de caracteres** do link é apresentada a partir do atributo **computeString**.

No formulário de entrada, o controle de edição do link é declarado da seguinte maneira:

```
<input type="articleEdit" xpath="mainChapter"/>
```

![](assets/d_ncs_content_link.png)

The **[!UICONTROL Magnifier]** icon enables you to open the edit form of the linked element.

#### Coleção de links {#link-collection}

Para preencher uma coleção de links, adicione o atributo **unbound=&quot;true&quot;** à definição do elemento do link no schema de dados:

```
<element expandSchemaTarget="cus:chapter" label="List of chapters" name="chapter"  ordered="true" unbound="true"/>
```

O conteúdo do elemento direcionado enriquece cada elemento de coleta:

```
<chapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</chapter>
```

No formulário de entrada, o controle de lista é declarado da seguinte maneira:

```
<input editable="false" nolabel="true" toolbarCaption="List of chapters" type="articleList" xpath="chapter" zoom="true"/>
```

![](assets/d_ncs_content_link2.png)

Uma coluna padrão é exibida para mostrar a **Cálculo de cadeia de caracteres** dos elementos pretendidos.

### Links para tabelas externas {#links-to-external-tables}

Um link para uma tabela externa é declarado no schema de dados da seguinte maneira:

```
<element label="Main contact" name="mainContact" target="nms:recipient" type="link"/>
```

The definition of the link is populated on a **link**-type **`<element>`**, and the **target** attribute references the target schema (&quot;nms:recipient&quot; in our example).

Por convenção, os links devem ser declarados do elemento principal do schema de dados.

The **Compute string** and the key of the targeted element enrich the **`<name>-id`** and **`<name>-cs`** attributes on the main element.

No nosso exemplo, o link é preenchido no schema &quot;cus:book&quot;, o conteúdo dos dados do link está contido nos atributos &quot;mainContact-id&quot; e &quot;mainContact-cs&quot;:

```
<book computeString="Content management" date="2006/06/08" id="6106" language="en" mainContact-cs="John Doe (john.doe@adobe.com)" mainContact-id="3012" name="Content management" xtkschema="cus:book">
```

O controle de edição de link é declarado da seguinte maneira:

```
<input xpath="mainContact"/>
```

![](assets/d_ncs_content_link3.png)

You can restrict the choice of target elements by adding the **`<sysfilter>`** element via the link definition in the input form:

```
<input xpath="mainContact">
  <!-- Filter the selection of the link on the Adobe domain -->
  <sysFilter>
    <condition expr="@domain =  'adobe.com '"/>
  </sysFilter>
</input>
```

>[!NOTE]
>
>Essa restrição também se aplica aos links de conteúdo.

#### Coleção de links {#link-collection-1}

A definição da coleção é idêntica à definição de uma lista em elementos de coleção:

```
<element label="List of contacts" name="contact" unbound="true">
  <element label="Recipient" name="recipient" target="nms:recipient" type="link"/>
</element>
```

No formulário de entrada, o controle de lista é declarado da seguinte maneira:

```
<input nolabel="true" toolbarCaption="List of contacts" type="list" xpath="contact">
  <input xpath="recipient"/>
</input>
```

![](assets/d_ncs_content_link4.png)

>[!NOTE]
>
>A lista é editável e permite selecionar o link de um controle de tipo &quot;link&quot; apresentado acima.

O conteúdo do elemento target enriquece cada elemento de coleção no documento de saída:

```
<contact id="11504978621" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>
<contact id="11504982510" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/>
```

#### Agregação de links {#link-aggregation}

O conteúdo de cada link referenciado é limitado à chave interna e ao elemento pretendido do **Cálculo de cadeia de caracteres**.

Um script JavaScript é usado para enriquecer o conteúdo dos links por queries SOAP.

**Exemplo**: Adicionar o nome do destinatário ao link &quot;mainContact&quot; e aos links da coleção &quot;contact&quot;:

```
// Update <mainContact> link
var mainContactId = content.@['mainContact-id']
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="get">
      <select>
        <node expr="@lastName"/>
      </select>
      <where>
        <condition expr={"@id="+mainContactId}/>
      </where>
    </queryDef>)

var recipient = query.ExecuteQuery()
content.mainContact.@lastName = recipient.@lastName

// Update <contact> link collection
for each(var contact in content.contact)
{
  var contactId = contact.@['recipient-id']
  var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="get">
      <select>
        <node expr="@lastName"/>
      </select>
      <where>
        <condition expr={"@id="+contactId}/>
      </where>
    </queryDef>
  )
  
  var recipient = query.ExecuteQuery()
  contact.@lastName = recipient.@lastName
}
```

O resultado obtido após a execução do script:

```
<mainContact lastName="Doe"/>

<contact id="11504978621" lastName="Doe" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>  
<contact id="11504982510" lastName="Martinez" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/> 
```

The content of the JavaScript code is added via the **[!UICONTROL Administration > Configuration > Content management > JavaScript Codes]** folder and must be populated in the publication template for each transformation.

![](assets/d_ncs_content_link5.png)

