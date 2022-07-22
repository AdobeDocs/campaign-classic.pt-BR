---
product: campaign
title: Exemplos de código JavaScript em workflows
description: Estes exemplos mostram como é possível usar o código JavaScript em um workflow
feature: Workflows
exl-id: 7213ea64-3dec-4b16-9d93-4ae941ddfaa7
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Exemplos de código JavaScript em workflows{#javascript-in-workflows}

![](../../assets/v7-only.svg)

Estes exemplos mostram como é possível usar o código JavaScript em um workflow:

* [Gravar no banco de dados](#write-example)
* [Consultar o banco de dados](#read-example)
* [Acionar um workflow usando um método SOAP estático](#trigger-example)
* [Interagir com o banco de dados usando um método SOAP não estático](#interact-example)

[Saiba mais](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html?lang=pt-BR) sobre métodos SOAP estáticos e não estáticos.

Nesses exemplos, a extensão ECMAScript for XML (E4X) é usada. Com esta extensão, é possível combinar chamadas de JavaScript e primitivos de XML no mesmo script.

Para experimentar estes exemplos, siga estas etapas:

1. Crie um workflow e adicione essas atividades ao workflow:
   1. Iniciar atividade
   1. Atividade de código JavaScript
   1. Finalizar atividade

   [Saiba mais](building-a-workflow.md) sobre a criação de workflows.

1. Adicione o código JavaScript a uma atividade. [Saiba mais](advanced-parameters.md).
1. Salve o workflow.
1. Teste os exemplos:
   1. Inicie o workflow. [Saiba mais](starting-a-workflow.md).
   1. Abra o journal. [Saiba mais](monitoring-workflow-execution.md#displaying-logs).

## Exemplo 1: gravar no banco de dados{#write-example}

Para gravar no banco de dados, é possível usar o método estático `Write` no schema `xtk:session`:

1. Componha uma solicitação de gravação em XML.

1. Grave o registro:

   1. Chame o método `Write` no schema `xtk:session`.

      >[!IMPORTANT]
      > Se estiver usando o Adobe Campaign v8, recomendamos o uso do mecanismo de preparo com as APIs de **Assimilação** e **Atualização/exclusão de dados** para o método `Write` em uma tabela Snowflake. [Leia mais](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html?lang=pt-BR){target=&quot;_blank&quot;}.

   1. Transmita o código XML como argumento para a solicitação de gravação.

### Etapa 1: compor uma solicitação de gravação

É possível adicionar, atualizar e excluir registros.

#### Inserir um registro

Visto que `insert` é a operação padrão, não é necessário especificá-la.

Especifique essas informações como atributos XML:

* O schema da tabela a ser modificada
* Os campos a serem preenchidos na tabela

Exemplo:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>
```

#### Atualizar um registro

Use a operação `_update`. [Saiba mais](../../configuration/using/data-oriented-apis.md).

Especifique essas informações como atributos XML:

* O schema da tabela a ser modificada
* Os campos a serem atualizados na tabela 
* O argumento principal necessário para identificar o registro a ser atualizado

Exemplo:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    status="Client"
    email="isabel.garcia@mycompany.com"
    operation="_update"
    _key="@email"/>
```

#### Excluir um registro

Use o método `DeleteCollection`. [Saiba mais](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html?lang=pt-BR).

Especifique estas informações:

* O schema da tabela a ser modificada
* A cláusula `where` necessária para identificar o registro a ser atualizado, na forma de um elemento XML

Exemplo:

```javascript
xtk.session.DeleteCollection(
    "nms:recipient",
    <where>
        <condition expr="[@email] = 'isabel.garcia@mycompany.com'"/>
    </where>,
    false
    )
```

### Etapa 2: gravar o registro

Chame o método `Write` não estático no schema `xtk:session`:

```javascript
xtk.session.Write(myXML)
```

Nenhum valor é retornado para este método.

Adicione o código completo a uma atividade de código JavaScript no workflow:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>

xtk.session.Write(myXML)
```

Este vídeo mostra como gravar no banco de dados:
>[!VIDEO](https://video.tv.adobe.com/v/18472/?learn=on)

## Exemplo 2: consultar o banco de dados{#read-example}

Para consultar o banco de dados, é possível usar o método da instância `xtk:queryDef` não estático:

1. Componha uma consulta em XML.
1. Crie um objeto de consulta.
1. Execute a consulta.

### Etapa 1: compor uma consulta

Especifique o código XML para uma entidade `queryDef`.

Sintaxe:

```xml
<queryDef schema="nms:recipient" operation="">
    <!-- select, where, and orderBy clauses as XML elements -->
</queryDef>
```

Especifique estas informações:

* O schema da tabela a ser lida
* A operação
* As colunas a serem retornadas, em uma cláusula `select` 
* As condições, em uma cláusula `where` 
* Os critérios de filtragem, em uma cláusula `orderBy` 

É possível usar estas operações:

| Operação | Resultado |
| --- | --- |
| `select` | Zero ou mais elementos são retornados como uma coleção. |
| `getIfExists` | Um elemento é retornado. Se nenhum elemento correspondente existir, um elemento vazio será retornado. |
| `get` | Um elemento é retornado. Se nenhum elemento correspondente existir, um erro será retornado. |
| `count` | O número de registros correspondentes é retornado na forma de um elemento com um atributo `count`. |

Insira as cláusulas `select`, `where` e `orderBy` como elementos XML:

* Cláusula `select`

   Especifique as colunas a serem retornadas. Por exemplo, para selecionar o nome e sobrenome da pessoa, insira este código:

   ```xml
   <select>
       <node expr="@firstName"/>
       <node expr="@lastName"/>
   </select>
   ```

   Com o schema `nms:recipient`, os elementos são retornados desta forma:

   ```xml
   <recipient firstName="Bo" lastName="Didley"/>
   ```

* Cláusula `where`

   Para especificar condições, use uma cláusula `where`. Por exemplo, para selecionar os registros localizados na pasta **Treinamento**, é possível inserir este código:

   ```xml
   <where>
       <condition expr="[folder/@label]='Training'"/>
   </where>
   ```

   Ao combinar várias expressões, use o operador booleano na primeira expressão. Por exemplo, para selecionar todas as pessoas chamadas Isabel Garcia, é possível inserir este código:

   ```xml
   <condition boolOperator="AND" expr="@firstName='Isabel'"/>
   <condition expr="@lastName='Garcia'"/>
   ```

* Cláusula `orderBy`

   Para classificar o conjunto de resultados, especifique a cláusula `orderBy` como um elemento XML com o atributo `sortDesc`. Por exemplo, para classificar os sobrenomes em ordem crescente, é possível inserir este código:

   ```xml
   <orderBy>
       <node expr="@lastName> sortDesc="false"/>
   </orderBy>
   ```

### Etapa 2: criar um objeto de consulta

Para criar uma entidade a partir do código XML, use o método `create(`*`content`*`)`:

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="select">
    …
    </queryDef>)
```

Prefixe o método `create(`*`content`*`)` com o schema da entidade a ser criada.

O argumento *`content`* é um argumento de sequência, e é opcional. Esse argumento contém o código XML que descreve a entidade.

### Etapa 3: executar a consulta

Siga estas etapas:

1. Chame o método `ExecuteQuery` na entidade `queryDef`:

   ```javascript
   var res = query.ExecuteQuery()
   ```

1. Processe os resultados:
   1. Repita os resultados da operação `select`, usando uma construção de loop.
   1. Teste os resultados usando a operação `getIfExists`.
   1. Conte os resultados usando a operação `count`.

#### Resultados de uma operação `select`

Todas as correspondências são retornadas como uma coleção:

```xml
<recipient-collection>
    <recipient email="jane.smith@mycompany.com">
    <recipient email="john.harris@mycompany.com">
</recipient-collection>
```

Para repetir os resultados, use o loop `for each`:

```javascript
for each (var rcp in res:recipient)
    logInfo(rcp.@email)
```

O loop inclui uma variável de recipient local. Para cada recipient que é retornado na coleção de recipients, o email do recipient é impresso. [Saiba mais](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html?lang=pt-BR) sobre a função `logInfo`.

#### Resultados de uma operação `getIfExists` 

Cada correspondência é retornada como um elemento:

```xml
<recipient id="52,378,079">
```

Se não houver correspondência, um elemento vazio será retornado:

```xml
<recipient/>
```

É possível consultar o nó primário da chave, como por exemplo, o atributo `@id`:

```javascript
if (res.@id !=undefined)
    { // match was found
    …
    }
```

#### Resultado de uma operação `get` 

Uma correspondência é retornada como um elemento:

```xml
<recipient id="52,378,079">
```

Se não houver correspondência, um erro será retornado.

>[!TIP]
>
>Caso saiba que há uma correspondência, use a operação `get`. Caso contrário, use a operação `getIfExists`. Ao utilizar esta prática recomendada, os erros revelarão problemas inesperados. Caso utilize a operação `get`, não use a instrução `try…catch`. O problema é tratado pelo processo de tratamento de erros do workflow.

#### Resultado de uma operação `count` 

Um elemento com o atributo `count` é retornado:

```xml
<recipient count="200">
```

Para usar o resultado, consulte o atributo `@count`:

```javascript
if (res.@count > 0)
    { // matches were found
    …
    }
```

Para a operação `select`, adicione este código a uma atividade de código JavaScript no workflow:

```javascript
var myXML =
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@firstName"/>
        <node expr="@lastName"/>
    </select>
</queryDef>

var query = xtk.queryDef.create(myXML)

var res = query.ExecuteQuery()

for each (var rcp in res.recipient)
    logInfo(rcp.@firstName + " " + rcp.@lastName)
```

Visto que `select` é a operação padrão, não é necessário especificá-la.

Este vídeo mostra como ler a partir do banco de dados:
>[!VIDEO](https://video.tv.adobe.com/v/18475/?learn=on)

## Acionar um workflow {#trigger-example}

É possível acionar workflows programaticamente, por exemplo, em workflows técnicos ou para processar informações que um usuário inseriu em uma página de aplicativo web.

O acionamento do workflow funciona por meio do uso de eventos. É possível usar estes recursos para eventos:

* Para publicar um evento, é possível usar o método estático `PostEvent`. [Saiba mais](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html?lang=pt-BR).
* Para receber um evento, é possível usar a atividade **[!UICONTROL External signal]**. [Saiba mais](external-signal.md).

É possível acionar workflows de diferentes maneiras:

* É possível acionar um workflow em linha, ou seja, a partir do script principal de uma atividade **[!UICONTROL JavaScript code]**.
* É possível acionar um workflow ao concluir outro:
   * Adicione um script de inicialização à atividade **[!UICONTROL End]** do workflow inicial.
   * Adicione a atividade **[!UICONTROL External signal]** no início do workflow desejado.

      Após a conclusão do workflow inicial, um evento é postado. A transição de saída é ativada e as variáveis do evento são preenchidas. Em seguida, o evento é recebido pelo workflow desejado.

      >[!TIP]
      >
      >Como prática recomendada, ao adicionar um script a uma atividade, coloque o nome da atividade entre hifens duplos. Por exemplo: `-- end --`. [Saiba mais](workflow-best-practices.md) sobre as práticas recomendadas de workflow.

Sintaxe do método `PostEvent`:

```javascript
PostEvent(
    String     //ID of the target workflow
    String     //Name of the target activity
    String     //Name of the transition to be activated in case of multiple transitions
    XML        //Event parameters, in the <variables/> element
    Boolean    //To trigger the target workflow only once, set this parameter to true.
)
```

Neste exemplo, após a conclusão do workflow, um texto curto é passado para a atividade de **sinal** do workflow **wkfExampleReceiver**:

```javascript
var strLabel = "Adobe Campaign, Marketing that delivers"
xtk.workflow.PostEvent(
    "wkfExampleReceiver",
    "signal",
    "",
    <variables strLine={strLabel}/>,
    false)
```

Como o último parâmetro é definido como `false`, o workflow **wkfExampleReceiver** é acionado toda vez que o workflow inicial é concluído.

Ao acionar workflows, lembre-se dos seguintes princípios:

* O comando `PostEvent` é executado de forma assíncrona. O comando é colocado na fila do servidor. O método retorna após a publicação do evento.
* O workflow desejado deve ser iniciado. Caso contrário, um erro será gravado no arquivo de log.
* Se o workflow desejado for suspenso, o comando `PostEvent` é enfileirado até que o workflow seja retomado.
* A atividade acionada não requer que uma tarefa esteja em andamento.

Este vídeo mostra como usar métodos de API estáticos:
>[!VIDEO](https://video.tv.adobe.com/v/18481/?learn=on)

Este vídeo mostra como acionar workflows:
>[!VIDEO](https://video.tv.adobe.com/v/18485/?learn=on)

## Interagir com o banco de dados {#interact-example}

Estes exemplos mostram como executar essas ações:

* Use os métodos `get` e `create` em schemas para usar métodos SOAP não estáticos
* Criar métodos que executam consultas SQL
* Use o método `write` para inserir, atualizar e excluir registros

Siga estas etapas:

1. Defina a consulta:

   * Recupere uma entidade usando o método `create` no schema correspondente, como por exemplo, o schema `xtk:workflow`. [Saiba mais](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html?lang=pt-BR).
   * Use o método `queryDef` para emitir uma consulta SQL.

1. Execute a consulta usando o método `ExecuteQuery`. [Saiba mais](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html?lang=pt-BR).

   Use o loop `for each` para recuperar os resultados.

### Sintaxe do método `queryDef` com uma cláusula `select` 

```xml
<queryDef schema="schema_key" operation="operation_type">
    <select>
        <node expr="expression1">
        <node sql="expression2">
    </select>
    <where> 
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </where>
    <orderBy>
        <node expr="expression1">
        <node sql="expression2">
    </orderBy>
    <groupBy>
        <node expr="expression1">
        <node sql="expression2">
    </groupBy>
    <having>
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </having>
</queryDef>
```

### Método `Create`

#### Exemplo 1: selecionar registros e gravar no journal

Os nomes internos dos workflows localizados na pasta **wfExamples** são selecionados. Os resultados são classificados por nome interno, em ordem crescente, e gravados no journal.

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="xtk:workflow" operation="select">
        <select>
            <node expr="@internalName"/>
        </select>
        <where>
            <condition expr="[folder/@name]='wfExamples'"/>
        </where>
        <orderBy>
            <node expr="@internalName" sortDesc="false"/>
        </orderBy>
    </queryDef>
    )

var res = query.ExecuteQuery()
for each (var w in res.workflow)
    logInfo(w.@internalName)
```

#### Exemplo 2: excluir registros

O nome, sobrenome, email e a ID de todos os recipients que se chamam Chris Smith são selecionados. Os resultados são classificados por email, em ordem crescente, e gravados no journal. A operação `delete` é usada para excluir os registros selecionados.

```javascript
// Build the query, create a query object and hold the object in a variable
var query = xtk.queryDef.create(
        <queryDef schema="nms:recipient" operation="select">
            <select>
                <node expr="@firstName"/>
                <node expr="@lastName"/>
                <node expr="@email"/>
                <node expr="@id"/>
            </select>
            <where>
                <condition expr="[folder/@label]='Recipients'"/>
                <condition expr="[@lastName]='Smith'"/>
                <condition expr="[@firstName]='Chris'"/>
            </where>
            <orderBy>
                <node expr="@email" sortDesc="false"/>
            </orderBy>
        </queryDef>
)

//Run the query using the ExecuteQuery method against the created object
var res = query.ExecuteQuery()

//Loop through the results, print out the person's name and email, then delete the records
for each (var rec in res.recipient)
    {
     logInfo("Delete record = Email: " + rec.@email + ', ' + rec.@firstName + ' ' + rec.@lastName)
     xtk.session.Write(<recipient xtkschema="nms:recipient" _operation="delete" id={rec.@id}/>)
    }
```

#### Exemplo 3: selecionar registros e gravar no journal

Neste exemplo, um método não estático é usado. O email e o ano de nascimento de todos os recipients cujas informações estão armazenadas na pasta **1234** e cujo nome de domínio de email começe com “adobe” são selecionados. Os resultados são classificados por data de nascimento, em ordem decrescente. O email dos recipients é gravado no journal.

```javascript
var query = xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@email"/>
        <node sql="sEmail"/>
        <node expr="Year(@birthDate)"/>
    </select>
    <where>
        <condition expr="[@folder-id] = 1234 and @domain like 'adobe%'"/>
        <condition sql="iFolderId = 1234 and sDomain like 'adobe%'"/>
    </where>
    <orderBy>
        <node expr="@birthDate" sortDesc="true"/>
    </orderBy>
</queryDef>
)

var res = query.ExecuteQuery()
for each (var w in res.recipient)
    logInfo(w.@email)
```

### Método `Write`

É possível inserir, atualizar e excluir registros. É possível usar o método `Write` em qualquer schema no Adobe Campaign. Como esse método é estático, não é necessário criar um objeto. É possível usar estas operações:

* A operação `update` 
* A operação `insertOrUpdate`, com o argumento `_key` para identificar o registro a ser atualizado

   Se não especificar a pasta **Recipients**, e houver uma correspondência, o registro será atualizado em qualquer subpasta. Caso contrário, o registro será criado na pasta raiz de **Recipients**.

* A operação `delete` 

>[!IMPORTANT]
> Caso utilize o Adobe Campaign v8, recomendamos utilizar o mecanismo de preparo com as APIs de **Assimilação** e **Atualização/exclusão de dados** para o método `Write` em uma tabela Snowflake. [Leia mais](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html?lang=pt-BR){target=&quot;_blank&quot;}.

#### Exemplo 1: inserir ou atualizar um registro

```javascript
xtk.session.Write(
<recipient
    xtkschema="nms:recipient"
    _operation="insertOrUpdate" _key="@email"
    lastName="Lennon"
    firstName="John"
    email="johnlennon@thebeatles.com"
/>
)
```

#### Exemplo 2: excluir registros

Este exemplo combina um método estático com um não estático.

```javascript
var query=xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@Id"/>
    </select>
    <where>
        <condition expr="[@email]='johnlennon@thebeatles.com'"/>
    </where>
</queryDef>
);

var res = query.ExecuteQuery()
for each (var w in res.recipient) {
xtk.session.Write(
    <recipient xtkschema="nms:recipient" _operation="delete" id={w.@id}/>
);
}
```

Este vídeo mostra como usar métodos de API não estáticos:
>[!VIDEO](https://video.tv.adobe.com/v/18477/?learn=on)

Este vídeo mostra um exemplo de uso de um método de API não estático em um workflow:
>[!VIDEO](https://video.tv.adobe.com/v/18476/?learn=on)

## Tópicos relacionados

* [APIs orientadas por dados](../../configuration/using/data-oriented-apis.md)
* [Modelos e scripts JavaScript](javascript-scripts-and-templates.md)
* [Métodos SOAP em JavaScript](../../configuration/using/soap-methods-in-javascript.md)

### Documentação da API

* [Exemplos de chamadas SOAP](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html?lang=pt-BR)
* Métodos:
   * [Create](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html?lang=pt-BR)
   * [DeleteCollection](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html?lang=pt-BR)
   * [ExecuteQuery](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html?lang=pt-BR)
   * [PostEvent](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html?lang=pt-BR)
   * [Write](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-Write.html?lang=pt-BR)
* [função logInfo](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html?lang=pt-BR)
