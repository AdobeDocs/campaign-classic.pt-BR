---
product: campaign
title: Mapeamento de banco de dados
description: Mapeamento de banco de dados
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: 4a29c189e1e438bbb90067ece63ced0196c618ec
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 5%

---

# Mapeamento de banco de dados{#database-mapping}

O mapeamento SQL do schema de amostra descrito [nesta página](schema-structure.md) gera o seguinte documento XML:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient email address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

O elemento raiz do esquema foi alterado para **`<srcschema>`** para **`<schema>`**.

Esse outro tipo de documento é gerado automaticamente a partir do schema de origem e chamado simplesmente de schema.

Os nomes SQL são determinados automaticamente com base no nome e no tipo do elemento.

As regras de nomenclatura SQL são as seguintes:

* **tabela**: concatenação do namespace e do nome do schema

  No nosso exemplo, o nome da tabela é inserido por meio do elemento principal do schema na **sqltable** atributo:

  ```sql
  <element name="recipient" sqltable="CusRecipient">
  ```

* **campo**: nome do elemento precedido por um prefixo definido de acordo com o tipo: &#39;i&#39; para inteiro, &#39;d&#39; para duplo, &#39;s&#39; para cadeia de caracteres, &#39;ts&#39; para datas, etc.

  O nome do campo é inserido por meio da variável **sqlname** atributo para cada tipo **`<attribute>`** e **`<element>`**:

  ```sql
  <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
  ```

>[!NOTE]
>
>Os nomes SQL podem ser sobrecarregados do esquema de origem. Para fazer isso, preencha os atributos &quot;sqltable&quot; ou &quot;sqlname&quot; no elemento relacionado.

O script SQL para criar a tabela gerada a partir do schema estendido é o seguinte:

```sql
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

As restrições do campo SQL são as seguintes:

* nenhum valor nulo em campos numéricos e de data
* campos numéricos são inicializados como 0

## Campos XML {#xml-fields}

Por padrão, qualquer  **`<attribute>`** e **`<element>`** O elemento do tipo é mapeado em um campo SQL da tabela de esquema de dados. No entanto, você pode fazer referência a esse campo em XML, em vez de SQL, o que significa que os dados são armazenados em um campo de memorando (&quot;mData&quot;) da tabela que contém os valores de todos os campos XML. O armazenamento desses dados é um documento XML que observa a estrutura do schema.

Para preencher um campo em XML, é necessário adicionar o **xml** com o valor &quot;true&quot; ao elemento em questão.

**Exemplo**: estes são dois exemplos de uso de campo XML.

* Campo de comentário multilinha:

  ```sql
  <element name="comment" xml="true" type="memo" label="Comment"/>
  ```

* Descrição dos dados em formato HTML:

  ```sql
  <element name="description" xml="true" type="html" label="Description"/>
  ```

  O tipo &quot;html&quot; permite armazenar o conteúdo do HTML em uma tag CDATA e exibir uma verificação de edição de HTML especial na interface do cliente do Adobe Campaign.

Use campos XML para adicionar novos campos sem modificar a estrutura física do banco de dados. Outra vantagem é que você usa menos recursos (tamanho alocado para campos SQL, limite do número de campos por tabela etc.). No entanto, observe que não é possível indexar ou filtrar um campo XML.

## Campos indexados {#indexed-fields}

Os índices permitem otimizar o desempenho das consultas SQL usadas na aplicação.

Um índice é declarado pelo elemento principal do schema de dados.

```sql
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Os índices obedecem às seguintes regras:

* Um índice pode fazer referência a um ou mais campos na tabela
* Um índice pode ser exclusivo (para evitar duplicatas) em todos os campos se a variável **único** o atributo contém o valor &quot;true&quot;
* O nome SQL do índice é determinado pelo nome SQL da tabela e pelo nome do índice

>[!NOTE]
>
>* Como padrão, os índices são os primeiros elementos declarados do elemento principal do esquema.
>
>* Os índices são criados automaticamente durante o mapeamento de tabela (padrão ou FDA).

**Exemplo**:

* Adicionar um índice ao endereço de email e à cidade:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </dbindex>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

* Adicionar um índice exclusivo ao campo de nome &quot;id&quot;:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="id" unique="true">
        <keyfield xpath="@id"/> 
      </dbindex>
  
      <dbindex name="email">
        <keyfield xpath="@email"/> 
      </dbindex>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

## Saiba mais

Navegue pelos links a seguir para saber mais:

* [Introdução a esquemas](about-schema-reference.md)
* [Estrutura de esquema](schema-structure.md)
* [Gerenciamento de chaves](database-keys.md)
* [Gerenciamento de link](database-links.md)
* [Modelo de dados do Campaign](about-data-model.md)