---
product: campaign
title: Adição de funções SQL extras
description: Adição de funções SQL extras
audience: configuration
content-type: reference
topic-tags: api
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1021'
ht-degree: 1%

---

# Adição de funções SQL extras{#adding-additional-sql-functions}

## Introdução {#introduction}

O Adobe Campaign permite que o usuário defina **suas próprias funções** que possam acessar funções SQL, tanto aquelas oferecidas pelo banco de dados quanto aquelas que ainda não estão disponíveis no console. Isso é útil para funções agregadas (média, máximo, soma), por exemplo, que só podem ser calculadas no servidor ou quando o banco de dados fornece uma maneira mais fácil de implementar determinadas funções, em vez de gravar a expressão &quot;manualmente&quot; no console (por exemplo, gerenciamento de datas).

Esse mecanismo também pode ser usado se você quiser usar uma função SQL do mecanismo de banco de dados recente ou incomum, que ainda não é oferecida pelo console do Adobe Campaign.

Depois que essas funções forem adicionadas, elas aparecerão no editor de expressão como outras funções predefinidas.

>[!IMPORTANT]
>
>As chamadas de função SQL no console não são mais enviadas naturalmente para o servidor. O mecanismo descrito aqui torna-se, portanto, **a única maneira de chamar** no servidor de função SQL não planejado.

## Instalação {#installation}

As funções a serem adicionadas estão em um arquivo **&quot;package&quot; no formato XML**, cuja estrutura é detalhada no parágrafo a seguir.

Para instalá-lo no console, selecione as opções **Tools/Advanced/Import package** no menu, em seguida, **[!UICONTROL Install from file]** e siga as instruções no assistente de importação.

>[!IMPORTANT]
>
>Aviso: mesmo que a lista de funções importadas seja exibida imediatamente no editor de funções, elas não poderão ser usadas até que o Adobe Campaign seja reiniciado.

## Estrutura geral do pacote a ser importado {#general-structure-of-package-to-import}

As funções a serem adicionadas podem ser encontradas no arquivo **&quot;package&quot;** no formato XML. Aqui está um exemplo:

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

* O **name**, **namespace** e **label** são somente para fins de informação. Eles permitem exibir um resumo do pacote na lista de pacotes instalados (Explorer/Administration/Package management/Installed packages).
* Os campos **buildVersion** e **buildNumber** são obrigatórios. Eles devem corresponder ao número do servidor ao qual o console está conectado. Essas informações podem ser encontradas na caixa &quot;Ajuda/Sobre&quot;.
* Os seguintes blocos, **entities** e **funclist** são obrigatórios. Em funcList, os campos &quot;name&quot; e &quot;namespace&quot; são obrigatórios, mas seu nome é deixado para o usuário decidir e eles designam exclusivamente a lista de funções.

   Isso significa que, se outra lista de funções com o mesmo par de namespace/nome (aqui &quot;cus::myList&quot;) for importada, as funções importadas anteriormente serão excluídas. Por outro lado, se você alterar esse par de namespace/nome, a nova série de funções importadas será adicionada à anterior.

* O elemento **group** permite especificar o grupo de funções no qual as funções importadas serão exibidas no editor de funções. O atributo @name pode ser um nome que já existe (nesse caso, as funções serão adicionadas ao grupo considerado) ou um novo nome (nesse caso, ele aparecerá em um novo grupo).
* Lembrete: os valores possíveis para o atributo @name no elemento `<group>` são:

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
>Certifique-se de concluir o atributo @label: esse é o nome que será exibido na lista de funções disponíveis. Se você não inserir nada, o grupo não terá um nome. No entanto, se você inserir um nome diferente do existente, o nome do grupo inteiro será alterado.

Se quiser adicionar funções a vários grupos diferentes, faça com que vários elementos `<group>` sejam rastreados na mesma lista.

Finalmente, um elemento `<group>` pode conter a definição de uma ou várias funções, que é a finalidade do arquivo de pacote. O `<function>`   é detalhado no parágrafo a seguir.

## Descritor de função &lt;function>&lt;/function> {#function-descriptor--function-}

O caso apresentado aqui é um caso geral em que queremos fornecer a **função implementation**.

Abaixo está um exemplo de uma função de &quot;maturidade relativa&quot; que, usando uma idade, indica por quantos anos a pessoa foi considerada madura.

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

O campo **@name** faz referência ao nome da função e &quot;args&quot; é a lista de parâmetros que serão exibidos na descrição. Nesse caso, a função aparecerá como &quot;relativeMaturity ( `<age>` )&quot; na janela de seleção de função.

* **** ajuda é o campo exibido na parte inferior da janela do editor de expressão.
* **@** displayis é uma mensagem informativa.

   >[!NOTE]
   >
   >Nos atributos @help e @display, a string &quot;$1&quot; representa o nome que foi dado no primeiro parâmetro de função (aqui, &quot;Age&quot;). $2, $3... representaria os seguintes parâmetros. No atributo @body detalhado abaixo, $1 designa o valor do argumento passado para a função durante a chamada.

   >[!NOTE]
   >
   >A descrição deve ser uma string de caracteres XML válidos: observe o uso de &#39;&lt;&#39; e &#39;>&#39; em vez de &lt; e >.

* **@** type é o tipo de retorno da função e é um valor padrão (long, string, byte, datetime...). Se for omitido, o servidor determinará o melhor tipo entre os tipos disponíveis na expressão que implementa a função.
* **@** minArgand  **** maxArgsdesigna o número de parâmetros (mínimo e máximo) para um parâmetro. Por exemplo, para uma função com 2 parâmetros, minArgs e maxArgs serão 2 e 2. Para 3 parâmetros, mais 1 opcional, serão 3 e 4, respectivamente.
* Finalmente, o elemento **providerPart** fornece a implementação da função.

   * O atributo **provider** é obrigatório, especifica os sistemas de banco de dados para os quais a implementação é fornecida. Como mostrado no exemplo, quando as sintaxes da expressão ou as funções subjacentes são diferentes, as implementações alternativas podem ser fornecidas de acordo com o banco de dados.
   * O atributo **@body** contém a implementação da função. Observe: essa implementação deve ser uma expressão, na linguagem do banco de dados (não um bloco de código). Dependendo dos bancos de dados, as expressões podem ser subconsultas (&quot;(selecione a coluna da tabela onde...)&quot;) que retornam somente um único valor. Por exemplo, esse é o caso no Oracle (o query deve ser escrito entre colchetes).

   >[!NOTE]
   >
   >Se apenas um ou dois bancos de dados puderem ser consultados pela função definida, sempre poderemos fornecer apenas as definições correspondentes a esses bancos de dados.

## Descritor de função &quot;Pass-through&quot; {#pass-through--function-descriptor}

Um descritor de função especial é o bloco **&quot;pass-through&quot;**, com um sistema de banco de dados &quot;provedor&quot; não especificado. Nesse caso, a implementação &quot;body&quot; só pode conter uma única chamada de função com uma sintaxe que não depende do banco de dados usado. Enquanto isso, o bloco &quot;ProviderPart&quot; é exclusivo.

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

Nesse caso, a adição de uma função só serve para tornar uma função de banco de dados que não estaria disponível por padrão, agora visível para o cliente.

## Exemplos {#examples}

Outros exemplos de função podem ser encontrados no pacote predefinido &quot;xtkdatakitfuncList.xml&quot;.
