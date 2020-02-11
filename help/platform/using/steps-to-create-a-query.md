---
title: Etapas para criar um query
seo-title: Etapas para criar um query
description: Etapas para criar um query
seo-description: null
page-status-flag: never-activated
uuid: 9668f49c-2da7-42c8-8728-8d644c787935
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: creating-queries
discoiquuid: d538f489-f1ae-4682-9c21-d0300bd42b26
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# Etapas para criar um query{#steps-to-create-a-query}

As etapas para criar um query no Adobe Campaign são as seguintes:

1. Selecione a tabela de trabalho. Consulte a [Etapa 1 - Escolher uma tabela](#step-1---choose-a-table).
1. Em seguida, selecione os dados a serem extraídos. Consulte a [Etapa 2 - Escolha os dados a serem extraídos](#step-2---choose-data-to-extract).
1. Defina a sequência de classificação de dados. Consulte a [Etapa 3 - Classificar dados](#step-3---sort-data).
1. Filtre os dados. Consulte a [Etapa 4 - Filtrar dados](#step-4---filter-data).
1. Formate os dados. Consulte a [Etapa 5 - Formatar dados](#step-5---format-data).
1. Exiba o resultado. Consulte a [Etapa 6 - Visualizar dados](#step-6---preview-data).

>[!NOTE]
>
>Todas essas etapas estão disponíveis no editor de query genérico. Quando um query é criado em outro contexto, algumas etapas podem ser deixadas de fora.\
>The Query activity is presented in [this section](../../workflow/using/query.md).

## Etapa 1 - Escolher uma tabela {#step-1---choose-a-table}

Select the table containing the data you want to query in the **[!UICONTROL Document type]** window. If necessary, filter the data using the filter field or the **[!UICONTROL Filters]** button.

![](assets/query_editor_nveau_21.png)

## Etapa 2 - Escolher dados para extrair {#step-2---choose-data-to-extract}

In the **[!UICONTROL Data to extract]** window, select the data to display: these fields will make up the output columns.

Por exemplo, selecione **[!UICONTROL Age]**, **[!UICONTROL Primary key]** e **[!UICONTROL Email domain]** e **[!UICONTROL City]**. Os resultados serão organizados com base nessa seleção. Use as setas azuis à direita da janela para alterar a ordem da coluna.

![](assets/query_editor_nveau_01.png)

Você pode editar uma expressão inserindo uma fórmula nela ou executando um processo em uma função agregada. Para fazer isso, clique no campo da **[!UICONTROL Expression]** coluna e selecione **[!UICONTROL Edit expression]**.

![](assets/query_editor_nveau_97.png)

It is possible to group output column data: to do this, check **[!UICONTROL Yes]** in the **[!UICONTROL Group]** column of the **[!UICONTROL Data to extract]** window. Essa função gera um resultado ao redor do eixo de agrupamento marcado. Um exemplo de query com agrupamento está disponível [nesta seção](../../workflow/using/querying-delivery-information.md).

![](assets/query_editor_nveau_56.png)

* The **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** function lets you &quot;group by&quot; and select what has been grouped (&quot;having&quot;). Essa função se aplica a todos os campos na coluna de saída. Por exemplo, essa opção permite agrupar todas as escolhas de uma coluna de saída e recuperar um tipo específico de informações, como destinatários de idade entre 35 e 50.

   Para obter mais informações, consulte [esta seção](../../workflow/using/querying-using-grouping-management.md).

* The **[!UICONTROL Remove duplicate rows (DISTINCT)]** function lets you deduplicate identical results obtained in the output column. Por exemplo, se você realizar um censo selecionando os campos de sobrenome, nome e email na coluna de saída, os que tiverem dados idênticos serão eliminados, pois isso significa que o mesmo contato foi inserido várias vezes no banco de dados. Sendo assim, somente um resultado será levado em conta.

## Etapa 3 - Classificar dados {#step-3---sort-data}

The **[!UICONTROL Sorting]** window lets you sort column content. Use as setas para modificar a ordem de exibição:

* The **[!UICONTROL Sorting]** column enables a simple sort and arranges column content from A to Z or in ascending order.
* The **[!UICONTROL Descending sort]** arranges the content from Z to A and in descending order. Isso é útil para demonstrar os maiores resultados de venda: as figuras maiores são mostradas na parte superior da lista.

Neste exemplo, os dados são classificados em ordem crescente com base na idade do destinatário.

![](assets/query_editor_nveau_57.png)

## Etapa 4 - Filtrar dados {#step-4---filter-data}

O editor de query permite que você filtre os dados para refinar sua pesquisa.

Os filtros oferecidos dependem da tabela à qual o query se refere.

![](assets/query_editor_nveau_09.png)

Once you select the **[!UICONTROL Filtering conditions]** you will access the **[!UICONTROL Target elements]** section: this lets you define how to filter the data to collect.

* Para criar um novo filtro, selecione os campos, operadores e valores necessários para a criação da fórmula a ser verificada para que os dados sejam selecionados. It&#39;s possible to combine several conditions (for more on this, refer to [Defining filter conditions](../../platform/using/defining-filter-conditions.md)).
* To use previously saved filters, open the drop-down list by clicking the **[!UICONTROL Add]** button, click **[!UICONTROL Predefined filter]** and select the one you want.

   ![](assets/query_editor_15.png)

* The filters created in the **[!UICONTROL Generic query editor]** are available in other query applications and vice versa. To save a filter, click the **[!UICONTROL Save]** icon.

   >[!NOTE]
   >
   >For more on creating and using filters, refer to [Filtering options](../../platform/using/filtering-options.md).

Como mostrado no exemplo a seguir, para recuperar todos os destinatários falantes de inglês, selecione: &quot;Língua do destinatário **igual** a EN&quot;.

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>You can directly access an option by typing the following formula in the **Value** field: **$(options:OPTION_NAME)**.

Click the **[!UICONTROL Preview]** tab to view the result of the filtering condition. Nesse caso, todos os destinatários que falam inglês são exibidos com sobrenome, nome e endereço de email.

![](assets/query_editor_nveau_98.png)

Users familiar with SQL language can click **[!UICONTROL Generate SQL query]** to view the query in SQL.

![](assets/query_editor_nveau_99.png)

## Etapa 5 - Formatar dados {#step-5---format-data}

Once you have configured the restriction filters, you will access the **[!UICONTROL Data formatting]** window. Essa janela permite que você reorganize as colunas de saída, transforme dados e altere letras maiúsculas e minúsculas dos rótulos de coluna. Ela também permite aplicar uma fórmula ao resultado final usando um campo calculado.

>[!NOTE]
>
>For more information on the types of calculated fields, refer to [Creating calculated fields](../../platform/using/defining-filter-conditions.md#creating-calculated-fields).

Colunas não verificadas não serão mostradas na janela de visualização de dados.

![](assets/query_editor_nveau_10.png)

The **[!UICONTROL Transformation]** column lets you change a column label to upper or lower case. Select the column and click in the **[!UICONTROL Transformation]** column. Você pode escolher:

* **[!UICONTROL Switch to lower case]**,
* **[!UICONTROL Switch to upper case]**,
* **[!UICONTROL First letter in upper case]**.

![](assets/query_editor_nveau_42.png)

## Etapa 6 - Visualizar dados {#step-6---preview-data}

A **[!UICONTROL Data preview]** janela é o último estágio. Clique em **[!UICONTROL Start the preview of the data]** para obter o resultado da consulta. Ele está disponível em colunas ou no formato XML. Click the **[!UICONTROL Generated SQL queries]** tab to view the query in SQL format.

Neste exemplo, dados são classificados em ordem crescente com base na idade do destinatário.

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>By default, only the first 200 lines are displayed in the **[!UICONTROL Data preview]** window. Para alterar isso, digite um número na **[!UICONTROL Lines to display]** caixa e clique em **[!UICONTROL Start the preview of the data]**.

