---
product: campaign
title: Exemplos de código JavaScript em workflows
description: Estes exemplos mostram como você pode usar o código JavaScript em um workflow
audience: workflow
content-type: reference
topic-tags: advanced-management
source-git-commit: fa3a3e1801738928876734aa42342f0a5b49e320
workflow-type: tm+mt
source-wordcount: '1768'
ht-degree: 2%

---

# Exemplos de código JavaScript em workflows{#javascript-in-workflows}

![](../../assets/common.svg)

Estes exemplos mostram como você pode usar o código JavaScript em um workflow:

* [Gravar no banco de dados](#write-example)
* [Consultar o banco de dados](#read-example)
* [Acione um workflow usando um método SOAP estático](#trigger-example)
* [Interagir com o banco de dados, usando um método SOAP não estático](#interact-example)

[Saiba mais](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html) sobre métodos SOAP estáticos e não estáticos.

Nesses exemplos, a extensão ECMAScript for XML (E4X) é usada. Com essa extensão, você pode combinar chamadas do JavaScript e primitivos XML no mesmo script.

Para experimentar estes exemplos, siga estas etapas:

1. Crie um workflow e adicione essas atividades ao workflow:
   1. Iniciar atividade
   1. Atividade de código JavaScript
   1. Finalizar atividade

   [Saiba mais](building-a-workflow.md) sobre como criar workflows.

1. Adicione o código JavaScript a uma atividade . [Saiba mais](advanced-parameters.md).
1. Salve o workflow.
1. Teste os exemplos:
   1. Inicie o workflow. [Saiba mais](starting-a-workflow.md).
   1. Abra o diário. [Saiba mais](monitoring-workflow-execution.md#displaying-logs).

## Exemplo 1: gravar no banco de dados{#write-example}

Para gravar no banco de dados, você pode usar a variável `Write` no método `xtk:session` schema:

1. Componha uma solicitação de gravação em XML.

1. Escreva o registro:

   1. Chame o `Write` no método `xtk:session` esquema.

      >[!IMPORTANT]
      > Se você usar o Adobe Campaign v8, recomendamos que você use o mecanismo de preparo com a **Assimilação** e **Atualização/exclusão de dados** APIs para o `Write` em uma tabela Snowflake. [Leia mais](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target=&quot;_blank&quot;}.

   1. Transmita o código XML como um argumento para a solicitação de gravação.

### Etapa 1: compor uma solicitação de gravação

Você pode adicionar, atualizar e excluir registros.

#### Inserir um registro

Porque a variável `insert` é a operação padrão, não é necessário especificá-la.

Especifique essas informações como atributos XML:

* O schema da tabela a ser modificada
* Os campos de tabela a serem preenchidos

Exemplo:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>
```

#### Atualizar um registro

Use o `_update` operação. [Saiba mais](../../configuration/using/data-oriented-apis.md).

Especifique essas informações como atributos XML:

* O schema da tabela a ser modificada
* Os campos da tabela a serem atualizados
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

Use o `DeleteCollection` método . [Saiba mais](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html).

Especifique estas informações:

* O schema da tabela a ser modificada
* O `where` cláusula necessária para identificar o registro a ser atualizado, na forma de um elemento XML

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

Chame o não estático `Write` no método `xtk:session` schema:

```javascript
xtk.session.Write(myXML)
```

Nenhum valor é retornado para este método.

Adicione o código completo a uma atividade JavaScript code no workflow:

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

Para consultar o banco de dados, você pode usar o `xtk:queryDef` método da instância:

1. Componha uma consulta em XML.
1. Crie um objeto de consulta.
1. Execute a consulta.

### Etapa 1: compor um query

Especifique o código XML para um `queryDef` entidade.

Sintaxe:

```xml
<queryDef schema="nms:recipient" operation="">
    <!-- select, where, and orderBy clauses as XML elements -->
</queryDef>
```

Especifique estas informações:

* O schema da tabela a ser lida
* A operação
* As colunas a serem retornadas, em um `select` cláusula
* As condições, em um `where` cláusula
* Os critérios de filtragem, em uma `orderBy` cláusula

Você pode usar estas operações:

| Operação | Resultado |
| --- | --- |
| `select` | Zero ou mais elementos são retornados como uma coleção. |
| `getIfExists` | Um elemento é retornado. Se nenhum elemento correspondente existir, um elemento vazio será retornado. |
| `get` | Um elemento é retornado. Se nenhum elemento de correspondência existir, um erro será retornado. |
| `count` | O número de registros correspondentes é retornado no formulário de um elemento com um `count` atributo. |

Escreva o `select`, `where`e `orderBy` cláusulas como elementos XML:

* `select` cláusula

   Especifique as colunas a serem retornadas. Por exemplo, para selecionar o nome e sobrenome da pessoa, escreva este código:

   ```xml
   <select>
       <node expr="@firstName"/>
       <node expr="@lastName"/>
   </select>
   ```

   Com o `nms:recipient` , os elementos são retornados neste formulário:

   ```xml
   <recipient firstName="Bo" lastName="Didley"/>
   ```

* `where` cláusula

   Para especificar condições, use uma `where` cláusula. Por exemplo, para selecionar os registros localizados na variável **Treinamento** , você pode gravar este código:

   ```xml
   <where>
       <condition expr="[folder/@label]='Training'"/>
   </where>
   ```

   Ao combinar várias expressões, use o operador booleano na primeira expressão. Por exemplo, para selecionar todas as pessoas chamadas Isabel Garcia, você pode escrever este código:

   ```xml
   <condition boolOperator="AND" expr="@firstName='Isabel'"/>
   <condition expr="@lastName='Garcia'"/>
   ```

* `orderBy` cláusula

   Para classificar o conjunto de resultados, especifique o `orderBy` cláusula como um elemento XML com a variável `sortDesc` atributo. Por exemplo, para classificar os últimos nomes em ordem crescente, você pode escrever este código:

   ```xml
   <orderBy>
       <node expr="@lastName> sortDesc="false"/>
   </orderBy>
   ```

### Etapa 2: criar um objeto de consulta

Para criar uma entidade a partir do código XML, use o `create(`*`content`*`)` método :

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="select">
    …
    </queryDef>)
```

Coloque o prefixo `create(`*`content`*`)` com o schema da entidade a ser criada.

O *`content`* é um argumento de string e é opcional. Esse argumento contém o código XML que descreve a entidade.

### Etapa 3: executar a consulta

Siga estas etapas:

1. Chame o `ExecuteQuery` no método `queryDef` entidade:

   ```javascript
   var res = query.ExecuteQuery()
   ```

1. Processar os resultados:
   1. Iterar sobre os resultados da `select` , usando uma construção de loop.
   1. Teste os resultados usando o `getIfExists` operação.
   1. Conte os resultados usando a `count` operação.

#### Resultados de um `select` operation

Todas as correspondências são retornadas como uma coleção:

```xml
<recipient-collection>
    <recipient email="jane.smith@mycompany.com">
    <recipient email="john.harris@mycompany.com">
</recipient-collection>
```

Para iterar os resultados, use o `for each` loop:

```javascript
for each (var rcp in res:recipient)
    logInfo(rcp.@email)
```

O loop inclui uma variável de recipient local. Para cada recipient que é retornado na coleção de recipients, o email do recipient é impresso. [Saiba mais](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html) sobre o `logInfo` .

#### Resultados de um `getIfExists` operation

Cada correspondência é retornada como um elemento:

```xml
<recipient id="52,378,079">
```

Se não houver correspondência, um elemento vazio será retornado:

```xml
<recipient/>
```

Você pode consultar o nó da chave primária, por exemplo, a variável `@id` atributo:

```javascript
if (res.@id !=undefined)
    { // match was found
    …
    }
```

#### Resultado de um `get` operation

Uma correspondência é retornada como um elemento:

```xml
<recipient id="52,378,079">
```

Se não houver correspondência, um erro será retornado.

>[!TIP]
>
>Se você sabe que há uma correspondência, use a variável `get` operação. Caso contrário, use a `getIfExists` operação. Se você usar essa prática recomendada, os erros revelarão problemas inesperados. Se você usar a variável `get` não use a `try…catch` instrução. O problema é tratado pelo processo de tratamento de erros do workflow.

#### Resultado de um `count` operation

Um elemento com a variável `count` é retornado:

```xml
<recipient count="200">
```

Para usar o resultado, consulte `@count` atributo:

```javascript
if (res.@count > 0)
    { // matches were found
    …
    }
```

Para o `select` , adicione este código a uma atividade JavaScript code no workflow:

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

Porque a variável `select` é a operação padrão, não é necessário especificá-la.

Este vídeo mostra como ler a partir do banco de dados:
>[!VIDEO](https://video.tv.adobe.com/v/18475/?learn=on)

## Acionar um workflow {#trigger-example}

Você pode acionar workflows programaticamente, por exemplo, em workflows técnicos ou para processar informações que um usuário inseriu em uma página de aplicativo Web.

O acionamento do workflow funciona por meio do uso de eventos. Você pode usar esses recursos para eventos:

* Para publicar um evento, você pode usar a variável `PostEvent` método . [Saiba mais](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html).
* Para receber um evento, você pode usar a variável **[!UICONTROL External signal]** atividade . [Saiba mais](external-signal.md).

Você pode acionar fluxos de trabalho de diferentes maneiras:

* Você pode acionar um workflow em linha, ou seja, a partir do script principal de um **[!UICONTROL JavaScript code]** atividade .
* Você pode acionar um workflow ao concluir outro:
   * Adicione um script de inicialização ao **[!UICONTROL End]** atividade do workflow inicial.
   * Adicione o **[!UICONTROL External signal]** no início do workflow do target.

      Após a conclusão do fluxo de trabalho inicial, um evento é postado. A transição de saída é ativada e as variáveis de evento são preenchidas. Em seguida, o evento é recebido pelo workflow do target.

      >[!TIP]
      >
      >Como prática recomendada, ao adicionar um script a uma atividade, coloque o nome da atividade em hífens duplos, por exemplo, `-- end --`. [Saiba mais](workflow-best-practices.md) sobre as práticas recomendadas de workflow.

Sintaxe do `PostEvent` método :

```javascript
PostEvent(
    String     //ID of the target workflow
    String     //Name of the target activity
    String     //Name of the transition to be activated in case of multiple transitions
    XML        //Event parameters, in the <variables/> element
    Boolean    //To trigger the target workflow only once, set this parameter to true.
)
```

Neste exemplo, após a conclusão do workflow, um texto curto é passado para a função **sinal** da **wkfExampleReceiver** fluxo de trabalho:

```javascript
var strLabel = "Adobe Campaign, Marketing that delivers"
xtk.workflow.PostEvent(
    "wkfExampleReceiver",
    "signal",
    "",
    <variables strLine={strLabel}/>,
    false)
```

Como o último parâmetro é definido como `false`, o **wkfExampleReceiver** O fluxo de trabalho é acionado toda vez que o fluxo de trabalho inicial é concluído.

Ao acionar workflows, lembre-se dos seguintes princípios:

* O `PostEvent` O comando é executado de forma assíncrona. O comando é colocado na fila do servidor. O método retorna após a publicação do evento.
* O workflow do target deve ser iniciado. Caso contrário, um erro será gravado no arquivo de log.
* Se o workflow do target for suspenso, a função `PostEvent` é enfileirado até que o workflow seja retomado.
* A atividade acionada não requer que uma tarefa esteja em andamento.

Este vídeo mostra como usar métodos de API estática:
>[!VIDEO](https://video.tv.adobe.com/v/18481/?learn=on)

Este vídeo mostra como acionar fluxos de trabalho:
>[!VIDEO](https://video.tv.adobe.com/v/18485/?learn=on)

## Interagir com o banco de dados {#interact-example}

Estes exemplos mostram como executar estas ações:

* Use o `get` e `create` métodos em schemas para usar métodos SOAP não estáticos
* Criar métodos que executam consultas SQL
* Use o `write` método para inserir, atualizar e excluir registros

Siga estas etapas:

1. Defina a query:

   * Recupere uma entidade usando o `create` no schema correspondente, por exemplo, a variável `xtk:workflow` esquema. [Saiba mais](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html).
   * Use o `queryDef` para emitir uma consulta SQL.

1. Execute a consulta usando o `ExecuteQuery` método . [Saiba mais](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html).

   Use o `for each` para recuperar os resultados.

### Sintaxe do `queryDef` com um `select` cláusula

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

### `Create` método

#### Exemplo 1: selecionar registros e gravar no diário

Os nomes internos dos workflows localizados na variável **wfExamples** estão selecionadas. Os resultados são classificados por nome interno, em ordem crescente e gravados no diário.

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

O nome, o sobrenome, o email e a ID de todos os recipients que recebem o nome Chris Smith são selecionados. Os resultados são classificados por email, em ordem crescente e gravados no diário. A `delete` é usada para excluir os registros selecionados.

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

#### Exemplo 3: selecionar registros e gravar no diário

Neste exemplo, um método não estático é usado. O email e o ano de nascimento de todos os recipients cujas informações estão armazenadas no **1234** e cujo nome de domínio de email começa com &quot;adobe&quot; são selecionadas. Os resultados são classificados por data de nascimento em ordem decrescente. O email dos recipients é gravado no diário.

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

### `Write` método

Você pode inserir, atualizar e excluir registros. Você pode usar o `Write` em qualquer schema no Adobe Campaign. Como esse método é estático, não é necessário criar um objeto. Você pode usar estas operações:

* O `update` operation
* O `insertOrUpdate` com a `_key` argumento para identificar o registro a ser atualizado

   Se você não especificar a variável **Recipients** , em seguida, se houver uma correspondência, o registro será atualizado em qualquer subpasta. Caso contrário, o registro será criado na raiz **Recipients** pasta.

* O `delete` operation

>[!IMPORTANT]
> Se você usar o Adobe Campaign v8, recomendamos que você use o mecanismo de preparo com a **Assimilação** e **Atualização/exclusão de dados** APIs para o `Write` em uma tabela Snowflake. [Leia mais](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target=&quot;_blank&quot;}.

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

Este exemplo combina um método estático e um método não estático.

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

* [APIs orientadas a dados](../../configuration/using/data-oriented-apis.md)
* [Modelos e scripts JavaScript](javascript-scripts-and-templates.md)
* [Métodos SOAP em JavaScript](../../configuration/using/soap-methods-in-javascript.md)

### Documentação da API

* [Exemplos de chamadas SOAP](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html)
* Métodos:
   * [Criar](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html)
   * [DeleteCollection](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html)
   * [ExecuteQuery](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html)
   * [PostEvent](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html)
   * [Gravar](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-Write.html)
* [função logInfo](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html)