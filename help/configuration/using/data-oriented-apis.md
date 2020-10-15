---
title: APIs orientadas a dados
seo-title: APIs orientadas a dados
description: APIs orientadas a dados
seo-description: null
page-status-flag: never-activated
uuid: f81356b3-8eef-4b65-9510-47c9d4b4e871
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: fba46d42-0253-425b-bbc2-6702d4140e05
translation-type: tm+mt
source-git-commit: 63b208e5607bdcddaef03292d229847c4b7366f8
workflow-type: tm+mt
source-wordcount: '1884'
ht-degree: 1%

---


# APIs orientadas a dados{#data-oriented-apis}

As APIs orientadas por dados permitem que você solucione todo o modelo de dados.

## Visão geral do modelo de dados {#overview-of-the-datamodel}

A Adobe Campaign não oferta uma API de leitura dedicada por entidade (sem função getRecipient ou getDelivery etc.). Use os métodos de leitura e modificação de dados do QUERY e do WRITER para acessar os dados do modelo.

A Adobe Campaign permite gerenciar coleções: query permitem recuperar um conjunto de informações coletadas em toda a base. Diferentemente do acesso no modo SQL, as APIs do Adobe Campaign retornam uma árvore XML em vez de colunas de dados. Assim, a Adobe Campaign cria documentos compostos com todos os dados coletados.

Esse modo operacional não oferta o mapeamento um para um entre os atributos e elementos dos documentos XML e as colunas das tabelas no banco de dados.

DOCUMENTOS XML são armazenados nos campos do tipo MEMO do banco de dados.

## Descrição do modelo {#description-of-the-model}

É necessário estar familiarizado com o modelo de dados da Adobe Campaign para poder endereçar os campos do banco de dados em seus scripts.

Para obter uma apresentação do modelo de dados, consulte a descrição [do modelo de dados da](../../configuration/using/data-model-description.md)Adobe Campaign.

Para gerar sua estrutura, consulte este artigo: [Como gerar um Modelo de dados ou um Dicionário](https://helpx.adobe.com/campaign/kb/generate-data-model.html)de dados.

## Query e escritor {#query-and-writer}

O schema de introdução a seguir detalha as trocas de baixo nível para leitura (ExecuteQuery) e gravação (Writer) entre o banco de dados e o cliente (páginas da Web ou console do cliente Adobe Campaign).

![](assets/s_ncs_integration_webservices_schema_writer.png)

### ExecuteQuery {#executequery}

Para colunas e condições, você pode usar Query.

Isso permite isolar o SQL subjacente. A linguagem do query não depende do mecanismo subjacente: algumas funções serão mapeadas novamente, o que pode gerar várias ordens SELECT SQL.

Para obter mais informações, consulte [Exemplo no método &#39;ExecuteQuery&#39; do schema &#39;xtk:queryDef&#39;](../../configuration/using/web-service-calls.md#example-on-the--executequery--method-of-schema--xtk-querydef-).

O método **ExecuteQuery** é apresentado em [ExecuteQuery (xtk:queryDef)](#executequery--xtk-querydef-).

### Gravar {#write}

Os comandos Gravar permitem que você escreva documentos simples ou complexos, com entradas em uma ou mais tabelas da base.

As APIs transacionais permitem gerenciar reconciliações por meio do comando **updateOrInsert** : um comando permite criar ou atualizar dados. Você também pode configurar a união de modificação (**mesclagem**): esse modo operacional permite autorizar atualizações parciais.

A estrutura XML oferta uma visualização lógica dos dados e permite driblar a estrutura física da tabela SQL.

O método Write é apresentado em [Write / WriteCollection (xtk:session)](#write---writecollection--xtk-session-).

## ExecuteQuery (xtk:queryDef) {#executequery--xtk-querydef-}

Esse método permite executar query a partir de dados associados a um schema. É necessária uma string de autenticação (deve estar conectado) e um documento XML que descreve o query a ser submetido como parâmetros. O parâmetro return é um documento XML que contém o resultado do query no formato do schema ao qual o query se refere.

Definição do método &quot;ExecuteQuery&quot; no schema &quot;xtk:queryDef&quot;:

```
<method name="ExecuteQuery" const="true">
  <parameters>
    <param desc="Output XML document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

>[!NOTE]
>
>Este é um método &quot;const&quot;. Os parâmetros de entrada são incluídos em um documento XML no formato do schema &quot;xtk:queryDef&quot;.

### Formato do documento XML do query de entrada {#format-of-the-xml-document-of-the-input-query}

A estrutura do documento XML do query é descrita no schema &quot;xtk:queryDef &quot;. Este documento descreve as cláusulas de um query SQL: &quot;select&quot;, &quot;where&quot;, &quot;order by&quot;, &quot;group by&quot;, &quot;tendo&quot;.

```
<queryDef schema="schema_key" operation="operation_type">
  <select>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </select>
  <where> 
    <condition expr="expression1"/> 
    <condition expr="expression2"/>
    ... 
  </where>
  <orderBy>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </orderBy>
  <groupBy>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </groupBy>
  <having>
    <condition expr="expression1"/> 
    <condition expr="expression2"/>
    ...
  </having>
</queryDef>
```

Um subquery ( `<subquery>` ) pode ser definido em um `<condition> ` elemento. A sintaxe de um `<subquery> ` elemento se baseia na sintaxe de um `<querydef>`.

Example of a `<subquery>  : </subquery>`

```
<condition setOperator="NOT IN" expr="@id" enabledIf="$(/ignored/@ownerType)=1">
  <subQuery schema="xtk:operatorGroup">
     <select>
       <node expr="[@operator-id]" />
     </select>
     <where>
       <condition expr="[@group-id]=$long(../@owner-id)"/>
     </where>
   </subQuery>
</condition>  
  
```

Um query deve fazer referência a um schema start do atributo **schema** .

O tipo de operação desejado é inserido no atributo **operation** e contém um dos seguintes valores:

* **get**: recupera um registro da tabela e retorna um erro se os dados não existirem,
* **getIfExists**: recupera um registro da tabela e retorna um documento vazio se os dados não existirem,
* **selecione**: cria um cursor para retornar vários registros e retorna um documento vazio se não houver dados,
* **contagem**: retorna uma contagem de dados.

A sintaxe **XPath** é usada para localizar dados com base no schema de entrada. Para obter mais informações sobre XPouts, consulte schemas [de dados](../../configuration/using/data-schemas.md).

#### Exemplo com a operação &#39;get&#39; {#example-with-the--get--operation}

Recupera o sobrenome e o nome de um recipient (&quot;schema:nms:recipient&quot;) com um filtro no email.

```
<queryDef schema="nms:recipient" operation="get">
  <!-- fields to retrieve -->
  <select>
    <node expr="@firstName"/>
    <node expr="@lastName"/>
  </select> 

  <!-- condition on email -->
  <where>  
    <condition expr="@email= 'john.doe@aol.com'"/>
  </where>
</queryDef>
```

#### Exemplo com a operação &#39;select&#39; {#example-with-the--select--operation}

Retorna a lista de recipient filtrados em uma pasta e o domínio de email com uma classificação em ordem decrescente na data de nascimento.

```
<queryDef schema="nms:recipient" operation="select">
  <select>
    <node expr="@email"/>
    <!-- builds a string with the concatenation of the last name and first name separated by a dash -->      
    <node expr="@lastName+'-'+@firstName"/>
    <!-- get year of birth date -->
    <node expr="Year(@birthDate)"/>
  </select> 

  <where>  
     <condition expr="[@folder-id] = 1234 and @domain like 'Adobe%'"/>
  </where>

  <!-- order by birth date -->
  <orderBy>
    <node expr="@birthDate" sortDesc="true"/> <!-- by default sortDesc="false" -->
  </orderBy>
</queryDef>
```

Expressões podem ser campos simples ou expressões complexas, como operações aritméticas ou a concatenação de sequências de caracteres.

Para limitar o número de registros a serem retornados, adicione o atributo **lineCount** ao `<querydef>` elemento.

Para limitar o número de registros retornados pelo query para 100:

```
<queryDef schema="nms:recipient" operation="select" lineCount="100">
...
```

Para recuperar os próximos 100 registros, execute o mesmo query novamente, adicionando o atributo **startLine** .

```
<queryDef schema="nms:recipient" operation="select" lineCount="100" startLine="100">
...
```

#### Exemplo com a operação &#39;count&#39; {#example-with-the--count--operation}

Para contar o número de registros em um query:

```
<queryDef schema="nms:recipient" operation="count"">
  <!-- condition on the folder and domain of the e-mail -->
  <where>  
    <condition expr="[@folder-id] = 1234" and @domain like 'Adobe%'"/>
  </where>
</queryDef>
```

>[!NOTE]
>
>Novamente usamos a condição do exemplo anterior. As cláusulas `<select>` e não são usadas. `</select>`

#### Agrupamento de dados {#data-grouping}

Para recuperar endereços de email referenciados mais de uma vez:

```
<queryDef schema="nms:recipient" operation="select">
  <select>
    <node expr="@email"/>
    <node expr="count(@email)"/>
  </select>

  <!-- e-mail grouping clause -->
  <groupby>
    <node expr="@email"/>
  </groupby>

  <!-- grouping condition -->
  <having>
    <condition expr="count(@email) > 1"/>
  </having>

</queryDef>
```

O query pode ser simplificado adicionando o atributo **groupBy** diretamente ao campo a ser agrupado:

```
<select>
  <node expr="@email" groupBy="true"/>
</select>
```

>[!NOTE]
>
>Não é mais necessário preencher o `<groupby>` elemento.

#### Colchete em condições {#bracketing-in-conditions}

Estes são dois exemplos de colchetes na mesma condição.

* A versão simples em uma única expressão:

   ```
   <where>
     <condition expr="(@age > 15 or @age <= 45) and  (@city = 'Newton' or @city = 'Culver City') "/>
   </where>
   ```

* A versão estruturada com `<condition>` elementos:

   ```
   <where>
     <condition bool-operator="AND">
       <condition expr="@age > 15" bool-operator="OR"/>
       <condition expr="@age <= 45"/>
     </condition>
     <condition>
       <condition expr="@city = 'Newton'" bool-operator="OR"/>
       <condition expr="@city = 'Culver City'"/>
     </condition>
   </where>
   ```

É possível substituir o operador &#39;OR&#39; pela operação &#39;IN&#39; quando várias condições se aplicam ao mesmo campo:

```
<where>
  <condition>
    <condition expr="@age IN (15, 45)"/>
    <condition expr="@city IN ('Newton', 'Culver City')"/>
  </condition>
</where>
```

Essa sintaxe simplifica o query quando mais de dois dados são usados na condição.

#### Exemplos de links {#examples-on-links}

* Links 1-1 ou N1: quando a tabela tem a chave estrangeira (os start de link da tabela), os campos da tabela vinculada podem ser filtrados ou recuperados diretamente.

   Exemplo de um filtro no rótulo da pasta:

   ```
   <where>
     <condition expr="[folder/@label] like 'Segment%'"/>
   </where>
   ```

   Para recuperar os campos da pasta do schema &quot;nms:recipient&quot;:

   ```
   <select>
     <!-- label of recipient folder -->
     <node expr="[folder/@label]"/>
     <!-- displays the string count of the folder -->
     <node expr="partition"/>
   </select>
   ```

* Links de coleção (1N): a filtragem nos campos de uma tabela de coleção deve ser executada por meio do operador **EXISTS** ou **NOT EXISTS** .

   Para filtrar os recipient que se inscreveram no serviço de informação &#39;Newsletter&#39;:

   ```
   <where>
     <condition expr="subscription" setOperator="EXISTS">
       <condition expr="@name = 'Newsletter'"/>
     </condition>
   </where>
   ```

   A recuperação direta dos campos de um link de coleção a partir da `<select>` cláusula não é recomendada porque o query retorna um produto cardinal. Ela é usada somente quando a tabela vinculada contém apenas um registro (exemplo `<node expr="">`).

   Exemplo no link da coleção &quot;subscrição&quot;:

   ```
   <select>
     <node expr="subscription/@label"/>
   </select>
   ```

   É possível recuperar uma sublista que contém os elementos de um link de coleção na `<select>` cláusula. Os XPouts dos campos referenciados são contextuais a partir do elemento de coleta.

   Os elementos filtragem ( `<orderby>` ) e restrição ( `<where>` ) podem ser adicionados ao elemento de coleção.

   Neste exemplo, para cada recipient, o query retorna o email e a lista dos serviços de informação aos quais o recipient se inscreve:

   ```
   <queryDef schema="nms:recipient" operation="select">
     <select>
       <node expr="@email"/>
   
       <!-- collection table (unbound type) -->
       <node expr="subscription">  
         <node expr="[service/@label]"/>    
         <!-- sub-condition on the collection table -->
         <where>  
           <condition expr="@expirationDate >= GetDate()"/>
         </where>
         <orderBy>
           <node expr="@expirationDate"/> 
         </orderBy>
       </node>
     </select> 
   </queryDef>
   ```

#### Vínculo dos parâmetros das cláusulas &#39;where&#39; e &#39;select&#39; {#binding-the-parameters-of-the--where--and--select--clause}

O vínculo de parâmetros permite que o mecanismo defina os valores dos parâmetros usados no query. Isso é muito útil, já que o mecanismo é responsável pela fuga de valores e há o benefício adicional de um cache para os parâmetros serem recuperados.

Quando um query é construído, os valores &quot;vinculados&quot; são substituídos por um caractere (? no ODBC, `#[index]#` em cartazes...) no corpo do query SQL.

```
<select>
  <!--the value will be bound by the engine -->
  <node expr="@startDate = #2002/02/01#"/>                   
  <!-- the value will not be bound by the engine but visible directly in the query -->
  <node expr="@startDate = #2002/02/01#" noSqlBind="true"/> 
</select>
```

Para evitar vincular um parâmetro, o atributo &quot;noSqlBind&quot; deve ser preenchido com o valor &quot;true&quot;.

>[!IMPORTANT]
>
>Se o query incluir instruções &quot;pedido por&quot; ou &quot;grupo por&quot;, os mecanismos do banco de dados não poderão &quot;vincular&quot; valores. Você deve colocar o atributo @noSqlBind=&quot;true&quot; nas instruções &quot;select&quot; e/ou &quot;where&quot; do query.

#### Dica de construção de query: {#query-building-tip-}

Para ajudar com a sintaxe de um query, você pode gravar o query usando o editor de query genérico no console do cliente Adobe Campaign ( **[!UICONTROL Tools/ Generic query editor...]** menu). Para fazer isso:

1. Selecione os dados a serem recuperados:

   ![](assets/s_ncs_integration_webservices_queyr1.png)

1. Defina a condição do filtro:

   ![](assets/s_ncs_integration_webservices_queyr2.png)

1. Execute o query e pressione CTRL+F4 para visualização do código-fonte do query.

   ![](assets/s_ncs_integration_webservices_queyr3.png)

### Formato de documento de saída {#output-document-format}

O parâmetro return é um documento XML no formato do schema associado ao query.

Exemplo de um retorno do schema &quot;nms:recipient&quot; em uma operação &quot;get&quot;:

```
<recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
```

Em uma operação &quot;select&quot;, o documento retornado é uma lista discriminada de elementos:

```
<!-- the name of the first element does not matter -->
<recipient-collection>   
  <recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
  <recipient email="peter.martinez@adobe.com" lastName"Martinez" firstName="Peter"/>
  <recipient...
</recipient-collection>  
```

Exemplo de um documento retornado para a operação do tipo &quot;count&quot;:

```
<recipient count="3"/>
```

#### Alias {#alias}

Um alias permite modificar a localização dos dados no documento de saída. O atributo **alias** deve especificar um XPath no campo correspondente.

```
<queryDef schema="nms:recipient" operation="get">
  <select>
    <node expr="@firstName" alias="@firstName"/>
    <node expr="@lastName"/>
    <node expr="[folder/@label]" alias="@My_folder"/>
  </select> 
</queryDef>
```

Retorna:

```
<recipient My_folder="Recipients" First name ="John" lastName="Doe"/>
```

Em vez de:

```
<recipient firstName="John" lastName="Doe">
  <folder label="Recipients"/>
</recipient>
```

### Exemplo de mensagens SOAP {#example-of-soap-messages}

* Query:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <ExecuteQuery xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
         <__sessiontoken xsi:type='xsd:string'/>
         <entity xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
           <queryDef operation="get" schema="nms:recipient" xtkschema="xtk:queryDef">
             <select>
               <node expr="@email"/>
               <node expr="@lastName"/>
               <node expr="@firstName"/>
             </select>
             <where>
               <condition expr="@id = 3599"/>
             </where>
           </queryDef>
         </entity>
       </ExecuteQuery>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* Resposta:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <ExecuteQueryResponse xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
         <pdomOutput xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
           <recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
         </pdomOutput>
       </ExecuteQueryResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

## Write / WriteCollection (xtk:session) {#write---writecollection--xtk-session-}

Esses serviços são usados para inserir, atualizar ou excluir uma entidade (método &quot;Write&quot;) ou uma coleção de entidades (método &quot;WriteCollection&quot;).

As entidades a serem atualizadas estão associadas a um schema de dados. Os parâmetros de entrada são uma string de autenticação (deve estar conectado) e um documento XML que contém os dados a serem atualizados.

Este documento é complementado por instruções para configurar os procedimentos de gravação.

A chamada não retorna nenhum dado, exceto erros.

Definição dos métodos &quot;Write&quot; e &quot;WriteCollection&quot; no schema &quot;xtk:session&quot;:

```
<method name="Write" static="true">
  <parameters>
    <param name="doc" type="DOMDocument" desc="Difference document"/>
  </parameters>
</method>
<method name="WriteCollection" static="true">
  <parameters>
    <param name="doc" type="DOMDocument" desc="Difference collection document"/>
  </parameters>
</method>
```

>[!NOTE]
>
>Este é um método &quot;estático&quot;. Os parâmetros de entrada são incluídos em um documento XML no formato do schema a ser atualizado.

### Visão geral {#overview}

A reconciliação de dados opera com base na definição das chaves inseridas no schema associado. O procedimento de gravação procura a primeira chave elegível com base nos dados inseridos no documento de entrada. A entidade é inserida ou atualizada com base na sua existência no banco de dados.

A chave do schema da entidade a ser atualizada é concluída com base no atributo **xtkschema** .

A chave de reconciliação pode, portanto, ser forçada com o atributo **_key** contendo a lista de XPouts que compõem a chave (separados por vírgulas).

É possível forçar o tipo de operação preenchendo o atributo **_operation** com os seguintes valores:

* **inserir**: força a inserção do registro (a chave de reconciliação não é utilizada),
* **insertOrUpdate**: atualiza ou insere o registro dependendo da chave de reconciliação (modo padrão),
* **atualização**: atualiza o registro; não faz nada se os dados não existirem,
* **excluir**: apaga os registros,
* **none**: usado apenas para reconciliação de link, sem atualização ou inserção.

### Exemplo com o método &#39;Write&#39; {#example-with-the--write--method}

Atualização ou inserção de um recipient (operação implícita &quot;insertOrUpdate&quot;) com endereço de email, data de nascimento e cidade:

```
<recipient xtkschema="nms:recipient" email="john.doe@adobe.com" birthDate="1956/05/04" folder-id=1203 _key="@email, [@folder-id]">
  <location city="Newton"/>
</recipient>
```

Excluindo um recipient:

```
<recipient xtkschema="nms:recipient" _operation="delete" email="rene.dupont@adobe.com" folder-id=1203 _key="@email, [@folder-id]"/>
```

>[!NOTE]
>
>Para uma operação de exclusão, o documento de entrada deve conter apenas os campos que compõem a chave de reconciliação.

### Exemplo com o método &#39;WriteCollection&#39; {#example-with-the--writecollection--method}

Atualizar ou inserir vários recipient:

```
<recipient-collection xtkschema="nms:recipient">    
  <recipient email="john.doe@adobe.com" firstName="John" lastName="Doe" _key="@email"/>
  <recipient email="peter.martinez@adobe.com" firstName="Peter" lastName="Martinez" _key="@email"/>
  <recipient ...
</recipient-collection>
```

### Exemplo em links {#example-on-links}

#### Example 1 {#example-1}

Associando a pasta a um recipient com base em seu nome interno (@name).

```
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <folder name="Folder2" _operation="none"/>
</recipient>
```

Os atributos &quot;_key&quot; e &quot;_operation&quot; podem ser inseridos em um elemento vinculado. O comportamento nesse elemento é o mesmo do elemento principal do schema de entrada.

A definição da chave da entidade principal (&quot;nms:recipient&quot;) consiste em um campo de uma tabela vinculada (o `<folder>` schema de elemento &quot;xtk:folder&quot;) e o email.

>[!NOTE]
>
>A operação &quot;none&quot; inserida no elemento de pasta define uma reconciliação na pasta sem atualização ou inserção.

#### Example 2 {#example-2}

Atualização da empresa (tabela vinculada no schema &quot;cus:empresa&quot;) de um recipient:

```
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <company name="adobe" code="ERT12T" _key="@name" _operation="update"/>
</recipient>
```

#### Example 3 {#example-3}

Adicionando um recipient a um grupo com a tabela de relação de grupo (&quot;nms:rcpGrpRel&quot;):

```
<recipient _key="@email" email="martin.ledger@adobe.net" xtkschema="nms:recipient">
  <rcpGrpRel _key="[rcpGroup/@name]">
    <rcpGroup name="GRP1"/>
  </rcpGrpRel>
</recipient>
```

>[!NOTE]
>
>A definição da chave não é inserida no `<rcpgroup>` elemento porque uma chave implícita com base no nome do grupo é definida no schema &quot;nms:group&quot;.

### Elementos de coleção XML {#xml-collection-elements}

Por padrão, todos os elementos da coleção devem ser preenchidos para atualizar os elementos da coleção XML. Os dados do banco de dados serão substituídos pelos dados do documento de entrada. Se o documento contiver apenas os elementos a serem atualizados, você deverá preencher o atributo &quot;_operation&quot; em todos os elementos de coleta a serem atualizados para forçar uma mesclagem com os dados XML do banco de dados.

### Exemplo de mensagens SOAP {#example-of-soap-messages-1}

* Query:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <Write xmlns='urn:xtk:persist' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
         <__sessiontoken xsi:type='xsd:string'/>
         <domDoc xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
           <recipient xtkschema="nms:recipient" email="rene.dupont@adobe.com" firstName="René" lastName="Dupont" _key="@email">
         </domDoc>
       </Write>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* Resposta:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <WriteResponse xmlns='urn:' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
       </WriteResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

   Retornar com erro:

   ```
   <?xml version='1.0'?>
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <SOAP-ENV:Fault>
         <faultcode>SOAP-ENV:Server</faultcode>
         <faultstring xsi:type="xsd:string">Error while executing the method 'Write' of service 'xtk:persist'.</faultstring>
         <detail xsi:type="xsd:string">PostgreSQL error: ERROR:  duplicate key violates unique constraint &quot;nmsrecipient_id&quot;Impossible to save document of type 'Recipients (nms:recipient)'</detail>
       </SOAP-ENV:Fault>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

