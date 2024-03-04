---
product: campaign
title: Mapeamento de banco de dados
description: Mapeamento de banco de dados
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
source-git-commit: f03e72d4ecd17446264adf74603aefca95f99d41
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 1%

---


# Gerenciamento de links {#links--relation-between-tables}

Um link descreve a associação entre uma tabela e outra.

Tipos de associações, também conhecidas como cardinalidades, estão listadas abaixo.

* Cardinalidade 1-1: uma ocorrência da tabela de origem pode ter no máximo uma ocorrência correspondente da tabela de destino.
* Cardinalidade 1-N: uma ocorrência da tabela de origem pode ter várias ocorrências correspondentes da tabela de destino, mas uma ocorrência da tabela de destino pode ter no máximo uma ocorrência correspondente da tabela de origem.
* Cardinalidade N-N: uma ocorrência da tabela de origem pode ter várias ocorrências correspondentes da tabela de destino e vice-versa.

Na interface de uso, as cardinalidades são representadas com um ícone específico.

Para relações de join com uma tabela/banco de dados de campanha:

* ![](assets/join_with_campaign11.png) : Cardinalidade 1-1. Por exemplo, entre um recipient e um pedido atual. Um recipient pode ser relacionado a apenas uma ocorrência da tabela de pedidos atual por vez.
* ![](assets/externaljoin11.png) : Cardinalidade 1-1, junção externa. Por exemplo, entre um recipient e seu país. Um recipient pode ser relacionado a apenas uma ocorrência do país da tabela. O conteúdo da tabela do país não será salvo.
* ![](assets/join_with_campaign1n.png) : Cardinalidade 1-N. Por exemplo, entre um recipient e a tabela de subscrições. Um recipient pode ser relacionado a várias ocorrências na tabela de assinaturas.

Para relações de join usando o Federated Database Access (FDA):

* ![](assets/join_fda_11.png) : Cardinalidade 1-1
* ![](assets/join_fda_1m.png) : Cardinalidade 1-N

Para obter mais informações sobre tabelas FDA, consulte [Acesso a um banco de dados externo](../../installation/using/about-fda.md).

Um link deve ser declarado no schema que contém a chave externa da tabela vinculada por meio do elemento principal:

```sql
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

Os links obedecem às seguintes regras:

* A definição de um link é inserida em um **link**-type **`<element>`** com os seguintes atributos:

   * **name**: nome do link da tabela de origem
   * **público alvo**: nome do schema de destino
   * **rótulo**: rótulo do link
   * **revLink** (opcional): nome do link reverso do schema de destino (deduzido automaticamente por padrão)
   * **integridade** (opcional): integridade referencial da ocorrência da tabela de origem à ocorrência da tabela de destino.
Os valores possíveis são:

      * **definir**: é possível excluir a ocorrência de origem se ela não for mais referenciada por uma ocorrência de destino
      * **normal**: ao excluir a ocorrência de origem inicializa as chaves do link para a ocorrência de destino (modo padrão), esse tipo de integridade inicializa todas as chaves estrangeiras
      * **próprio**: excluir a ocorrência de origem leva à exclusão da ocorrência de destino
      * **owncopy**: o mesmo que **próprio** (em caso de exclusão) ou duplica as ocorrências (em caso de duplicação)
      * **neutro**: nenhum comportamento específico

   * **revIntegrity** (opcional): integridade no schema do target (opcional, &quot;normal&quot; por padrão)
   * **revCardinality** (opcional): com o valor &quot;único&quot;, preenche cardinalidade com tipo 1-1 (1-N por padrão)
   * **externalJoin** (opcional): força a junção externa
   * **revExternalJoin** (opcional): força a junção externa no link reverso

* Um link faz referência a um ou mais campos da tabela de origem para a tabela de destino. Os campos que compõem a associação ( `<join>`  element) não precisam ser preenchidos porque são automaticamente deduzidos por padrão usando a chave interna do schema de público-alvo.
* Um índice é adicionado automaticamente à chave externa do link no schema estendido.
* Um link consiste em dois semilinks, em que o primeiro é declarado do esquema de origem e o segundo é criado automaticamente no esquema estendido do esquema de destino.
* Uma associação pode ser uma associação externa se a variável **externalJoin** é adicionado, com o valor &quot;true&quot; (compatível com PostgreSQL).

>[!NOTE]
>
>Como padrão, os links são os elementos declarados no final do schema.

## Exemplo: link reverso {#example-1}

No exemplo abaixo, declaramos uma relação 1-N para a tabela de schema &quot;cus:company&quot;:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

O schema gerado:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>
    ...
    <element label="Company" name="company" revLink="recipient" target="cus:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Company' link (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

A definição do link é complementada pelos campos que compõem a junção, ou seja, a chave primária com seu XPath (&quot;@id&quot;) no esquema de destino e a chave externa com seu XPath (&quot;@company-id&quot;) no esquema.

A chave estrangeira é adicionada automaticamente em um elemento que usa as mesmas características do campo associado na tabela de destino, com a seguinte convenção de nomenclatura: nome do esquema de destino seguido do nome do campo associado (&quot;company-id&quot; no nosso exemplo).

Esquema estendido do target (&quot;cus:company&quot;):

```sql
<schema mappingType="sql" name="company" namespace="cus" xtkschema="xtk:schema">  
  <element name="company" sqltable="CusCompany" autopk="true"> 
    <dbindex name="id" unique="true">     
      <keyfield xpath="@id"/>    
    </dbindex>   
    <key internal="true" name="id">      
      <keyfield xpath="@id"/>    
    </key>
    ...
    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iCompanyId" type="long"/>
    ...
    <element belongsTo="cus:recipient" integrity="define" label="Contact" name="recipient" revLink="company" target="nms:recipient" type="link" unbound="true">      
      <join xpath-dst="@company-id" xpath-src="@id"/>    
    </element>
  </element>
</schema>
```

Um link reverso para a tabela &quot;cus:recipient&quot; foi adicionado com os seguintes parâmetros:

* **name**: deduzido automaticamente do nome do schema de origem (pode ser forçado com o atributo &quot;revLink&quot; na definição do link no schema de origem)
* **revLink**: nome do link reverso
* **público alvo**: chave do schema vinculado (schema &quot;cus:recipient&quot;)
* **desvinculado**: o link é declarado como um elemento de coleção para uma cardinalidade 1-N (por padrão)
* **integridade**: &quot;define&quot; por padrão (pode ser forçado com o atributo &quot;revIntegrity&quot; na definição do link no esquema de origem).

## Exemplo: link simples {#example-2}

Neste exemplo, declaramos um link para a tabela de schema &quot;nms:address&quot;. A associação é uma associação externa e é preenchida explicitamente com o endereço de email do recipient e o campo &quot;@address&quot; da tabela vinculada (&quot;nms:address&quot;).

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient"> 
    ...
    <element integrity="neutral" label="Info about email" name="emailInfo" revIntegrity="neutral" revLink="recipient" target="nms:address" type="link" externalJoin="true">      
      <join xpath-dst="@address" xpath-src="@email"/>
    </element>
  </element>
</srcSchema>
```

## Exemplo: cardinalidade exclusiva {#example-3}

Neste exemplo, criamos uma relação 1-1 para a tabela de schema &quot;cus:extension&quot;:

```sql
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

## Exemplo: link para uma pasta {#example-4}

Neste exemplo, declaramos um link para uma pasta (schema &quot;xtk:folder&quot;):

```sql
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

O valor padrão retorna o identificador do primeiro arquivo de tipo de parâmetro elegível inserido na função &quot;DefaultFolder(&#39;nmsFolder&#39;)&quot;.

## Exemplo: criar uma chave em um link {#example-5}

Neste exemplo, criamos uma chave em um link (&quot;company&quot; para &quot;cus:company&quot; schema) com a variável **xlink** e um campo da tabela (&quot;email&quot;):

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <key name="companyEmail"> 
      <keyfield xpath="@email"/>
      <keyfield xlink="company"/>
    </key>
    
    <attribute name="email" type="string" length="80" label="Email" desc="Recipient email"/>
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

O schema gerado:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>

    <dbindex name="companyEmail" unique="true">
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </dbindex>    

    <key name="companyEmail">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </key>

    <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

A definição da chave de nome &quot;companyEmail&quot; foi estendida com a chave externa do link &quot;company&quot;. Essa chave gera um índice exclusivo em ambos os campos.
