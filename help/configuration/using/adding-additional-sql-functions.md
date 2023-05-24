---
product: campaign
title: Adição de funções SQL extras
description: Saiba como definir funções SQL adicionais
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---

# Definir funções SQL adicionais{#adding-additional-sql-functions}

O Adobe Campaign permite que o usuário defina **suas próprias funções** que podem acessar funções SQL, aquelas oferecidas pelo banco de dados e aquelas que ainda não estão disponíveis no console. Isso é útil para funções agregadas (média, máximo, soma), por exemplo, que só podem ser calculadas no servidor ou quando o banco de dados fornece uma maneira mais fácil de implementar determinadas funções, em vez de gravar &quot;manualmente&quot; a expressão no console (por exemplo, gerenciamento de datas).

Esse mecanismo também pode ser usado se você quiser usar uma função SQL recente ou incomum do mecanismo de banco de dados, que ainda não é oferecida pelo console do Adobe Campaign.

Depois que essas funções forem adicionadas, elas aparecerão no editor de expressão da mesma forma que outras funções predefinidas.

>[!IMPORTANT]
>
>As chamadas de função SQL no console não são mais enviadas naturalmente ao servidor. O mecanismo aqui descrito torna-se, por conseguinte, **a única maneira de chamar** no servidor de função SQL não planejado.

## Instalação {#installation}

As funções a serem adicionadas estão em um **arquivo &quot;package&quot; no formato XML**, cuja estrutura é apresentada em pormenor no parágrafo seguinte.

Para instalá-lo a partir do console, selecione a opção **Ferramentas/Avançado/Importar pacote** opções no menu e, em seguida, na guia **[!UICONTROL Install from file]** e siga as instruções do assistente de importação.

>[!IMPORTANT]
>
>Aviso: mesmo que a lista de funções importadas apareça imediatamente no editor de funções, elas não poderão ser usadas até que o Adobe Campaign seja reiniciado.

## Estrutura geral do pacote a importar {#general-structure-of-package-to-import}

As funções a serem adicionadas podem ser encontradas no **arquivo &quot;package&quot;** no formato XML. Aqui está um exemplo:

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

* A variável **name**, **namespace** e **rótulo** são apenas para fins informativos. Eles permitem exibir um resumo do pacote na lista de pacotes instalados (Explorer/Administration/Package management/Installed packages).
* A variável **buildVersion** e **buildNumber** Os campos são obrigatórios. Eles devem corresponder ao número do servidor ao qual o console está conectado. Essas informações podem ser encontradas na caixa &quot;Ajuda/Sobre&quot;.
* Os seguintes blocos, **entidades** e **funclist** são obrigatórios. Em funcList, os campos &quot;name&quot; e &quot;namespace&quot; são obrigatórios, mas seu nome é deixado para o usuário decidir e ele designa exclusivamente a lista de funções.

   Isso significa que se outra lista de funções com o mesmo par de namespace/nome (aqui &quot;cus::myList&quot;) for importada, as funções importadas anteriormente serão excluídas. Por outro lado, se você alterar esse par de namespace/nome, a nova série de funções importadas será adicionada à série anterior.

* A variável **grupo** element permite especificar o grupo de funções no qual as funções importadas aparecerão no editor de funções. O atributo @name pode ser um nome que já existe (nesse caso, as funções serão adicionadas ao grupo considerado) ou um novo nome (nesse caso, ele aparecerá em um novo grupo).
* Lembrete: valores possíveis para o atributo @name no `<group>` elementos são:

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
>Certifique-se de completar o atributo @label: este é o nome que será exibido na lista de funções disponíveis. Se você não inserir nada, o grupo não terá um nome. No entanto, se você inserir um nome diferente do nome existente, o nome do grupo inteiro será alterado.

Se quiser adicionar funções a vários grupos diferentes, você pode fazer vários `<group>`  Os elementos do são rastreados na mesma lista.

Por último, uma `<group>` O elemento pode conter a definição de uma ou várias funções, que é a finalidade do arquivo de pacote. A variável  `<function>`   O elemento é detalhado no parágrafo a seguir.

## Descritor de função &lt;function>&lt;/function> {#function-descriptor--function-}

O caso aqui apresentado é um caso geral em que pretendemos apresentar **implementação de função**.

Abaixo está um exemplo de uma função de &quot;maturidade relativa&quot; que, usando uma idade, indica por quantos anos a pessoa foi considerada madura.

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

A variável **@name** o campo refere-se ao nome da função, e &quot;args&quot; é a lista de parâmetros que será exibida na descrição. Nesse caso, a função aparecerá como &quot;relativeMaturity ( `<age>` )&quot; na janela de seleção de função.

* **ajuda** é o campo exibido na parte inferior da janela do editor de expressões.
* **@display** é uma mensagem informativa.

   >[!NOTE]
   >
   >Nos atributos @help e @display, a string &quot;$1&quot; representa o nome fornecido no primeiro parâmetro de função (aqui, &quot;Age&quot;). $2, $3... representariam os seguintes parâmetros. No atributo @body detalhado abaixo, $1 designa o valor do argumento passado para a função durante a chamada.

   >[!NOTE]
   >
   >A descrição deve ser uma cadeia de caracteres XML válidos: observe o uso de &#39;&lt;&#39; e &#39;>&#39; em vez de &lt; e >.

* **@type** é o tipo de retorno da função e é um valor padrão (long, string, byte, datetime...). Se for omitido, o servidor determinará o melhor tipo entre os tipos disponíveis na expressão que implementa a função.
* **@minArgs** e **maxArgs** designa o número de parâmetros (mínimo e máximo) para um parâmetro. Por exemplo, para uma função com 2 parâmetros, minArgs e maxArgs serão 2 e 2. Para 3 parâmetros, mais 1 opcional, eles serão 3 e 4, respectivamente.
* Por último, a **providerPart** elemento fornece a implementação da função.

   * A variável **provider** atributo é obrigatório, ele especifica os sistemas de banco de dados para os quais a implementação é fornecida. Como mostrado no exemplo, quando as sintaxes de expressão ou as funções subjacentes diferem, implementações alternativas podem ser fornecidas de acordo com o banco de dados.
   * A variável **@body** O atributo contém a implementação da função. Observação: esta implementação deve ser uma expressão em linguagem de banco de dados (não um bloco de código). Dependendo dos bancos de dados, as expressões podem ser subconsultas (&quot;(selecione a coluna da tabela onde...)&quot;) que retornam apenas um valor único. Por exemplo, esse é o caso no Oracle (a consulta deve ser gravada entre parênteses).

   >[!NOTE]
   >
   >Se apenas um ou dois bancos de dados forem consultados pela função definida, sempre poderemos fornecer apenas as definições correspondentes a esses bancos de dados.

## Descritor de função &#39;Pass-through&#39; {#pass-through--function-descriptor}

Um descritor de função especial é o **&quot;passagem&quot;** bloco, com um sistema de banco de dados &quot;provedor&quot; não especificado. Nesse caso, a implementação &quot;body&quot; só pode conter uma única chamada de função com uma sintaxe que não depende do banco de dados usado. Enquanto isso, o bloco &quot;ProviderPart&quot; é exclusivo.

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

Nesse caso, adicionar uma função serve apenas para tornar uma função de banco de dados que não estaria disponível por padrão, agora visível para o cliente.

## Exemplos {#examples}

Mais exemplos de função podem ser encontrados no pacote predefinido &quot;xtkdatakitfuncList.xml&quot;.
