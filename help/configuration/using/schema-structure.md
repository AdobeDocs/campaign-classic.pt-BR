---
product: campaign
title: Entender a estrutura do esquema no Adobe Campaign
description: Estrutura de esquema
feature: Custom Resources
role: Data Engineer, Developer
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1510'
ht-degree: 11%

---

# Entender a estrutura do esquema {#schema-structure}

A estrutura básica de um schema é descrita abaixo.

## Esquemas de dados  {#data-schema}

Para um `<srcschema>`, a estrutura é a seguinte:

```sql
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

```sql
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Vamos usar o seguinte conteúdo XML para ilustrar a estrutura de um schema de dados:

```sql
<recipient email="John.doe@aol.com" created="2009/03/12" gender="1"> 
  <location city="London"/>
</recipient>
```

Com seu schema de dados correspondente:

```sql
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

No nosso exemplo, o elemento principal é representado pela seguinte linha:

```
<element name="recipient">
```

A variável **`<attribute>`** e **`<element>`** os elementos que seguem o elemento principal são usados para definir os locais e os nomes dos itens de dados na estrutura XML.

No nosso esquema de amostra, são eles:

```sql
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

As seguintes regras se aplicam:

* Each **`<element>`** e **`<attribute>`** deve ser identificado por nome através do **name** atributo.

  >[!IMPORTANT]
  >
  >O nome do elemento deve ser conciso, de preferência em inglês e incluir apenas caracteres permitidos nas regras de nomenclatura XML.

* Somente **`<element>`** os elementos podem conter **`<attribute>`** elementos e **`<element>`** elementos na estrutura XML.
* Um **`<attribute>`** o elemento deve ter um nome exclusivo dentro de um **`<element>`**.
* A utilização de **`<elements>`** em cadeias de caracteres de dados de várias linhas é recomendado.

## Tipos de dados {#data-types}

O tipo de dados é inserido por meio de **type** atributo no **`<attribute>`** e **`<element>`** elementos.

Uma lista detalhada está disponível na descrição do [`<attribute>` element](../../configuration/using/schema/attribute.md) e a variável [`<element>` element](../../configuration/using/schema/element.md).

Quando este atributo não é preenchido, **string** é o tipo de dados padrão, a menos que o elemento contenha elementos secundários. Se isso acontecer, será usado apenas para estruturar os elementos hierarquicamente (**`<location>`** elemento em nosso exemplo).

Os seguintes tipos de dados são aceitos em esquemas:

* **string**: cadeia de caracteres. Exemplos: um nome, uma cidade etc.

  O tamanho pode ser especificado por meio da variável **length** atributo (opcional, valor padrão &quot;255&quot;).

* **booleano**: Campo booleano. Exemplo de valores possíveis: true/false, 0/1, yes/no, etc.
* **byte**, **curto**, **long**: números inteiros (1 byte, 2 bytes, 4 bytes). Exemplos: uma idade, um número de conta, um número de pontos, etc.
* **duplo**: número de ponto flutuante de precisão dupla. Exemplos: um preço, uma taxa etc.
* **data**, **datetime**: datas e datas + horas. Exemplos: uma data de nascimento, uma data de compra etc.
* **datetimenotz**: data + hora sem dados de fuso horário.
* **timespan**: durações. Exemplo: prioridade.
* **memorando**: campos de texto longo (várias linhas). Exemplos: uma descrição, um comentário etc.
* **uuid**: campos &quot;uniqueidentifier&quot; para oferecer suporte a uma GUID (compatível somente com o Microsoft SQL Server).

  >[!NOTE]
  >
  >Para conter um **uuid** no RDBMS que não seja o Microsoft SQL Server, `the newuuid()` deve ser adicionada e concluída com seu valor padrão.

Aqui está nosso schema de exemplo com os tipos inseridos:

```sql
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

A tabela abaixo lista os mapeamentos para os tipos de dados gerados pelo Adobe Campaign para os diferentes sistemas de gerenciamento de banco de dados.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> String<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2 (NVARCHAR2 se unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Booleano<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NÚMERO(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Byte<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NÚMERO(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Short<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NÚMERO(5)<br /> </td> 
  </tr> 
  <tr> 
   <td> Duplo<br /> </td> 
   <td> PRECISÃO DUPLA<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Longo<br /> </td> 
   <td> INTEIRO<br /> </td> 
   <td> NÚMERO(10)<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> NÚMERO(20)<br /> </td> 
  </tr> 
  <tr> 
   <td> Data<br /> </td> 
   <td> DATA<br /> </td> 
   <td> DATA<br /> </td> 
  </tr> 
  <tr> 
   <td> Hora<br /> </td> 
   <td> HORA<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Data e hora<br /> </td> 
   <td> CARIMBO DE DATA E HORA<br /> </td> 
   <td> DATA<br /> </td> 
  </tr> 
  <tr> 
   <td> Data e hora<br /> </td> 
   <td> CARIMBO DE DATA E HORA<br /> </td> 
   <td> DATA<br /> </td> 
  </tr> 
  <tr> 
   <td> Período<br /> </td> 
   <td> PRECISÃO DUPLA<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Memorando<br /> </td> 
   <td> TEXTO<br /> </td> 
   <td> CLOB (NCLOB se Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Propriedades {#properties}

A variável **`<elements>`** e **`<attributes>`** os elementos do schema de dados podem ser enriquecidos com várias propriedades. É possível preencher um rótulo para descrever o elemento atual.

### Rótulos e descrições {#labels-and-descriptions}

* A variável **rótulo** permite inserir uma breve descrição.

  >[!NOTE]
  >
  >O rótulo é associado ao idioma atual da instância.

  **Exemplo**:

  ```sql
  <attribute name="email" type="string" length="80" label="Email"/>
  ```

  O rótulo é exibido no formulário de entrada do console do cliente Adobe Campaign:

  ![](assets/d_ncs_integration_schema_label.png)

* A variável **desc** permite inserir uma descrição longa.

  A descrição é exibida no formulário de entrada na barra de status da janela principal do console do cliente Adobe Campaign.

  >[!NOTE]
  >
  >A descrição está associada ao idioma atual da instância.

  **Exemplo**:

  ```sql
  <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
  ```

### Valores padrão {#default-values}

Use o **padrão** para definir uma expressão que retorna um valor padrão na criação de conteúdo.

O valor deve ser uma expressão compatível com a linguagem XPath. Para obter mais informações, consulte [Referência com XPath](../../configuration/using/schema-structure.md#referencing-with-xpath).

**Exemplo**:

* Data atual: **default=&quot;GetDate()&quot;**
* Contador: **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

  Neste exemplo, o valor padrão é construído usando a concatenação de uma string e chamando o **ValorContador** com um nome de contador livre. O número retornado é incrementado em um em cada inserção.

  >[!NOTE]
  >
  >No console do cliente Adobe Campaign, navegue até o **[!UICONTROL Administration > Counters]** pasta do Explorer para gerenciar contadores.

Para vincular um valor padrão a um campo, é possível usar o `<default>`  ou  `<sqldefault>`   campo.

`<default>` : permite preencher previamente o campo com um valor padrão ao criar entidades. O valor não será um valor SQL padrão.

`<sqldefault>` : permite que você tenha um valor adicionado ao criar um campo. Esse valor aparece como um resultado SQL. Durante uma atualização de schema, somente os novos registros serão afetados por esse valor.

### Enumerações {#enumerations}

#### Abrir lista discriminada {#free-enumeration}

A variável **userEnum** property permite definir uma lista discriminada aberta para armazenar e exibir os valores inseridos por meio desse campo.

A sintaxe é a seguinte:

`userEnum="name of enumeration"`

Esses valores são mostrados em uma lista suspensa no formulário de entrada:

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>No console do cliente Adobe Campaign, navegue até o **[!UICONTROL Administration > Enumerations]** pasta do Explorer para gerenciar enumerações.

#### Definir enumeração {#set-enumeration}

A variável **enum** property permite definir uma enumeração fixa usada quando a lista de valores possíveis é conhecida antecipadamente.

A variável **enum** atributo refere-se à definição de uma classe de enumeração preenchida no schema fora do elemento principal.

As enumerações permitem que o usuário selecione um valor em uma lista suspensa em vez de inserir o valor em um campo de entrada regular:

![](assets/d_ncs_integration_schema_enum.png)

Exemplo de uma declaração de enumeração no schema de dados:

```sql
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

Uma enumeração é declarada fora do elemento principal por meio de **`<enumeration>`** elemento.

As propriedades de enumeração são as seguintes:

* **baseType**: tipo de dados associado aos valores
* **rótulo**: descrição da enumeração
* **name**: nome da enumeração
* **padrão**: valor padrão da enumeração

Os valores da lista discriminada são declarados na variável **`<value>`** elemento com os seguintes atributos:

* **name**: nome do valor armazenado internamente
* **rótulo**: rótulo exibido na interface gráfica

#### enumeração dbenum {#dbenum-enumeration}

*O **dbeno** permite definir uma enumeração cujas propriedades são semelhantes às da variável **enum** propriedade.

No entanto, a **name** O atributo não armazena o valor internamente, ele armazena um código que permite estender as tabelas relacionadas sem modificar o schema.

Essa lista discriminada é usada para especificar a natureza das campanhas, por exemplo.

![](assets/d_ncs_configuration_schema_dbenum.png)

### Exemplo {#example}

Este é o nosso exemplo de schema com as propriedades preenchidas:

```sql
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

A variável **desvinculado** O atributo com o valor &quot;true&quot; permite preencher um elemento de coleção.

**Exemplo**: definição do **`<group>`** elemento de coleção no esquema.

```sql
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

Com projeção do conteúdo XML:

```sql
<group label="Group1"/>
<group label="Group2"/>
```

## Referência com XPath {#referencing-with-xpath}

A linguagem XPath é usada no Adobe Campaign para referenciar um elemento ou atributo que pertence a um schema de dados.

XPath é uma sintaxe que permite localizar um nó na árvore de um documento XML.

Os elementos são designados pelo nome e os atributos são designados pelo nome precedido pelo caractere &quot;@&quot;.

**Exemplo**:

* **@email**: seleciona o email,
* **location/@city**: seleciona o atributo &quot;city&quot; na variável **`<location>`** element
* **../@email**: seleciona o endereço de email do elemento pai do elemento atual
* **grupo`[1]/@label`**: seleciona o atributo &quot;label&quot; que é filho do primeiro **`<group>`** elemento de coleção
* **grupo`[@label='test1']`**: seleciona o atributo &quot;label&quot; que é filho do **`<group>`** elemento e contém o valor &quot;test1&quot;

>[!NOTE]
>
>Uma restrição adicional é adicionada quando o caminho cruza um subelemento. Nesse caso, a seguinte expressão deve ser colocada entre colchetes:
>
>* **location/@city** não é válido; use **`[location/@city]`**
>* **`[@email]`** e **@email** são equivalentes
>

Também é possível definir expressões complexas, como as seguintes operações aritméticas:

* **@gender+1**: adiciona 1 ao conteúdo do **gênero** atributo,
* **@email + &#39;(&#39;+@created+&#39;)&#39;**: constrói uma cadeia de caracteres pegando o valor do endereço de email adicionado à data de criação entre parênteses (para o tipo de cadeia de caracteres, coloque a constante entre aspas).

Foram adicionadas funções de alto nível às expressões, a fim de enriquecer o potencial dessa linguagem.

Você pode acessar a lista de funções disponíveis por meio de qualquer editor de expressão no console do cliente do Adobe Campaign:

![](assets/d_ncs_integration_schema_function.png)

**Exemplo**:

* **GetDate()**: retorna a data atual
* **Year(@created)**: retorna o ano da data contida no atributo &quot;created&quot;
* **GetEmailDomain(@email)**: retorna o domínio do endereço de email

## Criação de uma string através do comando compute string {#building-a-string-via-the-compute-string}

A **String de cálculo** é uma expressão XPath usada para construir uma cadeia de caracteres que representa um registro em uma tabela associada ao esquema. **String de cálculo** é usado principalmente na interface gráfica para exibir o rótulo de um registro selecionado.

A variável **String de cálculo** é definido por meio da variável **`<compute-string>`** elemento no elemento principal do schema de dados. Um **expr** O atributo contém uma expressão XPath para calcular a exibição.

**Exemplo**: cadeia de caracteres de cálculo da tabela de recipients.

```sql
<srcSchema name="recipient" namespace="nms">  
  <element name="recipient">
    <compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')' "/>
    ...
  </element>
</srcSchema>
```

Resultado da cadeia de caracteres calculada para um destinatário: **Tom John (john.doe@aol.com)**

>[!NOTE]
>
>Se o esquema não contiver uma Cálculo de cadeia de caracteres, uma Cálculo de cadeia de caracteres será preenchida por padrão com os valores da chave primária do esquema.


## Saiba mais

Navegue pelos links a seguir para saber mais:

* [Introdução a esquemas](about-schema-reference.md)
* [Mapeamento de banco de dados](database-mapping.md)
* [Gerenciamento de link](database-links.md)
* [Gerenciamento de chaves](database-keys.md)
* [Modelo de dados do Campaign](about-data-model.md)