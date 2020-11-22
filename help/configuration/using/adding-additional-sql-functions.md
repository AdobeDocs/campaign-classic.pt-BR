---
solution: Campaign Classic
product: campaign
title: Adição de funções SQL extras
description: Adição de funções SQL extras
audience: configuration
content-type: reference
topic-tags: api
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1021'
ht-degree: 1%

---


# Adição de funções SQL extras{#adding-additional-sql-functions}

## Introdução {#introduction}

A Adobe Campaign permite que o usuário defina **suas próprias funções** que podem acessar funções SQL, tanto aquelas oferecidas pelo banco de dados quanto aquelas que ainda não estão disponíveis no console. Isso é útil para funções de agregação (média, máxima, soma), por exemplo, que só podem ser calculadas no servidor ou quando o banco de dados fornece uma maneira mais fácil de implementar certas funções, em vez de gravar &quot;manualmente&quot; a expressão no console (por exemplo, gerenciamento de datas).

Esse mecanismo também pode ser usado se você quiser usar uma função SQL de mecanismo de banco de dados recente ou incomum, que ainda não é oferecida pelo console do Adobe Campaign.

Depois que essas funções forem adicionadas, elas aparecerão no editor de expressões da mesma forma que outras funções predefinidas.

>[!IMPORTANT]
>
>As chamadas de função SQL no console não são mais enviadas naturalmente para o servidor. O mecanismo descrito aqui se torna, portanto, **a única maneira de chamar** o servidor de função SQL não planejado.

## Instalação {#installation}

As funções a serem adicionadas estão em um arquivo **&quot;package&quot; no formato** XML, cuja estrutura é detalhada no parágrafo a seguir.

Para instalá-lo do console, selecione as opções de pacote **** Ferramentas/Avançado/Importação no menu e, em seguida, **[!UICONTROL Install from file]** e siga as instruções no assistente de importação.

>[!IMPORTANT]
>
>Aviso: mesmo se a lista de funções importadas for exibida imediatamente no editor de funções, elas não poderão ser usadas até que o Adobe Campaign seja reiniciado.

## Estrutura geral do pacote a importar {#general-structure-of-package-to-import}

As funções a serem adicionadas podem ser encontradas no arquivo **** &quot;package&quot; no formato XML. Aqui está um exemplo:

```
<?xml version="1.0" encoding='ISO-8859-1' ?>
<!-- ===========================================================================
  Additional SQL functions for Adobe Campaign
  ========================================================================== -->
<package
  namespace   = "nms"
  name        = "package-additional-funclist"
  label       = "Additional functions"
  buildVersion= "6.1"
  buildNumber = "10000">

  <entities schema="xtk:funcList">
    <funcList name="myList" namespace="cus">
      <group name="date" label="Personalized date">
        <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
                  minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
          <providerPart provider="MSSQL,Sybase,PostgreSQL" body="extract(year from age($1))-18"/>
        </function>
      </group>
    </funcList>
  </entities>
</package>
```

* O **nome**, a **namespace** e o **rótulo** são apenas para fins informativos. Eles permitem que você visualização um resumo do pacote na lista de pacotes instalados (pacotes Explorer/Administration/Package management/Installed).
* Os campos **buildVersion** e **buildNumber** são obrigatórios. Elas devem corresponder ao número do servidor ao qual o console está conectado. Essas informações podem ser encontradas na caixa &quot;Ajuda/Sobre&quot;.
* Os seguintes blocos, **entidades** e **funclist** são obrigatórios. Em funcList, os campos &quot;nome&quot; e &quot;namespace&quot; são obrigatórios, mas seu nome é deixado ao critério do usuário e eles designam exclusivamente a lista de função.

   Isso significa que se outra lista de funções com o mesmo par de namespace/nome (aqui &quot;cus::myList&quot;) for importada, as funções importadas anteriormente serão excluídas. Por outro lado, se você alterar esse par de namespace/nome, a nova série de funções importadas será adicionada à anterior.

* O elemento **group** permite especificar o grupo de funções no qual as funções importadas aparecerão no editor de funções. O atributo @name pode ser um nome que já existe (nesse caso, as funções serão adicionadas ao grupo considerado) ou um novo nome (nesse caso, ele aparecerá em um novo grupo).
* Lembrete: os valores possíveis para o atributo @name no `<group>` elemento são:

   ```
     name="aggregate"      ( label="Aggregates"         )
     name="string"             ( label="String"           )
     name="date"               ( label="Date"             )
     name="numeric"          ( label="Numeric"        )
     name="geomarketing" ( label="Geomarketing"     )
     name="other"              ( label="Others"           )
     name="window"          ( label="Windowing functions" )
   ```

>[!IMPORTANT]
>
>Certifique-se de concluir o atributo @label: esse é o nome que será exibido na lista das funções disponíveis. Se você não inserir nada, o grupo não terá um nome. No entanto, se você inserir um nome diferente do existente, o nome do grupo inteiro será alterado.

Se desejar adicionar funções a vários grupos diferentes, é possível fazer com que vários `<group>` elementos sejam rastreados na mesma lista.

Finalmente, um `<group>` elemento pode conter a definição de uma ou várias funções, que é a finalidade do arquivo de pacote. O `<function>` elemento é detalhado no parágrafo a seguir.

## Descritor de função &lt;função>&lt;/função> {#function-descriptor--function-}

O caso aqui apresentado é um caso geral em que pretendemos assegurar a implementação **da** função.

Abaixo está um exemplo de uma função de &quot;maturidade relativa&quot; que, usando uma idade, indica por quantos anos a pessoa foi considerada madura.

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

O campo **@name** refere-se ao nome da função e &quot;args&quot; é a lista de parâmetros que serão exibidos na descrição. Nesse caso, a função aparecerá como &quot;relativeMaturity ( `<age>` )&quot; na janela de seleção da função.

* **help** é o campo exibido na parte inferior da janela do editor de expressões.
* **@display** é uma mensagem informativa.

   >[!NOTE]
   >
   >Nos atributos @help e @display, a string &quot;$1&quot; representa o nome que foi dado no primeiro parâmetro de função (aqui, &quot;Idade&quot;). $2, $3... representaria os seguintes parâmetros. No atributo @body detalhado abaixo, $1 designa o valor do argumento passado para a função durante a chamada.

   >[!NOTE]
   >
   >A descrição deve ser uma string de caracteres XML válidos: observe o uso de &#39;&lt;&#39; e &#39;>&#39; em vez de &lt; e >.

* **@type** é o tipo de retorno da função e é um valor padrão (long, string, byte, datetime...). Se for omitido, o servidor determinará o melhor tipo entre os tipos disponíveis na expressão que implementa a função.
* **@minArgs** e **maxArgs** designam o número de parâmetros (mínimo e máximo) para um parâmetro. Por exemplo, para uma função com 2 parâmetros, minArgs e maxArgs serão 2 e 2. Para 3 parâmetros, mais 1 opcional, eles serão 3 e 4, respectivamente.
* Finalmente, o elemento **providerPart** fornece a implementação da função.

   * O atributo **provider** é obrigatório e especifica os sistemas de banco de dados para os quais a implementação é fornecida. Como mostrado no exemplo, quando as sintaxes de expressão ou as funções subjacentes diferem, as implementações alternativas podem ser fornecidas de acordo com o banco de dados.
   * O atributo **@body** contém a implementação da função. Observe que: essa implementação deve ser uma expressão, na linguagem do banco de dados (não um bloco de código). Dependendo dos bancos de dados, as expressões podem ser subquery (&quot;(selecione a coluna da tabela onde...)&quot;) retornando somente um único valor. Por exemplo, esse é o caso no Oracle (o query deve ser escrito entre parênteses).

   >[!NOTE]
   >
   >Se for provável que apenas um ou dois bancos de dados sejam consultados pela função definida, nós sempre poderemos fornecer apenas as definições correspondentes a esses bancos de dados.

## Descritor da função &#39;Pass-through&#39; {#pass-through--function-descriptor}

Um descritor de função especial é o bloco **&quot;pass-through&quot;** , com um sistema de banco de dados &quot;provedor&quot; não especificado. Nesse caso, a implementação &quot;body&quot; só pode conter uma única chamada de função com uma sintaxe que não depende do banco de dados usado. Enquanto isso, o bloco &quot;ProviderPart&quot; é único.

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

Nesse caso, adicionar uma função somente serve para tornar uma função de banco de dados que não estaria disponível por padrão, agora visível para o cliente.

## Exemplos {#examples}

Outros exemplos de função podem ser encontrados no pacote predefinido &quot;xtkdatakitfuncList.xml&quot;.
