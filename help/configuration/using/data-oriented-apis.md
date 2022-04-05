---
product: campaign
title: APIs orientadas por dados
description: APIs orientadas por dados
feature: API
exl-id: a392c55e-541a-40b1-a910-4a6dc79abd2d
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '1857'
ht-degree: 1%

---

# APIs orientadas por dados{#data-oriented-apis}

![](../../assets/v7-only.svg)

As APIs orientadas a dados permitem abordar todo o modelo de dados.

## Visão geral do modelo de dados {#overview-of-the-datamodel}

A Adobe Campaign não oferece uma API de leitura dedicada por entidade (sem função getRecipient ou getDelivery etc.). Use os métodos de leitura e modificação de dados de QUERY &amp; WRITER para acessar os dados do modelo.

O Adobe Campaign permite gerenciar coleções: As queries permitem recuperar um conjunto de informações coletadas em toda a base. Ao contrário do acesso no modo SQL, as APIs do Adobe Campaign retornam uma árvore XML em vez de colunas de dados. O Adobe Campaign, portanto, cria documentos compostos com todos os dados coletados.

Esse modo operacional não oferece mapeamento de um para um entre os atributos e elementos dos documentos XML e as colunas das tabelas no banco de dados.

Os documentos XML são armazenados em campos do tipo MEMO do banco de dados.

## Descrição do modelo {#description-of-the-model}

Familiarize-se com o modelo de dados Adobe Campaign para poder endereçar os campos do banco de dados em seus scripts.

Para obter uma apresentação do modelo de dados, consulte [Descrição do modelo de dados do Adobe Campaign](../../configuration/using/data-model-description.md).

## Query e Gravador {#query-and-writer}

O schema de introdução a seguir detalha trocas de baixo nível para leitura (ExecuteQuery) e gravação (Writer) entre banco de dados e cliente (páginas da Web ou console do cliente Adobe Campaign).

![](assets/s_ncs_integration_webservices_schema_writer.png)

### ExecuteQuery {#executequery}

Para colunas e condições, você pode usar Queries.

Isso permite isolar o SQL subjacente. A linguagem de consulta não depende do mecanismo subjacente: algumas funções serão remapeadas, o que pode gerar várias ordens SELECT SQL.

Para obter mais informações, consulte [Exemplo no método &#39;ExecuteQuery&#39; do schema &#39;xtk:queryDef&#39;](../../configuration/using/web-service-calls.md#example-on-the--executequery--method-of-schema--xtk-querydef-).

O **ExecuteQuery** é apresentado em [ExecuteQuery (xtk:queryDef)](#executequery--xtk-querydef-).

### Write {#write}

Os comandos de gravação permitem escrever documentos simples ou complexos, com entradas em uma ou mais tabelas da base.

As APIs transacionais permitem gerenciar reconciliações por meio do **updateOrInsert** comando: um comando permite criar ou atualizar dados. Você também pode configurar a mesclagem de modificações (**mesclar**): esse modo operacional permite autorizar atualizações parciais.

A estrutura XML oferece uma visualização lógica dos dados e permite contornar a estrutura física da tabela SQL.

O método Write é apresentado em [Write / WriteCollection (xtk:session)](#write---writecollection--xtk-session-).

## ExecuteQuery (xtk:queryDef) {#executequery--xtk-querydef-}

Esse método permite executar consultas a partir de dados associados a um schema. Ele usa uma cadeia de caracteres de autenticação (deve estar conectado) e um documento XML que descreve a consulta a ser enviada como parâmetros. O parâmetro return é um documento XML que contém o resultado da consulta no formato do schema ao qual a consulta se refere.

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

### Formato do documento XML da consulta de entrada {#format-of-the-xml-document-of-the-input-query}

A estrutura do documento XML da consulta é descrita no schema &quot;xtk:queryDef &quot;. Este documento descreve as cláusulas de uma consulta SQL: &quot;selecionar&quot;, &quot;onde&quot;, &quot;ordenar por&quot;, &quot;agrupar por&quot;, &quot;ter&quot;.

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

Um subquery ( `<subquery>`  ) pode ser definido em um  `<condition> `  elemento. A sintaxe de um   `<subquery> `   O elemento é baseado na sintaxe de um    `<querydef>`.

Exemplo de um `<subquery>  : </subquery>`

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

Uma query deve referenciar um schema inicial do **schema** atributo.

O tipo de operação desejado é inserido na variável **operation** e contém um dos seguintes valores:

* **get**: recupera um registro da tabela e retorna um erro se os dados não existirem,
* **getIfExists**: recupera um registro da tabela e retorna um documento vazio se os dados não existirem,
* **select**: cria um cursor para retornar vários registros e retorna um documento vazio se não houver dados,
* **count**: retorna uma contagem de dados.

O **XPath** é usada para localizar dados com base no schema de entrada. Para obter mais informações sobre XP; consulte [Schemas de dados](../../configuration/using/data-schemas.md).

#### Exemplo com a operação &quot;get&quot; {#example-with-the--get--operation}

Recupera o sobrenome e o nome de um recipient (schema &quot;nms:recipient&quot;) com um filtro no email.

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

#### Exemplo com a operação &quot;select&quot; {#example-with-the--select--operation}

Retorna a lista de recipients filtrados em uma pasta e o domínio de email com uma classificação em ordem decrescente na data de nascimento.

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

As expressões podem ser campos simples ou expressões complexas, como operações aritméticas ou a concatenação de strings.

Para limitar o número de registros a serem retornados, adicione o **lineCount** para a `<querydef>` elemento.

Para limitar o número de registros retornados pelo query a 100:

```
<queryDef schema="nms:recipient" operation="select" lineCount="100">
...
```

Para recuperar os próximos 100 registros, execute a mesma consulta novamente, adicionando o **startLine** atributo.

```
<queryDef schema="nms:recipient" operation="select" lineCount="100" startLine="100">
...
```

#### Exemplo com a operação &quot;count&quot; {#example-with-the--count--operation}

Para contar o número de registros em um query:

```
<queryDef schema="nms:recipient" operation="count"">
  <!-- condition on the folder and domain of the email -->
  <where>  
    <condition expr="[@folder-id] = 1234" and @domain like 'Adobe%'"/>
  </where>
</queryDef>
```

>[!NOTE]
>
>Novamente, usamos a condição do exemplo anterior. O `<select>` as cláusulas e não são usadas. `</select>`

#### Agrupamento de dados {#data-grouping}

Para recuperar endereços de email referenciados mais de uma vez:

```
<queryDef schema="nms:recipient" operation="select">
  <select>
    <node expr="@email"/>
    <node expr="count(@email)"/>
  </select>

  <!-- email grouping clause -->
  <groupby>
    <node expr="@email"/>
  </groupby>

  <!-- grouping condition -->
  <having>
    <condition expr="count(@email) > 1"/>
  </having>

</queryDef>
```

O query pode ser simplificado ao adicionar o **groupBy** atributo diretamente no campo a ser agrupado:

```
<select>
  <node expr="@email" groupBy="true"/>
</select>
```

>[!NOTE]
>
>Não é mais necessário preencher a variável `<groupby>` elemento.

#### Compactação em condições {#bracketing-in-conditions}

Aqui estão dois exemplos de colchetes na mesma condição.

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

* Links 1-1 ou N1: quando a tabela tem a chave externa (o link começa na tabela), os campos da tabela vinculada podem ser filtrados ou recuperados diretamente.

   Exemplo de filtro no rótulo da pasta:

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

* Links de coleção (1N): a filtragem nos campos de uma tabela de coleção deve ser executada por meio do **EXISTE** ou **NÃO EXISTE** operador.

   Para filtrar os recipients que assinaram o serviço de informação &quot;Informativo&quot;:

   ```
   <where>
     <condition expr="subscription" setOperator="EXISTS">
       <condition expr="@name = 'Newsletter'"/>
     </condition>
   </where>
   ```

   Recuperação direta dos campos de um link de coleção do `<select>` não é recomendada porque a consulta retorna um produto cardinal. Ele é usado somente quando a tabela vinculada contém apenas um registro (exemplo `<node expr="">`).

   Exemplo no link de coleção &quot;subscrição&quot;:

   ```
   <select>
     <node expr="subscription/@label"/>
   </select>
   ```

   É possível recuperar uma sublista contendo os elementos de um link de coleção no `<select>` cláusula. Os XPouts dos campos referenciados são contextuais do elemento de coleção.

   A filtragem ( `<orderby>`  ) e restrição (  `<where>`  ) podem ser adicionados ao elemento de coleção.

   Neste exemplo, para cada recipient, o query retorna o email e a lista de serviços de informação aos quais o recipient se inscreve:

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

#### Vínculo dos parâmetros da cláusula &#39;where&#39; e &#39;select&#39; {#binding-the-parameters-of-the--where--and--select--clause}

O vínculo de parâmetros permite que o mecanismo defina os valores dos parâmetros usados na query. Isso é muito útil, pois o mecanismo é responsável pelo escape dos valores e há o benefício adicional de um cache para os parâmetros a serem recuperados.

Quando uma consulta é construída, os valores &quot;vinculados&quot; são substituídos por um caractere (? em ODBC, `#[index]#` em postgres...) no corpo da consulta SQL.

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
>Se a consulta incluir instruções &quot;order-by&quot; ou &quot;group-by&quot;, os mecanismos de banco de dados não poderão &quot;vincular&quot; valores. Você deve colocar o atributo @noSqlBind=&quot;true&quot; nas instruções &quot;select&quot; e/ou &quot;where&quot; da query.

#### Dica de criação de consulta: {#query-building-tip-}

Para ajudar com a sintaxe de um query, você pode gravar o query usando o editor de query genérico no console do cliente Adobe Campaign ( **[!UICONTROL Tools/ Generic query editor...]** ). Para fazer isso:

1. Selecione os dados a serem recuperados:

   ![](assets/s_ncs_integration_webservices_queyr1.png)

1. Defina a condição do filtro:

   ![](assets/s_ncs_integration_webservices_queyr2.png)

1. Execute a consulta e pressione CTRL+F4 para visualizar o código-fonte da consulta.

   ![](assets/s_ncs_integration_webservices_queyr3.png)

### Formato do documento de saída {#output-document-format}

O parâmetro return é um documento XML no formato do schema associado à query.

Exemplo de um retorno do schema &quot;nms:recipient&quot; em uma operação &quot;get&quot;:

```
<recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
```

Em uma operação &quot;select&quot;, o documento retornado é uma enumeração de elementos:

```
<!-- the name of the first element does not matter -->
<recipient-collection>   
  <recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
  <recipient email="peter.martinez@adobe.com" lastName"Martinez" firstName="Peter"/>
  <recipient...
</recipient-collection>  
```

Exemplo de um documento retornado para a operação de tipo &quot;contagem&quot;:

```
<recipient count="3"/>
```

#### Alias {#alias}

Um alias permite modificar a localização dos dados no documento de saída. O **alias** deve especificar um XPath no campo correspondente.

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

* Consulta:

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

As entidades a serem atualizadas estão associadas a um schema de dados. Os parâmetros de entrada são uma string de autenticação (deve estar conectado) e um documento XML contendo os dados a serem atualizados.

Este documento é complementado por instruções para configurar os procedimentos de gravação.

A chamada não retorna dados, exceto erros.

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

A reconciliação de dados opera com base na definição das chaves inseridas no schema associado. O procedimento de gravação busca a primeira chave elegível com base nos dados inseridos no documento de entrada. A entidade é inserida ou atualizada com base em sua existência no banco de dados.

A chave do schema da entidade a ser atualizada é concluída com base na variável **xtkschema** atributo.

A chave de reconciliação pode, portanto, ser forçada com a variável **_key** que contém a lista de XPouts que compõem a chave (separados por vírgulas).

É possível forçar o tipo de operação preenchendo a variável **_operação** com os seguintes valores:

* **insert**: força a inserção do registro (a chave de reconciliação não é usada),
* **insertOrUpdate**: atualiza ou insere o registro dependendo da chave de reconciliação (modo padrão),
* **atualizar**: atualiza o registro; não faz nada se os dados não existirem,
* **excluir**: exclui os registros,
* **nenhum**: usado somente para reconciliação de link, sem atualização ou inserção.

### Exemplo com o método &quot;Write&quot; {#example-with-the--write--method}

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

Atualizar ou inserir para vários recipients:

```
<recipient-collection xtkschema="nms:recipient">    
  <recipient email="john.doe@adobe.com" firstName="John" lastName="Doe" _key="@email"/>
  <recipient email="peter.martinez@adobe.com" firstName="Peter" lastName="Martinez" _key="@email"/>
  <recipient ...
</recipient-collection>
```

### Exemplo em links {#example-on-links}

#### Exemplo 1 {#example-1}

Associando a pasta a um recipient com base em seu nome interno (@name).

```
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <folder name="Folder2" _operation="none"/>
</recipient>
```

Os atributos &quot;_key&quot; e &quot;_operation&quot; podem ser inseridos em um elemento vinculado. O comportamento nesse elemento é o mesmo do elemento principal do schema de entrada.

A definição da chave da entidade principal (&quot;nms:recipient&quot;) consiste em um campo de uma tabela vinculada (elemento `<folder>`  schema &quot;xtk:folder&quot;) e o email.

>[!NOTE]
>
>A operação &quot;none&quot; inserida no elemento folder define uma reconciliação na pasta sem atualização ou inserção.

#### Exemplo 2 {#example-2}

Atualização da empresa (tabela vinculada no schema &quot;cus:company&quot;) de um recipient:

```
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <company name="adobe" code="ERT12T" _key="@name" _operation="update"/>
</recipient>
```

#### Exemplo 3 {#example-3}

Adicionar um recipient a um grupo com a tabela de relação de grupo (&quot;nms:rcpGrpRel&quot;):

```
<recipient _key="@email" email="martin.ledger@adobe.net" xtkschema="nms:recipient">
  <rcpGrpRel _key="[rcpGroup/@name]">
    <rcpGroup name="GRP1"/>
  </rcpGrpRel>
</recipient>
```

>[!NOTE]
>
>A definição da chave não é inserida na variável `<rcpgroup>` elemento porque uma chave implícita com base no nome do grupo é definida no schema &quot;nms:group&quot;.

### Elementos de coleção XML {#xml-collection-elements}

Por padrão, todos os elementos de coleção devem ser preenchidos para atualizar os elementos de coleção XML. Os dados do banco de dados serão substituídos pelos dados do documento de entrada. Se o documento contiver apenas os elementos a serem atualizados, você deverá preencher o atributo &quot;_operation&quot; em todos os elementos de coleção a serem atualizados para forçar uma mesclagem com os dados XML do banco de dados.

### Exemplo de mensagens SOAP {#example-of-soap-messages-1}

* Consulta:

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
