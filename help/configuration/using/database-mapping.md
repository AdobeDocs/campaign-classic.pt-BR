---
title: Mapeamento de banco de dados
seo-title: Mapeamento de banco de dados
description: Mapeamento de banco de dados
seo-description: null
page-status-flag: never-activated
uuid: a51df3eb-cae6-4e8d-8386-d62defc1b610
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: bc06c00d-f421-452e-bde0-b4ecc12c72c8
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1976'
ht-degree: 1%

---


# Mapeamento de banco de dados{#database-mapping}

O mapeamento SQL do nosso schema de exemplo fornece o seguinte documento XML:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient e-mail address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

## Descrição {#description}

O elemento raiz do schema não é mais **`<srcschema>`**, mas **`<schema>`**.

Isso nos leva a outro tipo de documento, que é gerado automaticamente a partir do schema de origem, simplesmente chamado de schema. Este schema será usado pelo aplicativo Adobe Campaign.

Os nomes SQL são determinados automaticamente com base no nome e no tipo do elemento.

As regras de nomenclatura SQL são as seguintes:

* tabela: concatenação da namespace e do nome do schema

   Em nosso exemplo, o nome da tabela é inserido pelo elemento principal do schema no atributo **sqltable** :

   ```
   <element name="recipient" sqltable="CusRecipient">
   ```

* campo: nome do elemento precedido por um prefixo definido de acordo com o tipo (&#39;i&#39; para integer, &#39;d&#39; para duplo, &#39;s&#39; para string, &#39;ts&#39; para datas, etc.)

   O nome do campo é inserido pelo atributo **sqlname** para cada tipo **`<attribute>`** e **`<element>`**:

   ```
   <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
   ```

>[!NOTE]
>
>Os nomes SQL podem ser sobrecarregados do schema de origem. Para fazer isso, preencha os atributos &quot;sqltable&quot; ou &quot;sqlname&quot; no elemento em questão.

O script SQL para criar a tabela gerada a partir do schema estendido é o seguinte:

```
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

As restrições de campo SQL são as seguintes:

* sem valores nulos nos campos numéricos e de data,
* campos numéricos são inicializados para 0.

## Campos XML {#xml-fields}

Por padrão, qualquer elemento digitado **`<attribute>`** e **`<element>`** é mapeado em um campo SQL da tabela do schema de dados. No entanto, é possível fazer referência a esse campo no XML em vez do SQL, o que significa que os dados são armazenados em um campo de memorando (&quot;mData&quot;) da tabela que contém os valores de todos os campos XML. O armazenamento desses dados é um documento XML que observa a estrutura do schema.

Para preencher um campo em XML, é necessário adicionar o atributo **xml** com o valor &quot;true&quot; ao elemento em questão.

**Exemplo**: há dois exemplos de uso de campo XML.

* Campo de comentário de várias linhas:

   ```
   <element name="comment" xml="true" type="memo" label="Comment"/>
   ```

* Descrição dos dados em formato HTML:

   ```
   <element name="description" xml="true" type="html" label="Description"/>
   ```

   O tipo &quot;html&quot; permite que você armazene o conteúdo HTML em uma tag CDATA e exiba uma verificação de edição HTML especial na interface do cliente Adobe Campaign.

O uso de campos XML permite que você adicione campos sem precisar modificar a estrutura física do banco de dados. Outra vantagem é que você usa menos recursos (tamanho alocado para campos SQL, limite do número de campos por tabela etc.).

A principal desvantagem é que é impossível indexar ou filtrar um campo XML.

## Campos indexados {#indexed-fields}

Os índices permitem otimizar o desempenho dos query SQL usados no aplicativo.

Um índice é declarado do elemento principal do schema de dados.

```
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Os índices obedecem às seguintes regras:

* Um índice pode fazer referência a um ou mais campos na tabela.
* Um índice pode ser exclusivo (para evitar duplicados) em todos os campos se o atributo **exclusivo** contiver o valor &quot;true&quot;.
* O nome SQL do índice é determinado a partir do nome SQL da tabela e do nome do índice.

>[!NOTE]
>
>Como padrão, os índices são os primeiros elementos declarados do elemento principal do schema.

>[!NOTE]
>
>Os índices são criados automaticamente durante o mapeamento de tabela (padrão ou FDA).

**Exemplo**:

* Adicionando um índice ao endereço de email e à cidade:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <dbindex name="email">
         <keyfield xpath="@email"/> 
         <keyfield xpath="location/@city"/> 
       </dbindex>
   
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
       <element name="location" label="Location">
         <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
       </element>
     </element>
   </srcSchema>
   ```

* Adicionando um índice exclusivo ao campo de nome &quot;id&quot;:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <dbindex name="id" unique="true">
         <keyfield xpath="@id"/> 
       </dbindex>
   
       <dbindex name="email">
         <keyfield xpath="@email"/> 
       </dbindex>
   
       <attribute name="id" type="long" label="Identifier"/>
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
     </element>
   </srcSchema>
   ```

## Gestão das chaves {#management-of-keys}

Uma tabela deve ter pelo menos uma chave para identificar um registro na tabela.

Uma chave é declarada do elemento principal do schema de dados.

```
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

As teclas obedecem às seguintes regras:

* Uma tecla pode fazer referência a um ou mais campos na tabela.
* Uma chave é conhecida como &quot;primária&quot; (ou &quot;prioridade&quot;) quando é a primeira no schema a ser preenchida ou se contém o atributo **interno** com o valor &quot;true&quot;.
* Um índice exclusivo é declarado implicitamente para cada definição de chave. A criação de um índice na chave pode ser impedida adicionando o atributo **noDbIndex** com o valor &quot;true&quot;.

>[!NOTE]
>
>Como padrão, as teclas são os elementos declarados do elemento principal do schema após a definição dos índices.

>[!NOTE]
>
>As chaves são criadas durante o mapeamento de tabela (padrão ou FDA), a Adobe Campaign encontra índices exclusivos.

**Exemplo**:

* Adicionando uma chave ao endereço de email e à cidade:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <key name="email">
         <keyfield xpath="@email"/> 
         <keyfield xpath="location/@city"/> 
       </key>
   
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
       <element name="location" label="Location">
         <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
       </element>
     </element>
   </srcSchema>
   ```

   O schema gerou:

   ```
   <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
     <element name="recipient" sqltable="CusRecipient">    
      <dbindex name="email" unique="true">      
        <keyfield xpath="@email"/>      
        <keyfield xpath="location/@city"/>    
      </dbindex>    
   
      <key name="email">      
       <keyfield xpath="@email"/>      
       <keyfield xpath="location/@city"/>    
      </key>    
   
      <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
      <element label="Location" name="location">      
        <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
      </element>  
     </element>
   </schema>
   ```

* Adicionando uma chave primária ou interna no campo de nome &quot;id&quot;:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <key name="id" internal="true">
         <keyfield xpath="@id"/> 
       </key>
   
       <key name="email" noDbIndex="true">
         <keyfield xpath="@email"/> 
       </key>
   
       <attribute name="id" type="long" label="Identifier"/>
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
     </element>
   </srcSchema>
   ```

   O schema gerou:

   ```
   <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
     <element name="recipient" sqltable="CusRecipient">    
       <key name="email">      
         <keyfield xpath="@email"/>    
       </key>    
   
       <dbindex name="id" unique="true">      
         <keyfield xpath="@id"/>    
       </dbindex>    
   
       <key internal="true" name="id">      
        <keyfield xpath="@id"/>    
       </key>    
   
       <attribute label="Identifier" name="id" sqlname="iRecipientId" type="long"/>    
       <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
     </element>
   </schema>
   ```

### Tecla incremental automaticamente {#auto-incremental-key}

A chave primária da maioria das tabelas do Adobe Campaign é um número inteiro de 32 bits gerado automaticamente pelo mecanismo de banco de dados. O cálculo do valor chave depende de uma sequência (por padrão, a função SQL **XtkNewId** ) que gera um número exclusivo no banco de dados inteiro. O conteúdo da chave é automaticamente inserido na inserção do registro.

A vantagem de uma chave incremental é que ela fornece uma chave técnica não modificável para as junções entre tabelas. Além disso, essa chave não ocupa muita memória porque usa um número inteiro de duplo byte.

Você pode especificar no schema de origem o nome da sequência a ser usada com o atributo **pkSequence** . Se esse atributo não for fornecido no schema de origem, a sequência padrão **XtkNewId** será usada. O aplicativo usa sequências dedicadas para os schemas **nms:wideLog** e **nms:trackingLog** (**NmsBroadLogId** e **NmsTrackingLogId** , respectivamente) porque essas são as tabelas que contêm mais registros.

De ACC 18.10, **XtkNewId** não é mais o valor padrão para a sequência nos schemas predefinidos. Agora você pode criar schemas ou estender schemas existentes com uma sequência dedicada.

>[!IMPORTANT]
>
>Ao criar um novo schema ou durante uma extensão de schema, você precisa manter o mesmo valor de sequência da chave primária (@pkSequence) para todo o schema.

>[!NOTE]
>
>Uma sequência referenciada em um schema Adobe Campaign (**NmsTrackingLogId** , por exemplo) deve ser associada a uma função SQL que retorna o número de IDs nos parâmetros, separadas por vírgulas. Essa função deve ser chamada de ******GetNewXXXIds**, onde **XXX** é o nome da sequência (**GetNewNmsTrackingLogIds** , por exemplo). Visualização os arquivos **postgres-nms.sql**, **mssql-nms.sql** ou **oracle-nms.sql** fornecidos com o aplicativo no diretório **datakit/nms/eng/sql/** para recuperar o exemplo de criação de uma sequência &#39;NmsTrackingLogId&#39; para cada mecanismo de banco de dados.

Para declarar uma chave exclusiva, preencha o atributo **autopk** (com o valor &quot;true&quot;) no elemento principal do schema de dados.

**Exemplo**:

Declarando uma chave incremental no schema de origem:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

O schema gerou:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" autopk="true" pkSequence="XtkNewId" sqltable="CusRecipient"> 
    <dbindex name="id" unique="true">
      <keyfield xpath="@id"/>
    </dbindex>

    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key>

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iRecipientId" type="long"/>
  </element>
</schema>
```

Além da definição da chave e seu índice, um campo numérico chamado &quot;id&quot; foi adicionado ao schema estendido para conter a chave primária gerada automaticamente.

>[!IMPORTANT]
>
>Um registro com uma chave primária definida como 0 é automaticamente inserido na criação da tabela. Este registro é usado para evitar junções externas, que não são eficazes em tabelas de volume. Por padrão, todas as chaves estrangeiras são inicializadas com o valor 0 para que um resultado possa sempre ser retornado na junção quando o item de dados não for preenchido.

## Links: relação entre tabelas {#links--relation-between-tables}

Um link descreve a associação entre uma tabela e outra.

Os vários tipos de associações (conhecidas como &quot;cardinalidades&quot;) são os seguintes:

* Cardinalidade 1-1: uma ocorrência da tabela de origem pode ter no máximo uma ocorrência correspondente da tabela de públicos alvos.
* Cardinalidade 1-N: uma ocorrência da tabela de origem pode ter várias ocorrências correspondentes da tabela de públicos alvos, mas uma ocorrência da tabela de públicos alvos pode ter no máximo uma ocorrência correspondente da tabela de origem.
* Cardinalidade N-N: uma ocorrência da tabela de origem pode ter várias ocorrências correspondentes da tabela de públicos alvos e vice-versa.

Na interface, você pode distinguir os diferentes tipos de relações facilmente graças aos ícones deles.

Para relações de união com uma tabela/banco de dados de campanha:

* ![](assets/join_with_campaign11.png) : Cardinalidade 1-1. Por exemplo, entre um recipient e um pedido atual. Um recipient pode estar relacionado a apenas uma ocorrência da tabela de pedido atual por vez.
* ![](assets/externaljoin11.png) : Cardinalidade 1-1, junção externa. Por exemplo, entre um recipient e seu país. Um recipient pode estar relacionado a apenas uma ocorrência do país da tabela. O conteúdo da tabela de países não será salvo.
* ![](assets/join_with_campaign1n.png) : Cardinalidade 1-N. Por exemplo, entre um recipient e a tabela subscrição. Um recipient pode estar relacionado a várias ocorrências na tabela subscrição.

Para unir relações usando o Acesso ao Banco de Dados Federado:

* ![](assets/join_fda_11.png) : Cardinalidade 1-1
* ![](assets/join_fda_1m.png) : Cardinalidade 1-N

For more information on FDA tables, refer to [Accessing an external database](../../platform/using/about-fda.md).

Um link deve ser declarado no schema que contém a chave estrangeira da tabela vinculada pelo elemento principal:

```
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

Os links obedecem às seguintes regras:

* A definição de um link é inserida em um tipo de **link****`<element>`** com os seguintes atributos:

   * **name**: nome do link da tabela de origem,
   * **público alvo**: nome do schema do público alvo,
   * **rótulo**: rótulo da ligação,
   * **revLink** (opcional): nome do link inverso do schema do público alvo (deduzido automaticamente por padrão),
   * **integridade** (opcional): integridade referencial da ocorrência da tabela de origem para a ocorrência da tabela de públicos alvos. Os valores possíveis são os seguintes:

      * **definir**: é possível excluir a ocorrência de origem se ela não for mais mencionada por uma ocorrência de público alvo,
      * **normal**: a exclusão da ocorrência de origem inicializa as chaves do link para a ocorrência do público alvo (modo padrão), esse tipo de integridade inicializa todas as chaves estrangeiras,
      * **próprio**: a exclusão da ocorrência de origem leva à exclusão da ocorrência do público alvo,
      * **cópia**: igual ao **próprio** (em caso de eliminação) ou duplicado das ocorrências (em caso de duplicação),
      * **neutro**: não faz nada.
   * **revIntegrity** (opcional): integridade no schema do público alvo (opcional, &quot;normal&quot; por padrão),
   * **revCardinalidade** (opcional): com o valor &quot;único&quot; preenche a cardinalidade com o tipo 1-1 (1-N por padrão).
   * **externalJoin** (opcional): força a união externa
   * **revExternalJoin** (opcional): força a união externa no link inverso


* Um link faz referência a um ou mais campos da tabela de origem para a tabela de destino. Os campos que compõem a junção ( `<join>` elemento) não precisam ser preenchidos porque são automaticamente deduzidos por padrão usando a chave interna do schema do público alvo.
* Um índice é adicionado automaticamente à chave estrangeira do link no schema estendido.
* Um link consiste em dois links parciais, nos quais o primeiro é declarado a partir do schema de origem e o segundo é criado automaticamente no schema estendido do schema do público alvo.
* Uma junção pode ser uma junção externa se o atributo **externalJoin** for adicionado, com o valor &quot;true&quot; (compatível com PostgreSQL).

>[!NOTE]
>
>Como padrão, os links são os elementos declarados no final do schema.

### Example 1 {#example-1}

1-N em relação à tabela de schemas &quot;cus:empresa&quot;:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

O schema gerou:

```
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

A definição do link é complementada pelos campos que compõem a junção, isto é, a chave primária com seu XPath (&quot;@id&quot;) no schema de destino, e a chave estrangeira com seu XPath (&quot;@empresa-id&quot;) no schema.

A chave estrangeira é adicionada automaticamente em um elemento que usa as mesmas características do campo associado na tabela de destino, com a seguinte convenção de nomenclatura: nome do schema do público alvo seguido do nome do campo associado (&quot;empresa-id&quot; no nosso exemplo).

Schema estendido do público alvo (&quot;cus:empresa&quot;):

```
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

* **name**: deduzida automaticamente do nome do schema de origem (pode ser forçada com o atributo &quot;revLink&quot; na definição do link no schema de origem)
* **revLink**: nome do link reverso
* **público alvo**: chave do schema vinculado (&quot;cus:recipient&quot; schema)
* **unbound**: o link é declarado como um elemento de coleção para uma cardinalidade 1-N (por padrão)
* **integridade**: &quot;define&quot; por padrão (pode ser forçado com o atributo &quot;revIntegrity&quot; na definição do link no schema de origem).

### Example 2 {#example-2}

Neste exemplo, declararemos um link para a tabela de schemas &quot;nms:address&quot;. A junção é uma junção externa e é preenchida explicitamente com o endereço de email do recipient e o campo &quot;@address&quot; da tabela vinculada (&quot;nms:address&quot;).

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient"> 
    ...
    <element integrity="neutral" label="Info about email" name="emailInfo" revIntegrity="neutral" revLink="recipient" target="nms:address" type="link" externalJoin="true">      
      <join xpath-dst="@address" xpath-src="@email"/>
    </element>
  </element>
</srcSchema>
```

### Example 3 {#example-3}

1-1 relação com a tabela de schemas &quot;cus:extension&quot;:

```
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

### Example 4 {#example-4}

Link para uma pasta ( schema &quot;xtk:folder&quot;):

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

O valor padrão retorna o identificador do primeiro arquivo de tipo de parâmetro elegível inserido na função &quot;DefaultFolder(&#39;nmsFolder&#39;)&quot;.

### Example 5 {#example-5}

Neste exemplo, desejamos criar uma chave em um link (&quot;empresa&quot; para o schema &quot;cus:empresa&quot;) com o atributo **xlink** e um campo da tabela (&quot;email&quot;):

```
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

O schema gerou:

```
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

    <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

A definição da chave do nome &quot;companyEmail&quot; foi estendida com a chave estrangeira do link &quot;empresa&quot;. Essa chave gera um índice exclusivo em ambos os campos.
