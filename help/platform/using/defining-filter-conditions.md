---
title: Definição de condições de filtro
seo-title: Definição de condições de filtro
description: Definição de condições de filtro
seo-description: null
page-status-flag: never-activated
uuid: 2ed5d0bd-88fd-4eff-baf0-ed1b097269da
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: creating-queries
discoiquuid: 8e575da0-c51a-4106-a826-3e1771e63649
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# Definição de condições de filtro{#defining-filter-conditions}

## Escolha do operador {#choosing-the-operator}

Nas condições de filtragem, é necessário vincular dois valores usando um operador.

![](assets/query_editor_nveau_96.png)

Abaixo está uma lista dos operadores disponíveis:

<table> 
 <thead> 
  <tr> 
   <th> Operador<br /> </th> 
   <th> Finalidade<br /> </th> 
   <th> Exemplo<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Igual</span> a <br /> </td> 
   <td> Retorna um resultado idêntico aos dados inseridos na segunda coluna de valor.<br /> </td> 
   <td> <strong>Last name (@lastName) equal to 'Jones',</strong> retornará apenas destinatários cujo sobrenome seja Jones.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Maior que</span><br /> </td> 
   <td> Retorna um valor maior que o valor digitado.<br /> </td> 
   <td> <strong>Age (@age) greater than 50</strong>, retornará todos os valores maiores que '50', ou seja, '51', '52' etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Menor que</span><br /> </td> 
   <td> Retorna um valor menor que o valor digitado.<br /> </td> 
   <td> <strong>Creation date (@created) before 'DaysAgo(100)'</strong>, retornará todos os destinatários criados menos de 100 dias atrás.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Maior que ou igual a</span><br /> </td> 
   <td> Retorna todos os valores iguais ou maiores que o valor digitado.<br /> </td> 
   <td> <strong>Age (@age) greater than or equal to '30’</strong>, retornará todos os destinatários maiores de 30 anos ou mais.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Menor que ou igual</span> a <br /> </td> 
   <td> Retorna todos os valores iguais ou inferiores ao valor inserido.<br /> </td> 
   <td> <strong>Age (@age) less than or equal to '60'</strong>, retornará todos os destinatários com 60 anos ou menos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Diferente de</span><br /> </td> 
   <td> Retorna todos os valores não idênticos ao valor inserido.<br /> </td> 
   <td> <strong>Language (@language) to equal to 'English'</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Começa com</span><br /> </td> 
   <td> Retorna os resultados iniciando com o valor inserido.<br /> </td> 
   <td> <strong>Account # (@account) starts with '32010'.</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Não começa com</span><br /> </td> 
   <td> Retorna os resultados que não começam com o valor inserido<br /> </td> 
   <td> <strong>Account # (@account) does not start with '20'</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Contém</span><br /> </td> 
   <td> Retorna os resultados contendo pelo menos o valor inserido.<br /> </td> 
   <td> <strong>Email domain (@domain) contains 'mail'</strong> retornará todos os nomes de domínio que contêm 'mail’. Assim, o domínio "gmail.com" também será retornado.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Não contém</span><br /> </td> 
   <td> Retorna resultados não contendo o valor digitado.<br /> </td> 
   <td> <strong>Email domain (@domain) does not contain 'vo'</strong>. Nesse caso, nomes de domínio que contêm 'vo' não serão retornados. O nome de domínio 'voila.fr' não aparecerá nos resultados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Curtir</span><br /> </td> 
   <td> <span class="uicontrol">Like</span> é muito semelhante ao operador <span class="uicontrol">Contains</span> . It lets you insert a <span class="uicontrol">%</span> wild card character in the value.<br /> </td> 
   <td> <strong>Last name (@lastName) like 'Jon%s'</strong>. Aqui, o caractere curinga é usado como "joker" para localizar o nome "Jones", o operador esqueceu a letra ausente entre o 'n' e o 's'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Não é como</span><br /> </td> 
   <td> Is similar to <span class="uicontrol">Like</span> . Permite que você não recupere o valor inserido. Here too, the entered value must contain the <span class="uicontrol">%</span> wild card character.<br /> </td> 
   <td> <strong>Last name (@lastName) not like 'Smi%h'</strong>. Aqui, os destinatários que têm 'Smi%h' como sobrenome não serão retornados.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Está vazio</span><br /> </td> 
   <td> Nesse caso, o resultado que estamos procurando corresponde a um valor vazio na segunda coluna de valor.<br /> </td> 
   <td> <strong>Mobile (@mobilePhone) is empty</strong> retorna todos os destinatários que não têm número de celular.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Não está vazio</span><br /> </td> 
   <td> Works in reverse to the <span class="uicontrol">Is empty</span> operator. Não é necessário inserir dados na segunda coluna de valor.<br /> </td> 
   <td> <strong>Email (@email) is not empty</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Está incluído</span> em <br /> </td> 
   <td> Retorna resultados incluídos nos valores indicados. Esses valores devem ser separados por vírgula.<br /> </td> 
   <td> <strong>Birth date (@birthDate) is included in '12/10/1979,12/10/1984'</strong> retornará os destinatários nascidos entre essas datas. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Não está incluído</span> em <br /> </td> 
   <td> Works like the <span class="uicontrol">Is included in</span> operator. Aqui, queremos excluir destinatários com base nos valores inseridos.<br /> </td> 
   <td> <strong>Birth date (@birthDate) is not included in '12/10/1979,12/10/1984'</strong>. Ao contrário do exemplo anterior, os destinatários nascidos nessas datas não serão retornados.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Uso de AND, OR, EXCEPT {#using-and--or--except}

Para queries usando várias condições de filtragem, você precisa definir links entre as condições. Há três links possíveis:

* **[!UICONTROL And]** permite combinar duas condições de filtragem.
* **[!UICONTROL Or]** permite oferecer uma alternativa,
* **[!UICONTROL Except]** permite definir uma exceção.

Click **[!UICONTROL And]** (offered by default) and choose from the drop-down list.

![](assets/query_condition_modif_01.png)

* **[!UICONTROL And]**: adiciona uma condição e permite a filtragem excessiva.
* **[!UICONTROL Or]**: adiciona uma condição e permite a filtragem excessiva.

   O exemplo a seguir permite localizar destinatários cujo domínio de email contenha &quot;orange.co.uk&quot; ou cujo código postal começa com &quot;NW&quot;.

   ![](assets/query_condition_modif_02.png)

* **[!UICONTROL Except]**: se você tiver dois filtros e o primeiro não retornar um valor, esse tipo de link criará uma exceção.

   No exemplo a seguir, queremos retornar destinatários cujo domínio de email contenha &quot;orange.co.uk&quot;, exceto se o sobrenome do destinatário for &quot;Smith&quot;.

   ![](assets/query_condition_modif_03.png)

Este exemplo mostra um filtro que permite exibir: destinatários que falam espanhol, ou que são mulheres com números de celular, ou ainda destinatários sem um número de conta e cujo nome da empresa começa com a letra &quot;N&quot;.

![](assets/query_editor_nveau_31.png)

## Priorização das condições {#prioritizing-conditions}

Esta seção explica como priorizar condições com ajuda das setas azuis na barra de ferramentas.

* A seta apontando para a direita permite adicionar um nível de parênteses ao filtro.
* A seta apontando para a esquerda permite excluir um nível de parêntese selecionado do filtro.

   ![](assets/query_condition_modif_04.png)

* As setas verticais permitem mover uma condição, alterando assim sua sequência de execução.

Este exemplo mostra como usar a seta para excluir um nível de parênteses. Comece a partir da seguinte condição de filtragem: **[!UICONTROL City equal to London OR gender equal to male and mobile not indicated OR account # starts with "95" and company name starts with "A"]**.

Coloque o cursor na condição de **[!UICONTROL Gender (@gender) equal to Male]** filtragem e clique na **[!UICONTROL Remove a parenthesis level]** seta.

![](assets/query_editor_nveau_32.png)

A **[!UICONTROL Gender (@gender) equal to Male]** condição foi retirada de seus parênteses. Ela foi movida para o mesmo nível da condição &quot;Cidade igual a Londres&quot;. These conditions are linked together (**[!UICONTROL And]**).

## Selecionar dados para extrair {#selecting-data-to-extract}

Os campos disponíveis variam de uma tabela para outra. All fields are stored in a main node known as the **[!UICONTROL Main element]**. No exemplo a seguir, os campos disponíveis estão na tabela de destinatários. Os campos são sempre exibidos em ordem alfabética.

O detalhe do campo selecionado é visível na parte inferior da janela. Por exemplo, o **[!UICONTROL Email domain]** campo é um **[!UICONTROL Calculated SQL field]** e sua extensão é **[!UICONTROL (@domain)]**.

![](assets/query_editor_nveau_59.png)

>[!NOTE]
>
>Use the **[!UICONTROL Search]** tool to find an available field.

Clique duas vezes em um campo disponível para adicioná-lo às colunas de saída. At the end of the query, each selected field creates a column in the **[!UICONTROL Data preview]** window.

![](assets/query_editor_nveau_01.png)

Campos avançados não são exibidos por padrão. Click **[!UICONTROL Display advanced fields]** in the bottom right-hand corner of the available fields to display everything. Clique novamente para retornar ao modo de exibição anterior.

Por exemplo, na tabela do destinatário, os campos avançados são **Boolean 1**, **[!UICONTROL Boolean 2]**, **[!UICONTROL Boolean 3]**, **[!UICONTROL Foreign key of "Folder" link]** etc.

O exemplo a seguir mostra os campos avançados da tabela de destinatários.

![](assets/query_editor_nveau_53.png)

As várias categorias de campos:

<table> 
 <thead> 
  <tr> 
   <th> Ícone<br /> </th> 
   <th> Descrição<br /> </th> 
   <th> Exemplos<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_47.png" /> </td> 
   <td> Campo simples<br /> </td> 
   <td> Email, sexo, etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_48.png" /> </td> 
   <td> Chave primária. Este campo SQL é uma maneira de identificar um registro em uma tabela.<br /> </td> 
   <td> Os destinatários do identificador são chaves primárias e os identificadores são exclusivos por definição.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_02.png" /> </td> 
   <td> Chave externa. Usado como um link para outra tabela.<br /> </td> 
   <td> Chave externa do destinatário, chave externa de serviço etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_46.png" /> </td> 
   <td> Campo calculado. Esse tipo de campo é calculado mediante solicitação usando os valores no banco de dados.<br /> </td> 
   <td> Idade, domínio de email etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_49.png" /> </td> 
   <td> Campo contendo textos longos.<br /> </td> 
   <td> Comentário, endereço completo etc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_50.png" /> </td> 
   <td> Campo SQL indexado. <br /> </td> 
   <td> Nome completo, código ISO etc. <br /> </td> 
  </tr> 
 </tbody> 
</table>

Vincular a uma tabela e elemento de coleção:

<table> 
 <thead> 
  <tr> 
   <th> Ícone<br /> </th> 
   <th> Descrição<br /> </th> 
   <th> Exemplo<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_51.png" /> </td> 
   <td> Vincular a uma tabela em particular. Eles coincidem com as associações de tipo 1-1. Uma ocorrência da tabela de origem pode coincidir com apenas uma ocorrência da tabela de target. Por exemplo, somente um destinatário pode ser vinculado a um país.<br /> </td> 
   <td> Pasta, Estado, País etc. <br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_52.png" /> </td> 
   <td> Elemento de coleção em uma tabela específica. Eles correspondem com associações de tipo 1-N. Uma ocorrência da tabela de origem pode coincidir com várias ocorrências da tabela de destino, mas uma ocorrência da tabela de destino pode coincidir com apenas uma ocorrência da tabela de origem. Por exemplo, um destinatário pode assinar cartas de assinatura 'n'.<br /> </td> 
   <td> Assinaturas, listas, logs de exclusão etc.<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* Use the **[!UICONTROL Add]** button (above the side icon bar) to add an output column in which we wish to edit the expression. For more on editing an expression, refer to [Building expressions](#building-expressions).
>* Exclua uma coluna de saída clicando no &#39;x&#39; vermelho (**Excluir**).
>* Altere a ordem das colunas de saída usando as setas.
>* The **[!UICONTROL Distribution of values]** serves as a way to view the distributon of the values of the field selected (for example, the distributions linked to recipient towns, recipient languages, etc.).


## Criação de campos calculados {#creating-calculated-fields}

Se necessário, adicione uma coluna durante a formatação de dados. Um campo calculado adiciona uma coluna à seção de visualização de dados. Clique em **[!UICONTROL Add a calculated field]**.

![](assets/query_editor_nveau_43.png)

Existem quatro tipos de campos calculados:

* **[!UICONTROL Fixed string]**: permite adicionar uma string de caracteres.

   ![](assets/query_editor_nveau_60.png)

* **[!UICONTROL String with JavaScript tags]**: o valor do campo calculado combina uma sequência de caracteres e diretivas JavaScript.

   ![](assets/query_editor_nveau_61.png)

* **[!UICONTROL JavaScript expression]**: o valor do campo calculado é o resultado de uma avaliação da função do JavaScript. O valor retornado pode ser digitado (número, data etc.).

   ![](assets/query_editor_nveau_62.png)

* **[!UICONTROL Enumerations]**: Esse tipo de campo permite usar/modificar o conteúdo de uma das colunas de saída em uma nova coluna.

   É possível usar o valor de origem de uma coluna e fornecer um valor de destino. Esse valor de destino será exibido na nova coluna de saída.

   An example of adding calculated field type **[!UICONTROL Enumerations]** is available, refer to [this section](../../workflow/using/adding-enumeration-type-calculated-field.md).

   ![](assets/query_editor_nveau_63.png)

   The **[!UICONTROL Enumerations]** type calculated field can include 4 conditions:

   * **[!UICONTROL Keep the source value]** restaura o valor de origem para o destino sem alterá-lo.
   * **[!UICONTROL Use the following value]** permite inserir um valor de destino padrão para valores de origem não definidos.
   * **[!UICONTROL Generate a warning and continue]** avisa ao usuário que o valor de origem não pode ser alterado.
   * **[!UICONTROL Generate an error and reject the line]** impede que a linha seja calculada e importada.

Click the **[!UICONTROL Detail of calculated field]** to view the detail of the inserted field.

Para remover esse campo calculado, clique na **[!UICONTROL Remove the calculated field]** cruz.

![](assets/query_editor_nveau_58.png)

## Criação de expressões {#building-expressions}

A ferramenta de edição de expressão permite calcular agregações, gerar funções ou editar uma fórmula usando uma expressão.

O exemplo a seguir mostra como executar uma contagem em uma chave primária.

Siga as etapas abaixo:

1. Clique **[!UICONTROL Add]** na **[!UICONTROL Data to extract]** janela. In the **[!UICONTROL Formula type]** window, select a type of formula to enter the expression.

   Há vários tipos de fórmulas disponíveis: **[!UICONTROL Field only]**, **[!UICONTROL Aggregate]**, **[!UICONTROL Expression]**.

   Select **[!UICONTROL Process on an aggregate function]**, and **[!UICONTROL Count]**. Click **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_54.png)

1. A chave primária é calculada.

   ![](assets/query_editor_nveau_88.png)

Here is a detailed view of the choices available in the **[!UICONTROL Formula types]** window:

![](assets/query_editor_nveau_05.png)

1. **[!UICONTROL Field only]** permite que você volte à **[!UICONTROL Field to select]** janela.
1. **[!UICONTROL Aggregate (Process on an aggregate function)]**. Veja alguns exemplos de uso agregado:

   * **[!UICONTROL Count]** permite que você execute uma contagem de chave primária.
   * **[!UICONTROL Sum]** permite que você adicione todas as compras feitas por um cliente por mais de um ano.
   * **[!UICONTROL Maximum value]** permite que você encontre os clientes que compraram a maioria dos produtos &quot;n&quot;.
   * **[!UICONTROL Minimum value]** permite que você classifique os clientes e localize os que assinaram uma oferta mais recentemente.
   * **[!UICONTROL Average]**. Essa função permite calcular a idade média dos destinatários.

      The **[!UICONTROL Distinct]** box lets you recover unique and non-zero values of a column. Por exemplo, é possível recuperar todos os logs de rastreamento de um destinatário; eles são alterados para o valor 1, desde que sejam todos referentes ao mesmo destinatário.

1. **[!UICONTROL Expression]** abre a **[!UICONTROL Edit the expression]** janela. Isso permite detectar números de telefone com muitos numerais, provavelmente devido a erros de entrada.

   ![](assets/query_editor_nveau_71.png)

   For a list of all available functions, refer to [List of functions](#list-of-functions).

## Lista de funções {#list-of-functions}

If an **[!UICONTROL Expression]** type formula is chosen, you will be taken to the &quot;edit the expression&quot; window. Various categories of functions can be associated to the available fields: **[!UICONTROL Aggregates]**, **[!UICONTROL String]**, **[!UICONTROL Date]**, **[!UICONTROL Numerical]**, **[!UICONTROL Currency]**, **[!UICONTROL Geomarketing]**, **[!UICONTROL Windowing function]** and **[!UICONTROL Others]**.

O editor de expressão tem esta aparência:

![](assets/s_ncs_user_filter_define_expression.png)

Ele permite selecionar campos nas tabelas do banco de dados e adicionar funções avançadas a eles. Os recursos abaixo estão disponíveis.

**Agregados**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nome</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
   <td> <strong>Sintaxe</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Avg</strong><br /> </td> 
   <td> Retorna a média de uma coluna do tipo número<br /> </td> 
   <td> Avg(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Contagem</strong><br /> </td> 
   <td> Conta os valores não nulos de uma coluna<br /> </td> 
   <td> Count(&lt;value&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>CountAll</strong><br /> </td> 
   <td> Conta os valores retornados (todos os campos)<br /> </td> 
   <td> CountAll()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Countdistinct</strong><br /> </td> 
   <td> Conta os valores não nulos distintos de uma coluna<br /> </td> 
   <td> Countdistinct(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Max</strong><br /> </td> 
   <td> Retorna o valor máximo de uma coluna, cadeira de caracteres ou coluna de tipo de data<br /> </td> 
   <td> Max(&lt;value&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Min</strong><br /> </td> 
   <td> Retorna o valor mínimo de uma coluna do tipo número, cadeira de caracteres ou dados<br /> </td> 
   <td> Min(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>StdDev</strong><br /> </td> 
   <td> Retorna o desvio padrão de uma coluna do tipo número, cadeira de caracteres ou dados<br /> </td> 
   <td> StdDev(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Sum</strong><br /> </td> 
   <td> Retorna a soma dos valores de uma coluna do tipo número, cadeira de caracteres ou dados<br /> </td> 
   <td> Sum(&lt;value&gt;)<br /></td> 
  </tr> 
 </tbody> 
</table>

**Cadeia de caracteres**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nome</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
   <td> <strong>Sintaxe</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull2</strong><br /> </td> 
   <td> Indica se todos os parâmetros são não nulos e não estão vazios<br /> </td> 
   <td> AllNonNull2(&lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull3</strong><br /> </td> 
   <td> Indica se todos os parâmetros são não nulos e não estão vazios<br /> </td> 
   <td> AllNonNull3(&lt;string&gt;, &lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ascii</strong><br /> </td> 
   <td> Retorna o valor ASCII do primeiro caractere na cadeia de caracteres.<br /> </td> 
   <td> Ascii(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Char</strong><br /> </td> 
   <td> Retorna o caractere correspondente ao código ASCII 'n'<br /> </td> 
   <td> Char(&lt;number&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Charindex</strong><br /> </td> 
   <td> Retorna a posição da cadeia de caracteres 2 na cadeia de caracteres 1.<br /> </td> 
   <td> Charindex(&lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>GetLine</strong><br /> </td> 
   <td> Retorna a linha enésima (de 1 a n) da cadeia de caracteres<br /> </td> 
   <td> GetLine(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IfEquals</strong><br /> </td> 
   <td> Retorna o terceiro parâmetro se os dois primeiros parâmetros forem iguais. Caso contrário, retorna o último parâmetro<br /> </td> 
   <td> IfEquals(&lt;string&gt;, &lt;string&gt;, &lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IsMemoNull</strong><br /> </td> 
   <td> Indica se o memorando passado como parâmetro é nulo<br /> </td> 
   <td> IsMemoNull(&lt;memo&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords</strong><br /> </td> 
   <td> Concatena as cadeira de caracteres transmitidas como parâmetros. Adiciona espaços entre as cadeiras de caracteres, se necessário.<br /> </td> 
   <td> JuxtWords(&lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords3</strong><br /> </td> 
   <td> Concatena as cadeira de caracteres transmitidas como parâmetros. Adiciona espaços entre as cadeiras de caracteres, se necessário<br /> </td> 
   <td> JuxtWords3(&lt;string&gt;, &lt;string&gt;, &lt;string&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>LPad</strong><br /> </td> 
   <td> Retorna a cadeira de caracteres concluída à esquerda<br /> </td> 
   <td> LPad(&lt;string&gt;, &lt;número&gt;, &lt;caractere&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Left</strong><br /> </td> 
   <td> Retorna os primeiros n caracteres da cadeira de caracteres<br /> </td> 
   <td> Left(&lt;string&gt;, &lt;number&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Length</strong><br /> </td> 
   <td> Retorna o comprimento da cadeira de caracteres<br /> </td> 
   <td> Length(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Lower</strong><br /> </td> 
   <td> Retorna a cadeira de caracteres em minúsculas<br /> </td> 
   <td> Lower(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ltrim</strong><br /> </td> 
   <td> Remove espaços à esquerda da cadeira de caracteres<br /> </td> 
   <td> Ltrim(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Md5Digest</strong><br /> </td> 
   <td> Retorna uma representação hexadecimal da chave MD5 de uma cadeira de caracteres<br /> </td> 
   <td> Md5Digest(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>MemoContains</strong><br /> </td> 
   <td> Especifica se o memorando contém a cadeira de caracteres aprovada como um parâmetro<br /> </td> 
   <td> MemoContains(&lt;memo&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>RPad</strong><br /> </td> 
   <td> Retorna a cadeira de caracteres concluída à direita<br /> </td> 
   <td> RPad(&lt;string&gt;, &lt;number&gt;, &lt;character&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Right</strong><br /> </td> 
   <td> Retorna os últimos n caracteres da cadeira de caracteres<br /> </td> 
   <td> Right(&lt;string&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Rtrim</strong><br /> </td> 
   <td> Remove espaços à direita da cadeira de caracteres<br /> </td> 
   <td> Rtrim(&lt;string&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Smart</strong><br /> </td> 
   <td> Retorna a cadeira de caracteres com a primeira letra de cada palavra em maiúsculas<br /> </td> 
   <td> Smart(&lt;string&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Substring</strong><br /> </td> 
   <td> Extrai a subcadeia de caracteres iniciando no caractere n1 da cadeira de caracteres e de comprimento n2<br /> </td> 
   <td> Substring(&lt;string&gt;, &lt;offset&gt;, &lt;length&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToString</strong><br /> </td> 
   <td> Converte o número em uma cadeira de caracteres<br /> </td> 
   <td> ToString(&lt;número&gt;, &lt;número&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Upper</strong><br /> </td> 
   <td> Retorna a cadeira de caracteres em maiúsculas<br /> </td> 
   <td> Upper(&lt;string&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLink</strong><br /> </td> 
   <td> Retorna a chave externa de um link passado como um parâmetro se os outros dois parâmetros forem iguais<br /> </td> 
   <td> VirtualLink(&lt;number&gt;, &lt;number&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLinkStr</strong><br /> </td> 
   <td> Retorna a chave externa (texto) de um link passado como um parâmetro se os outros dois parâmetros forem iguais<br /> </td> 
   <td> VirtualLinkStr(&lt;string&gt;, &lt;number&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>dataLength</strong><br /> </td> 
   <td> Retorna o tamanho da cadeia de caracteres<br /> </td> 
   <td> dataLength(&lt;string&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Data**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nome</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
   <td> <strong>Sintaxe</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AddDays</strong><br /> </td> 
   <td> Adiciona um número de dias a uma data<br /> </td> 
   <td> AddDays(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddHours</strong><br /> </td> 
   <td> Adiciona um número de horas a uma data<br /> </td> 
   <td> AddHours(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMinutes</strong><br /> </td> 
   <td> Adiciona um número de minutos a uma data<br /> </td> 
   <td> AddMinutes(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMonths</strong><br /> </td> 
   <td> Adiciona um número de meses a uma data<br /> </td> 
   <td> AddMonths(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddSeconds</strong><br /> </td> 
   <td> Adiciona um número de segundos a uma data<br /> </td> 
   <td> AddSeconds(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddYears</strong><br /> </td> 
   <td> Adiciona um número de anos a uma data<br /> </td> 
   <td> AddYears(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DateOnly</strong><br /> </td> 
   <td> Retorna somente a data (com a hora 00:00)*<br /> </td> 
   <td> DateOnly(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Day</strong><br /> </td> 
   <td> Retorna o número que representa o dia da data<br /> </td> 
   <td> Day(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DayOfYear</strong><br /> </td> 
   <td> Retorna o número do dia no ano da data<br /> </td> 
   <td> DayOfYear(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgo</strong><br /> </td> 
   <td> Retorna a data correspondente à data atual menos n dias<br /> </td> 
   <td> DaysAgo(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgoInt</strong><br /> </td> 
   <td> Retorna a data (inteiro aaaammdd) correspondente à data atual menos n dias<br /> </td> 
   <td> DaysAgoInt(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysDiff</strong><br /> </td> 
   <td> Número de dias entre duas datas<br /> </td> 
   <td> DaysDiff(&lt;end date&gt;, &lt;start date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysOld</strong><br /> </td> 
   <td> Retorna a idade em dias de uma data.<br /> </td> 
   <td> DaysOld(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetDate</strong><br /> </td> 
   <td> Retorna a data atual do sistema do servidor.<br /> </td> 
   <td> GetDate()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Hour</strong><br /> </td> 
   <td> Retorna a hora da data.<br /> </td> 
   <td> Hour(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>HoursDiff</strong><br /> </td> 
   <td> Retorna o número de horas entre duas datas<br /> </td> 
   <td> HoursDiff(&lt;end date&gt;, &lt;start date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Minute</strong><br /> </td> 
   <td> Retorna os minutos da data<br /> </td> 
   <td> Minute(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MinutesDiff</strong><br /> </td> 
   <td> Retorna o número de minutos entre duas datas<br /> </td> 
   <td> MinutesDiff(&lt;end date&gt;, &lt;start date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Month</strong><br /> </td> 
   <td> Retorna o número que representa o mês da data<br /> </td> 
   <td> Month(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsAgo</strong><br /> </td> 
   <td> Retorna a data correspondente à data atual menos n meses<br /> </td> 
   <td> MonthsAgo(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsDiff</strong><br /> </td> 
   <td> Retorna o número de meses entre duas datas<br /> </td> 
   <td> MonthsDiff(&lt;end date&gt;, &lt;start date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsOld</strong><br /> </td> 
   <td> Retorna a idade em meses de uma data<br /> </td> 
   <td> MonthsOld(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Second</strong><br /> </td> 
   <td> Retorna os segundos da data<br /> </td> 
   <td> Second(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SecondsDiff</strong><br /> </td> 
   <td> Retorna o número de segundos entre duas datas<br /> </td> 
   <td> SecondsDiff(&lt;end date&gt;, &lt;start date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubDays</strong><br /> </td> 
   <td> Subtrai um número de dias a partir de uma data<br /> </td> 
   <td> SubDays(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubHours</strong><br /> </td> 
   <td> Subtrai um número de horas a partir de uma data<br /> </td> 
   <td> SubHours(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMinutes</strong><br /> </td> 
   <td> Subtrai um número de minutos de uma data<br /> </td> 
   <td> SubMinutes(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMonths</strong><br /> </td> 
   <td> Subtrai um número de meses a partir de uma data<br /> </td> 
   <td> SubMonths(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubSeconds</strong><br /> </td> 
   <td> Subtrai um número de segundos a partir de uma data<br /> </td> 
   <td> SubSeconds(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubYears</strong><br /> </td> 
   <td> Subtrai um número de anos a partir de uma data<br /> </td> 
   <td> SubYears(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDate</strong><br /> </td> 
   <td> Converte uma data + hora em uma data<br /> </td> 
   <td> ToDate(&lt;date + time&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDateTime</strong><br /> </td> 
   <td> Converte uma cadeia de caracteres em uma data + hora<br /> </td> 
   <td> ToDateTime(&lt;string&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncDate</strong><br /> </td> 
   <td> Arredonda uma data e hora para o segundo mais próximo<br /> </td> 
   <td> TruncDate(@lastModified, &lt;number of seconds&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncDateTZ</strong><br /> </td> 
   <td> Arredonda uma data e hora para uma determinada precisão expressa em segundos<br /> </td> 
   <td> TruncDateTZ(&lt;date&gt;, &lt;number of seconds&gt;, &lt;time zone&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncQuarter</strong><br /> </td> 
   <td> Arredonda uma data para o trimestre<br /> </td> 
   <td> TruncQuarter(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncTime</strong><br /> </td> 
   <td> Arredonda a parte de horário para cima até o próximo segundo<br /> </td> 
   <td> TruncTime(e&lt;data&gt;, &lt;número de segundos&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> Arredonda uma data para a semana<br /> </td> 
   <td> TruncWeek(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncYear</strong><br /> </td> 
   <td> Arredonda uma data + hora para 1º de janeiro do ano<br /> </td> 
   <td> TruncYear(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> Retorna o número que representa o dia na semana da data<br /> </td> 
   <td> WeekDay(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Year</strong><br /> </td> 
   <td> Retorna o número que representa o ano da data<br /> </td> 
   <td> Year(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearAnd Month</strong><br /> </td> 
   <td> Retorna o número que representa o ano e o mês da data.<br /> </td> 
   <td> YearAndMonth(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsDiff</strong><br /> </td> 
   <td> Retorna o número de anos entre as duas datas<br /> </td> 
   <td> YearsDiff(&lt;end date&gt;, &lt;start date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsOld</strong><br /> </td> 
   <td> Retorna a idade em anos de uma data<br /> </td> 
   <td> YearsOld(&lt;date&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Observe que a função **Dateonly** considera o fuso horário do servidor e não do operador.

**Numerical**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nome</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
   <td> <strong>Sintaxe</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Abs</strong><br /> </td> 
   <td> Retorna o valor absoluto de um número<br /> </td> 
   <td> Abs(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Ceil</strong><br /> </td> 
   <td> Retorna o número inteiro mais baixo maior ou igual a um número<br /> </td> 
   <td> Ceil(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Floor</strong><br /> </td> 
   <td> Retorna o maior inteiro maior ou igual a um número<br /> </td> 
   <td> Floor(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Greatest</strong><br /> </td> 
   <td> Retorna o maior número de dois números<br /> </td> 
   <td> Greatest(&lt;number 1&gt;, &lt;number 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Least</strong><br /> </td> 
   <td> Retorna o menor de dois números<br /> </td> 
   <td> Least(&lt;number 1&gt;, &lt;number 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Mod</strong><br /> </td> 
   <td> Retorna o restante da divisão inteira de n1 por n2<br /> </td> 
   <td> Mod(&lt;número 1&gt;, &lt;número 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Percent</strong><br /> </td> 
   <td> Retorna a proporção de dois números expressos como uma porcentagem<br /> </td> 
   <td> Percent(&lt;number 1&gt;, &lt;number 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Random</strong><br /> </td> 
   <td> Retorna o valor aleatório<br /> </td> 
   <td> Random()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Round</strong><br /> </td> 
   <td> Arredonda um número para decimais n<br /> </td> 
   <td> Round(&lt;number&gt;, &lt;number of decimals&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Sign</strong><br /> </td> 
   <td> Retorna o sinal do número<br /> </td> 
   <td> Sign(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDouble</strong><br /> </td> 
   <td> Converte um inteiro em um flutuante<br /> </td> 
   <td> ToDouble(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInt64</strong><br /> </td> 
   <td> Converte um flutuante em um inteiro de 64 bits<br /> </td> 
   <td> ToInt64(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInteger</strong><br /> </td> 
   <td> Converte um flutuante em um inteiro<br /> </td> 
   <td> ToInteger(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Trunc</strong><br /> </td> 
   <td> Corta o n1 para o decimal n2<br /> </td> 
   <td> Trunc(&lt;n1&gt;, &lt;n2&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

1. Currency

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nome</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
   <td> <strong>Sintaxe</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ConvertCurrency</strong><br /> </td> 
   <td> Converte uma quantia na moeda de origem em uma quantia na moeda de destino<br /> </td> 
   <td> ConvertCurrency(&lt;amount&gt;, &lt;source currency&gt;, &lt;target currency&gt;, &lt;conversion date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>FormatCurrency</strong><br /> </td> 
   <td> Formata a quantidade exibida com base nas configurações de moeda<br /> </td> 
   <td> FormatCurrency(&lt;amount&gt;, &lt;currency&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Geomarketing**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nome</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
   <td> <strong>Sintaxe</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Distance</strong><br /> </td> 
   <td> Retorna a distância entre dois pontos definidos por sua longitude e latitude, expresso em graus.<br /> </td> 
   <td> Distance(&lt;Longitude A&gt;, &lt;Latitude A&gt;, &lt;Longitude B&gt;, &lt;Latitude B&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Outros**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nome</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
   <td> <strong>Sintaxe</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Case</strong><br /> </td> 
   <td> Retorna o valor 1 se a condição for verdadeira. Caso contrário, retornará o valor 2.<br /> </td> 
   <td> Case(When(&lt;condition&gt;, &lt;value 1&gt;), Else(&lt;value 2&gt;))<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ClearBit</strong><br /> </td> 
   <td> Exclui o Sinalizador no valor<br /> </td> 
   <td> ClearBit(&lt;identifier&gt;, &lt;flag&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Coalesce</strong><br /> </td> 
   <td> Retorna o valor 2 se o valor 1 for zero ou nulo, caso contrário retorna o valor 1<br /> </td> 
   <td> Coalesce(&lt;value 1&gt;, &lt;value 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Decode</strong><br /> </td> 
   <td> Retorna o valor 3 se o valor 1 for igual ao valor 2. Caso contrário, retorna o valor 4.<br /> </td> 
   <td> Decode(&lt;value 1&gt;, &lt;value 2&gt;, &lt;value 3&gt;, &lt;value 4&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Else</strong><br /> </td> 
   <td> Retorna o valor 1 (só pode ser usado como parâmetro da função case)<br /> </td> 
   <td> Else(&lt;valor 1&gt;, &lt;valor 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetEmailDomain</strong><br /> </td> 
   <td> Extrai o domínio de um endereço de email<br /> </td> 
   <td> GetEmailDomain(&lt;value&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetMirrorURL</strong><br /> </td> 
   <td> Recupera o URL do servidor da mirror page<br /> </td> 
   <td> GetMirrorURL(&lt;value&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Iif</strong><br /> </td> 
   <td> Retorna o valor 1 se a expressão for verdadeira. Caso contrário, retorna o valor 2<br /> </td> 
   <td> Iif(&lt;condition&gt;, &lt;value 1&gt;, &lt;value 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsBitSet</strong><br /> </td> 
   <td> Indica se o Sinalizador está no valor<br /> </td> 
   <td> IsBitSet(&lt;identifier&gt;, &lt;flag&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsEmptyString</strong><br /> </td> 
   <td> Retorna o valor 2 se a cadeira de caracteres 1 estiver vazia, caso contrário, retorna o valor 3.<br /> </td> 
   <td> IsEmptyString(&lt;value 1&gt;, &lt;value 2&gt;, &lt;value 3&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>NoNull</strong><br /> </td> 
   <td> Retorna a cadeira de caracteres vazia se o argumento for NULL.<br /> </td> 
   <td> NoNull(&lt;value&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>RowId</strong><br /> </td> 
   <td> Retorna o número da linha.<br /> </td> 
   <td> RowId<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>SetBit</strong><br /> </td> 
   <td> Força o Sinalizador no valor.<br /> </td> 
   <td> SetBit(&lt;identifier&gt;, &lt;flag&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToBoolean</strong><br /> </td> 
   <td> Converte um número em um booleano<br /> </td> 
   <td> ToBoolean(&lt;number&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>When</strong><br /> </td> 
   <td> Retorna o valor 1 se a expressão for verdadeira. Se não, ele retorna o valor 2 (só pode ser usado como parâmetro da função case)<br /> </td> 
   <td> When(&lt;condition&gt;, &lt;value 1&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Funções janela**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nome</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
   <td> <strong>Sintaxe</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Desc</strong><br /> </td> 
   <td> Aplica uma classificação decrescente<br /> </td> 
   <td> Desc(&lt;value 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>OrderBy</strong><br /> </td> 
   <td> Classifica o resultado dentro da partição<br /> </td> 
   <td> OrderBy(&lt;value 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>PartitionBy</strong><br /> </td> 
   <td> Partições do resultado de um query em uma tabela<br /> </td> 
   <td> PartitionBy(&lt;value 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>RowNum</strong><br /> </td> 
   <td> Gera um número de linha com base na partição da tabela e em uma sequência de classificação.<br /> </td> 
   <td> RowNum(PartitionBy(&lt;value 1&gt;), OrderBy(&lt;value 1&gt;))<br /> </td> 
  </tr> 
 </tbody> 
</table>