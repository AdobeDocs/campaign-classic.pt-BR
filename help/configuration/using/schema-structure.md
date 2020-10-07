---
title: Estrutura de schema
seo-title: Estrutura de schema
description: Estrutura de schema
seo-description: null
page-status-flag: never-activated
uuid: 9be70907-6154-4890-91e8-fd0fac30ab05
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: b5c8faf7-d0ae-4d95-b7fe-6ef9674a33d2
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1566'
ht-degree: 12%

---


# Estrutura de schema{#schema-structure}

A estrutura básica de um `<srcschema>` é a seguinte:

```
<srcSchema>
    <enumeration>
        ...          //definition of enumerations
    </enumeration>
   
    <element>         //definition of the root <element>    (mandatory)

        <compute-string/>  //definition of a compute-string
        <dbindex>
            ...        //definition of indexes
        </dbindex>
        <key>
            ...        //definition of keys
        </key>
        <sysFilter>
            ...           //definition of filters
        </sysFilter>
        <attribute>
            ...             //definition of fields
        </attribute>
    
            <element>           //definition of sub-<element> 
                  <attribute>           //(collection, links or XML)
                  ...                         //and additional fields
                  </attribute>
                ...
            </element>
      
    </element> 

        <methods>                 //definition of SOAP methods
            <method>
                ...
            </method>
            ...
    </methods>  
          
</srcSchema>
```

O documento XML de um schema de dados deve conter o **`<srcschema>`** elemento raiz com os atributos **name** e **namespace** para preencher o nome e o namespace do schema.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Use o seguinte conteúdo XML para ilustrar a estrutura de um schema de dados:

```
<recipient email="John.doe@aol.com" created="2009/03/12" gender="1"> 
  <location city="London"/>
</recipient>
```

Com seu schema de dados correspondente:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email"/>
    <attribute name="created"/>
    <attribute name="gender"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

## Descrição {#description}

O ponto de entrada do schema é seu elemento principal. É fácil identificar porque ele tem o mesmo nome do schema e deve se originar do elemento raiz. A descrição do conteúdo começa com esse elemento.

Em nosso exemplo, o elemento principal é representado pela seguinte linha:

```
<element name="recipient">
```

Os elementos **`<attribute>`** e **`<element>`** que seguem o elemento principal permitem que você defina os locais e nomes dos itens de dados na estrutura XML.

Em nosso schema de amostra, eles são:

```
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

Devem ser respeitadas as seguintes regras:

* Cada **`<element>`** e **`<attribute>`** deve ser identificado pelo nome através do atributo **name** .

   >[!IMPORTANT]
   >
   >O nome do elemento deve ser conciso, de preferência em inglês, e incluir somente caracteres autorizados de acordo com as regras de nomenclatura XML.

* Somente **`<element>`** elementos podem conter **`<attribute>`** elementos e **`<element>`** elementos na estrutura XML.
* Um **`<attribute>`** elemento deve ter um nome exclusivo em um **`<element>`**.
* Recomenda-se o uso de sequências de dados **`<elements>`** em várias linhas.

## Tipos de dados {#data-types}

O tipo de dados é inserido pelo atributo **type** nos elementos **`<attribute>`** e **`<element>`** .

Uma lista detalhada está disponível na descrição do [`<attribute>` elemento](../../configuration/using/elements-and-attributes.md#attribute--element) e do [`<element>` elemento](../../configuration/using/elements-and-attributes.md#element--element).

Quando esse atributo não é preenchido, a **string** é o tipo de dados padrão, a menos que o elemento contenha elementos filho. Se isso acontecer, será usado apenas para estruturar os elementos hierarquicamente (elemento no nosso exemplo **`<location>`** ).

Os seguintes tipos de dados são suportados em schemas:

* **string**: sequência de caracteres. Exemplos: um nome, uma cidade, etc.

   O tamanho pode ser especificado por meio do atributo **length** (opcional, valor padrão &quot;255&quot;).

* **booleano**: Campo booleano. Exemplo de valores possíveis: true/false, 0/1, sim/não, etc.
* **byte**, **curto**, **longo**: inteiros (1 byte, 2 bytes, 4 bytes). Exemplos: uma idade, um número de conta, um número de pontos, etc.
* **duplo**: Número de ponto flutuante de precisão do duplo. Exemplos: um preço, uma taxa, etc.
* **data**, **datetime**: datas e datas + horas. Exemplos: data de nascimento, data de compra, etc.
* **datetimenotz**: data + hora sem dados de fuso horário.
* **calendário**: durações. Exemplo: senioridade.
* **memorando**: campos de texto longos (várias linhas). Exemplos: uma descrição, um comentário etc.
* **uid**: campos &quot;uniqueidentifier&quot; para suportar um GUID (compatível somente com o Microsoft SQL Server).

   >[!NOTE]
   >
   >Para conter um campo **uuid** em mecanismos diferentes do Microsoft SQL Server, a função &quot;newuuid()&quot; deve ser adicionada e concluída com seu valor padrão.

Este é nosso exemplo de schema com os tipos inseridos:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email" type="string" length="80"/>
    <attribute name="created" type="datetime"/>
    <attribute name="gender" type="byte"/>
    <element name="location">
      <attribute name="city" type="string" length="50"/>
   </element>
  </element>
</srcSchema>
```

### Mapeamento dos tipos de dados do Adobe Campaign/DBMS {#mapping-the-types-of-adobe-campaign-dbms-data}

A tabela abaixo lista os mapeamentos para os tipos de dados gerados pela Adobe Campaign para os diferentes sistemas de gerenciamento de banco de dados.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> <strong>Teradata</strong><br /> </td> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> <strong>MS SQL</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Cadeia de caracteres<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2 (NVARCHAR2 se unicode)<br /> </td> 
   <td> VARCHAR (CARACTERE VARCHAR DEFINE UNICODE se Unicode)<br /> </td> 
   <td> VARCHAR<br /> </td> 
   <td> VARCHAR (NVARCHAR se unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Booleano<br /> </td> 
   <td> PEQUENO<br /> </td> 
   <td> NÚMERO(3)<br /> </td> 
   <td> NUMÉRICO(3)<br /> </td> 
   <td> PEQUENO<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Byte<br /> </td> 
   <td> PEQUENO<br /> </td> 
   <td> NÚMERO(3)<br /> </td> 
   <td> NUMÉRICO(3)<br /> </td> 
   <td> PEQUENO<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Curto<br /> </td> 
   <td> PEQUENO<br /> </td> 
   <td> NÚMERO(5)<br /> </td> 
   <td> PEQUENO<br /> </td> 
   <td> PEQUENO<br /> </td> 
   <td> PEQUENO<br /> </td> 
  </tr> 
  <tr> 
   <td> Duplo<br /> </td> 
   <td> PRECISÃO DO duplo<br /> </td> 
   <td> FLUTUAÇÃO<br /> </td> 
   <td> FLUTUAÇÃO<br /> </td> 
   <td> DOUBLE<br /> </td> 
   <td> FLUTUAÇÃO<br /> </td> 
  </tr> 
  <tr> 
   <td> Longo<br /> </td> 
   <td> INTEIRO<br /> </td> 
   <td> NUMBER(10)<br /> </td> 
   <td> INTEIRO<br /> </td> 
   <td> INTEIRO<br /> </td> 
   <td> INT<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> NUMBER(20)<br /> </td> 
   <td> NUMÉRICO(20)<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> BIGINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Data<br /> </td> 
   <td> DATE<br /> </td> 
   <td> DATE<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> DATE<br /> </td> 
   <td> DATETIME<br /> </td> 
  </tr> 
  <tr> 
   <td> Time<br /> </td> 
   <td> TIME<br /> </td> 
   <td> FLUTUAÇÃO<br /> </td> 
   <td> TIME<br /> </td> 
   <td> TIME<br /> </td> 
   <td> FLUTUAÇÃO<br /> </td> 
  </tr> 
  <tr> 
   <td> Data e hora<br /> </td> 
   <td> TIMESTAMPING<br /> </td> 
   <td> DATE<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> MS SQL &lt; 2008: DATETIME<br /> MS SQL &gt;= 2012: DATETIMEOFFSET<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> TIMESTAMPING<br /> </td> 
   <td> DATE<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> MS SQL &lt; 2008: DATETIME<br /> MS SQL &gt;= 2012: DATETIME2<br /> </td> 
  </tr> 
  <tr> 
   <td> Duração<br /> </td> 
   <td> PRECISÃO DO duplo<br /> </td> 
   <td> FLUTUAÇÃO<br /> </td> 
   <td> FLUTUAÇÃO<br /> </td> 
   <td> DOUBLE<br /> </td> 
   <td> FLUTUAÇÃO<br /> </td> 
  </tr> 
  <tr> 
   <td> Memorando<br /> </td> 
   <td> TEXT<br /> </td> 
   <td> CLOB (NCLOB se Unicode)<br /> </td> 
   <td> CLOB (CLOB CHARACTER SET UNICODE se Unicode)<br /> </td> 
   <td> CLOB(6M)<br /> </td> 
   <td> TEXT (NTEXT se Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB(4M)<br /> </td> 
   <td> IMAGE<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Propriedades {#properties}

Os elementos **`<elements>`** e os elementos **`<attributes>`** do schema de dados podem ser enriquecidos com várias propriedades. Você pode preencher um rótulo para descrever o elemento atual.

### Etiquetas e descrições {#labels-and-descriptions}

* A propriedade **label** permite inserir uma breve descrição.

   >[!NOTE]
   >
   >O rótulo está associado ao idioma atual da instância.

   **Exemplo**:

   ```
   <attribute name="email" type="string" length="80" label="Email"/>
   ```

   O rótulo pode ser visto no formulário de entrada do console do cliente Adobe Campaign:

   ![](assets/d_ncs_integration_schema_label.png)

* A propriedade **desc** permite inserir uma descrição longa.

   A descrição pode ser vista do formulário de entrada na barra de status da janela principal do console do cliente Adobe Campaign.

   >[!NOTE]
   >
   >A descrição está associada ao idioma atual da instância.

   **Exemplo**:

   ```
   <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
   ```

### Valores padrão {#default-values}

A propriedade **padrão** permite definir uma expressão que retorna um valor padrão na criação do conteúdo.

O valor deve ser uma expressão compatível com o idioma XPath. Para obter mais informações, consulte [Referenciando com XPath](../../configuration/using/schema-structure.md#referencing-with-xpath).

**Exemplo**:

* Data atual: **default=&quot;GetDate()&quot;**
* Contador: **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

   Neste exemplo, o valor padrão é construído usando a concatenação de uma string e chamando a função **CounterValue** com um nome de contador gratuito. O número retornado é incrementado em um em cada inserção.

   >[!NOTE]
   >
   >No console do cliente Adobe Campaign, o **[!UICONTROL Administration>Counters]** nó é usado para gerenciar contadores.

Para vincular um valor padrão a um campo, é possível usar a variável `<default>  or  <sqldefault>   field.  </sqldefault> </default>`

`<default>` : permite que você preencha previamente o campo com um valor padrão ao criar entidades. O valor não será um valor SQL padrão.

`<sqldefault>` : permite que você tenha um valor adicionado ao criar um campo. Esse valor é exibido como um resultado SQL. Durante uma atualização de schema, somente os novos registros serão afetados por esse valor.

### Enumerações {#enumerations}

#### Lista discriminada gratuita {#free-enumeration}

A propriedade **userEnum** permite definir uma lista discriminada gratuita para memorizar e exibir os valores inseridos por meio desse campo. A sintaxe é a seguinte:

**userEnum=&quot;nome da lista discriminada&quot;**

O nome dado à lista discriminada pode ser escolhido livremente e compartilhado com outros campos.

Esses valores são mostrados em uma lista suspensa do formulário de entrada:

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>No console do cliente Adobe Campaign, o **[!UICONTROL Administration > Enumerations]** nó é usado para gerenciar o lista discriminada.

#### Definir lista discriminada {#set-enumeration}

A propriedade **enum** permite definir uma lista discriminada fixa usada quando a lista de possíveis valores é conhecida antecipadamente.

O atributo **enum** se refere à definição de uma classe de lista discriminada preenchida no schema fora do elemento principal.

As listas discriminadas permitem que o usuário selecione um valor de uma lista suspensa em vez de inserir o valor em um campo de entrada regular:

![](assets/d_ncs_integration_schema_enum.png)

Exemplo de uma declaração de lista discriminada no schema de dados:

```
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

Uma lista discriminada é declarada fora do elemento principal por meio do **`<enumeration>`** elemento .

As propriedades da lista discriminada são as seguintes:

* **baseType**: tipo de dados associados aos valores,
* **rótulo**: descrição da lista discriminada,
* **name**: nome da lista discriminada,
* **padrão**: valor padrão da lista discriminada.

Os valores de lista discriminada são declarados no **`<value>`** elemento com os seguintes atributos:

* **name**: nome do valor armazenado internamente,
* **rótulo**: rótulo exibido por meio da interface gráfica.

#### lista discriminada dbenum {#dbenum-enumeration}

* A propriedade **dbenum** permite definir uma lista discriminada cujas propriedades são semelhantes às da propriedade **enum** .

   No entanto, o atributo **name** não armazena o valor internamente, ele armazena um código que permite estender as tabelas em questão sem modificar seu schema.

   Os valores são definidos pelo **[!UICONTROL Administration>Enumerations]** nó.

   Essa lista discriminada é usada para especificar a natureza das campanhas, por exemplo.

   ![](assets/d_ncs_configuration_schema_dbenum.png)

### Exemplo {#example}

Este é o nosso exemplo de schema com as propriedades preenchidas:

```
<srcSchema name="recipient" namespace="cus">
  <enumeration name="gender" basetype="byte">    
    <value name="unknown" label="Not specified" value="0"/>    
    <value name="male" label="male" value="1"/>   
    <value name="female" label="female" value="2"/>   
  </enumeration>

  <element name="recipient">
    <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
    <attribute name="created" type="datetime" label="Date of creation" default="GetDate()"/>
    <attribute name="gender" type="byte" label="gender" enum="gender"/>
    <element name="location" label="Location">
      <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
   </element>
  </element>
</srcSchema>
```

## Coleções {#collections}

Uma coleção é uma lista de elementos com o mesmo nome e o mesmo nível hierárquico.

O atributo **não vinculado** com o valor &quot;true&quot; permite preencher um elemento de coleção.

**Exemplo**: definição do elemento de **`<group>`** coleção no schema.

```
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

Com a projeção do conteúdo XML:

```
<group label="Group1"/>
<group label="Group2"/>
```

## Referência com XPath {#referencing-with-xpath}

A linguagem XPath é usada no Adobe Campaign para referenciar um elemento ou atributo que pertence a um schema de dados.

XPath é uma sintaxe que permite localizar um nó na árvore de um documento XML.

Os elementos são designados pelo nome e os atributos são designados pelo nome precedido pelo caractere &quot;@&quot;.

**Exemplo**:

* **@email**: seleciona o e-mail,
* **location/@city**: seleciona o atributo &quot;city&quot; sob o **`<location>`** elemento
* **../@email**: seleciona o endereço de email do elemento pai do elemento atual
* **grupo`[1]/@label`**: seleciona o atributo &quot;label&quot; que é o filho do primeiro elemento de **`<group>`** coleção
* **grupo`[@label='test1']`**: seleciona o atributo &quot;label&quot; que é o filho do **`<group>`** elemento e contém o valor &quot;test1&quot;

>[!NOTE]
>
>Uma restrição adicional é adicionada quando o caminho cruza um subelemento. Nesse caso, a seguinte expressão deve ser colocada entre colchetes:
>
>* **location/@city** não é válido; use **`[location/@city]`**
>* **`[@email]`** e **@email** são equivalentes

>



Também é possível definir expressões complexas, como as seguintes operações aritméticas:

* **@gender+1**: adiciona 1 ao conteúdo do atributo **gênero** ,
* **@email + &#39;(&#39;+@created+&#39;)&#39;**: constrói uma string tirando o valor do endereço de email adicionado à data de criação entre parênteses (para o tipo de string, coloque a constante entre aspas).

Funções de alto nível foram adicionadas às expressões para enriquecer o potencial desse idioma.

Você pode acessar a lista de funções disponíveis por meio de qualquer editor de expressão no console do cliente Adobe Campaign:

![](assets/d_ncs_integration_schema_function.png)

**Exemplo**:

* **GetDate()**: retorna a data atual
* **Year(@created)**: retorna o ano da data contida no atributo &quot;criado&quot;.
* **GetEmailDomain(@email)**: retorna o domínio do endereço de email.

## Criação de uma string por meio da string de computação {#building-a-string-via-the-compute-string}

Uma string **** Compute é uma expressão XPath usada para construir uma string que representa um registro em uma tabela associada ao schema. **A string** de computação é usada principalmente na interface gráfica para exibir o rótulo de um registro selecionado.

A string **** Compute é definida pelo **`<compute-string>`** elemento abaixo do elemento principal do schema de dados. Um atributo **expr** contém uma expressão XPath para calcular a exibição.

**Exemplo**: compute a string da tabela de recipient.

```
<srcSchema name="recipient" namespace="nms">  
  <element name="recipient">
    <compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')' "/>
    ...
  </element>
</srcSchema>
```

Resultado da string calculada para um recipient: **Doe John (john.doe@aol.com)**

>[!NOTE]
>
>Se o schema não contiver uma string de Compute, uma string de Compute será preenchida por padrão com os valores da chave primária do schema.

