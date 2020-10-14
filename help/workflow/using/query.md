---
title: Consulta
seo-title: Consulta
description: Consulta
seo-description: null
page-status-flag: never-activated
uuid: 32f4f467-5083-414f-8616-1aa4bf2b5867
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: b53d9810-f61f-4257-b410-e4d30f78429d
translation-type: tm+mt
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: tm+mt
source-wordcount: '1617'
ht-degree: 100%

---


# Consulta{#query}

## Criação de query {#creating-a-query}

Um query permite selecionar um target de acordo com critérios. Você pode associar um código de segmento ao resultado do query e inserir dados adicionais nele.
Para obter mais informações sobre amostras de query, consulte [esta seção](../../workflow/using/querying-recipient-table.md).

>[!NOTE]
>
>As atividades de query não são compatíveis com campos CLOB ao usar o Oracle.

![](assets/s_user_segmentation_wizard_9.png)

Para mais informações sobre como usar e gerenciar dados adicionais, consulte [Adição de dados](#adding-data).

O link **[!UICONTROL Edit query...]** permite definir o tipo de direcionamento, as restrições e os critérios de seleção do público da seguinte maneira:

1. Selecione a targeting dimension e a dimensão de filtro. Por padrão, o target é selecionado dos recipients. A lista de filtros de restrição é igual àquelas usadas para o target de delivery.

   O targeting dimension coincide com o tipo de elemento que iremos trabalhar, por exemplo, o público alvo da operação.

   A dimensão do filtro permite coletar esses elementos, por exemplo, informações relacionadas à pessoa alvo (contratos, liquidações completas e finais etc.).

   Para obter mais informações, consulte [Direcionamento e dimensões de filtragem](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).

   ![](assets/s_user_segmentation_query_edit.png)

   Um query pode ser baseado em dados a partir da transição de entrada, se necessário, selecionando **[!UICONTROL Temporary schema]** ao escolher o targeting e a dimensão de filtro.

   ![](assets/query_temporary_table.png)

1. Defina os públicos usando o assistente. Os campos a serem inseridos podem variar de acordo com o tipo de target. Você pode visualizar o público-alvo com seus critérios atuais usando a guia **[!UICONTROL Preview]**.

   Para obter mais informações sobre como criar e usar filtros ou queries, consulte esta [seção](../../platform/using/filtering-options.md).

   ![](assets/s_user_segmentation_wizard.png)

1. Se você selecionou **[!UICONTROL Filtering conditions]** na etapa 1 ou usou a opção **[!UICONTROL Filters]** > **[!UICONTROL Advanced filter...]**, será necessário adicionar manualmente os critérios de filtragem posteriormente.

   Você também pode adicionar condições de agrupamento de dados marcando a caixa correspondente. Para fazer isso, a dimensão de filtro deve ser diferente do targeting dimension do query. Para obter mais informações sobre agrupamento, consulte esta [seção](../../workflow/using/querying-using-grouping-management.md).

   Você também pode adicionar mais critérios usando o Construtor de Expressões e combinando com as opções lógicas AND, OR e EXCEPT. Em seguida, é possível pré-visualizar o **[!UICONTROL Corresponding SQL query...]** para sua combinação de critérios. Para obter mais informações, consulte [esta seção](../../platform/using/defining-filter-conditions.md#building-expressions).

   Salve seu filtro se quiser reutilizá-lo posteriormente.

   ![](assets/s_user_segmentation_query_advanced.png)

## Adição de dados {#adding-data}

As colunas adicionais permitem coletar informações adicionais sobre o público alvo, como, por exemplo, números de contrato, assinaturas de boletins informativos ou origem. Esses dados podem ser armazenados no banco de dados do Adobe Campaign ou em um banco de dados externo.

O link **[!UICONTROL Add data...]** permite selecionar os dados adicionais a serem coletados.

![](assets/wf_add_data_link.png)

Comece selecionando o tipo de dado a ser adicionado:

![](assets/wf_add_data_1st_option.png)

* Selecione **[!UICONTROL Data linked to the filtering dimension]** para selecionar os dados no banco de dados do Adobe Campaign.
* Selecione **[!UICONTROL External data]** para adicionar dados de um banco de dados externo. Essa opção só estará disponível se você tiver adquirido a opção **Federated Data Access** . Para obter mais informações, consulte [Acesso a um banco de dados externo (FDA)](../../workflow/using/accessing-an-external-database--fda-.md).
* Selecione a opção **[!UICONTROL An offer proposition]** para adicionar um conjunto de colunas que permitem armazenar a melhor apresentação gerada pelo mecanismo de oferta. Essa opção só estará disponível se você tiver adquirido o módulo **Interaction** .

Se nenhum módulo opcional estiver instalado na plataforma, esse estágio não será exibido. Você será direcionado ao próximo estágio.

Para adicionar dados do banco de dados do Adobe Campaign:

1. Selecione o tipo de dado que deseja adicionar. Isso pode ser dados pertencentes à dimensão de filtro ou dados armazenados em tabelas vinculadas.

   ![](assets/query_add_columns.png)

1. Se os dados pertencerem à dimensão de filtro do query, basta selecioná-lo na lista de campos disponíveis para exibi-lo nas colunas de output.

   ![](assets/wf_add_data_field_selection.png)

   Você pode adicionar:

   * Um campo calculado com base nos dados obtidos do público alvo ou em um agregado (número de compras pendentes no último mês, quantidade média de um recibo, etc.). Para obter um exemplo, acesse [Seleção de dados](../../workflow/using/targeting-data.md#selecting-data).
   * Um novo campo, criado por meio do botão **[!UICONTROL Add]** à direita da lista de colunas de output.

      Você também pode adicionar uma coleção de informações, por exemplo, uma lista de contratos, os últimos 5 deliveries, etc. As coleções coincidem com os campos que podem ter múltiplos valores para o mesmo perfil (relação 1-N). Para obter mais informações, consulte [Edição de dados adicionais](../../workflow/using/targeting-data.md#editing-additional-data).

Para adicionar uma coleção de informações vinculadas a um público alvo:

1. Na primeira etapa do assistente, selecione a opção **[!UICONTROL Data linked to the filtering dimension]**:
1. Selecione a tabela que contém as informações que você deseja coletar e clique em **[!UICONTROL Next]**.

   ![](assets/wf_add_data_linked_table.png)

1. Se necessário, especifique o número de elementos da coleção que você deseja manter ao selecionar um dos valores no campo **[!UICONTROL Data collected]**. Por padrão, todas as linhas da coleção são recuperadas e filtradas de acordo com as condições especificadas na etapa a seguir.

   * Se um único elemento da coleção coincide com as condições de filtragem desta coleção, selecione **[!UICONTROL Single row]** no campo **[!UICONTROL Data collected]**.

      >[!IMPORTANT]
      >
      >Esse modo otimiza o query SQL gerada graças a uma junção direta dos elementos de coleção.
      >
      >Se a condição inicial não for respeitada, o resultado pode ser falho (linhas ausentes ou sobrepostas).

   * Se você optar por recuperar várias linhas (**[!UICONTROL Limit the line count]**), será possível especificar o número de linhas a serem coletadas.
   * Se as colunas coletadas contiverem agregados, por exemplo, o número de falhas declaradas, a despesa média em um site, etc. você poderá usar o valor **[!UICONTROL Aggregates]**.

   ![](assets/query_add_collection_param.png)

1. Especifique a subseleção da coleção. Por exemplo: compras somente dos últimos 15 dias.

   ![](assets/query_add_columns_collection_filter.png)

1. Se você selecionou a opção **[!UICONTROL Limit the line count]**, defina a ordem na qual os dados coletados serão filtrados. Quando o número de linhas coletadas for maior que o número de linhas especificado a ser mantido, a ordem de filtragem permite que você especifique quais linhas manter.

## Exemplo: direcionamento em atributos de recipients simples {#example--targeting-on-simple-recipient-attributes}

No exemplo a seguir, o query busca identificar homens que moram na França com idades entre 18 e 30. Este query será usado em um workflow que visa fazer uma oferta exclusiva, por exemplo.

>[!NOTE]
>
>Os exemplos de query são apresentados [nesta seção](../../workflow/using/querying-recipient-table.md).

1. Nomeie o query e selecione o link **[!UICONTROL Edit query...]**.
1. Selecione **[!UICONTROL Filtering conditions]** na lista de tipos de filtros disponíveis.
1. Insira os diferentes critérios para o target proposto. Os critérios são combinados usando a opção AND. Para ser incluído na seleção, os recipients terão de cumprir as quatro condições seguintes:

   * Recipients cujo título é &quot;Sr.&quot; (também é possível encontrar pelo campo **Sexo** e selecionar **Masculino** como valor).
   * Recipients abaixo de 30 anos.
   * Recipients acima de 18 anos.
   * Recipients que vivem na França.

   ![](assets/query_example.png)

   Você pode exibir o SQL correspondente com sua combinação de critérios:

   ![](assets/query_example_sql.png)

1. Você pode verificar se os seus critérios estão corretos visualizando os recipients que correspondam ao seu query na guia relevante:

   ![](assets/query_example_preview.png)

1. Salve os filtros para usá-los posteriormente clicando em **[!UICONTROL Finish]** > **[!UICONTROL OK]**.
1. Continue editando seu workflow adicionando outras atividades a ele. Depois de iniciado e após o término da etapa de query anterior, o número de recipients encontrados será exibido. Você pode exibir mais detalhes usando o menu pop-up do mouse (clique com o botão direito do mouse na transição > **[!UICONTROL Display the target...]**).

   ![](assets/query_example_result.png)

## Parâmetros de output {#output-parameters}

* tableName
* schema
* recCount

Esse conjunto de três valores identifica o público alvo do query. **[!UICONTROL tableName]** é o nome da tabela que registra os identificadores de target, **[!UICONTROL schema]** é o schema do público (normalmente nms:recipient) e **[!UICONTROL recCount]** é o número de elementos na tabela.

Este valor é o schema da tabela de trabalho. Esse parâmetro é válido para todas as transições com **[!UICONTROL tableName]** e **[!UICONTROL schema]**.

## Otimização das consultas {#optimizing-queries}

A seção abaixo fornece as práticas recomendadas para otimizar as consultas executadas no Adobe Campaign, a fim de limitar a carga de trabalho no banco de dados e melhorar a experiência do usuário.

### Associações e índices {#joins-and-indexes}

* Consultas eficientes dependem de índices.
* Use um índice para todas as associações.
* A definição de links no esquema determinará as condições da associação. A tabela vinculada deve ter um índice exclusivo na chave primária e a associação deve estar nesse campo.
* Realize associações definindo chaves em campos numéricos em vez de campos de sequência.
* Evite realizar associações externas. Sempre que possível, use o registro Zero ID para obter a funcionalidade de associação externa.
* Use o tipo de dados correto para associações.

   Certifique-se de que a `where` cláusula tenha o mesmo tipo do campo.

   Um erro comum é: `iBlacklist='3'` where `iBlacklist` é um campo numérico e `3` significa um valor de texto.

   Verifique se você sabe qual será o plano de execução da consulta. Evite varreduras completas de tabelas, especialmente para consultas em tempo real ou consultas quase em tempo real em execução a cada minuto.

Para obter mais informações, consulte as [Práticas recomendadas do modelo de dados](https://helpx.adobe.com/br/campaign/kb/acc-data-model-best-practices.html) e as seções de [Mapeamento do banco de dados](../../configuration/using/database-mapping.md).

### Funções {#functions}

* Cuidado com funções como `Lower(...)`. Quando a função Lower é usada, o Index não é usado.
* Verifique cuidadosamente as consultas usando a instrução &quot;like&quot; ou as instruções &quot;upper&quot; ou &quot;lower&quot;. Aplique &quot;Upper&quot; na entrada do usuário, não no campo do banco de dados.

   Para saber mais sobre as funções, consulte [esta seção](../../platform/using/defining-filter-conditions.md#list-of-functions).

### Filtrar dimensões {#filtering-dimensions}

Use a dimensão do filtro da consulta em vez de usar o operador &quot;exists such as&quot;.

![](assets/optimize-queries-filtering.png)

Em consultas, as condições &quot;exists such as&quot; em filtros não são eficientes. Elas são o equivalente de uma subconsulta no SQL:

`select iRecipientId from nmsRecipient where iRecipientId IN (select iRecipientId from nmsBroadLog where (...))`

A prática recomendada é usar a dimensão do filtro da consulta:

![](assets/optimize-queries-filtering2.png)

O equivalente da dimensão do filtro no SQL é a associação interna:

`select iRecipientId from nmsRecipient INNER JOIN nmsBroadLog ON (...)`

Para saber mais sobre as dimensões do filtro, consulte [esta seção](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).

### Arquitetura {#architecture}

* Crie uma plataforma de desenvolvimento com volumes, parâmetros e arquitetura semelhantes à plataforma de produção.
* Use os mesmos valores para os ambientes de desenvolvimento e produção. Na medida do possível, use as mesmas opções de:

   * sistema operacional,
   * versão,
   * data,
   * aplicação,
   * volumes.

   >[!NOTE]
   >
   >Um recurso que funciona em um ambiente de desenvolvimento pode não funcionar em um ambiente de produção onde os dados podem ser diferentes. Tente identificar as principais diferenças para antecipar os riscos e preparar soluções.

* Faça configurações que correspondam aos volumes de target. Grandes volumes exigem configurações específicas. Uma configuração que funcionou para 100.000 recipients pode não funcionar para 10.000.000 recipients.

   Considere como o sistema será dimensionado quando ele for acionado. Só porque algo funciona em pequena escala não significa que seja adequado com volumes maiores. Os testes devem ser feitos com volumes semelhantes aos da produção. Você também deve avaliar o efeito das alterações nos volumes (número de chamadas, tamanho do banco de dados) nas horas de pico, dias de pico e ao longo da vida útil do projeto.
