---
title: Uso do contexto
seo-title: Uso do contexto
description: Uso do contexto
seo-description: null
page-status-flag: never-activated
uuid: ac8c7068-d640-4934-b7f5-bc91b98eab4c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 72fe6df0-0271-48f9-bd6d-bb1ff25fbdf3
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 79%

---


# Uso do contexto{#using-the-context}

When you want to represent data in the form of **[!UICONTROL tables]** or **[!UICONTROL charts]**, it can be taken from two sources: a new query (refer to [Defining a direct filter on data](#defining-a-direct-filter-on-data)) or the report context (refer to [Using context data](#using-context-data)).

## Definição de um filtro direto em dados {#defining-a-direct-filter-on-data}

### Filtrar dados {#filtering-data}

A utilização de uma atividade do tipo **[!UICONTROL Query]** não é obrigatória ao criar um relatório. Os dados podem ser filtrados diretamente nas tabelas e nos gráficos que compõem o relatório.

Isso permite selecionar os dados a serem exibidos no relatório diretamente por meio da atividade **[!UICONTROL Page]** do relatório.

To do this, click the **[!UICONTROL Filter data...]** link in the **[!UICONTROL Data]** tab: this link lets you access the expressions editor to define a query on the data to be analyzed.

![](assets/reporting_filter_data_from_page.png)

### Exemplo: usar um filtro em um gráfico {#example--use-a-filter-in-a-chart}

No exemplo a seguir, queremos que o gráfico mostre apenas perfis de recipients que vivem na França e que tenham efetuado uma compra durante o ano.

Para definir esse filtro, coloque uma página no gráfico e edite-o. Clique em **[!UICONTROL Filter data]** e crie o filtro que corresponde aos dados que deseja exibir. Para obter mais informações sobre criação de queries no Adobe Campaign, consulte [esta seção](../../platform/using/about-queries-in-campaign.md).

![](assets/s_ncs_advuser_report_wizard_029.png)

Aqui, queremos exibir a análise por cidade dos recipients selecionados.

![](assets/reporting_graph_with_2vars.png)

A renderização terá esta aparência:

![](assets/reporting_graph_with_2vars_preview.png)

### Exemplo: usar um filtro em uma tabela dinâmica {#example--use-a-filter-in-a-pivot-table}

Neste exemplo, o filtro permite exibir somente clientes não parisienses na tabela dinâmica, sem usar outra query antecipadamente.

Siga as etapas abaixo:

1. Coloque uma página no gráfico e edite-o.
1. Crie uma tabela dinâmica.
1. Vá para a guia **[!UICONTROL Data]** e selecione o cubo a ser usado.
1. Click the **[!UICONTROL Filter data...]** link and define the following query to remove Adobe from the list of companies.

   ![](assets/s_ncs_advuser_report_display_03.png)

Somente os recipients que atenderem aos critérios de filtragem aparecerão no relatório.

![](assets/s_ncs_advuser_report_display_04.png)

## Uso de dados de contexto {#using-context-data}

To represent data in the form of a **[!UICONTROL table]** or a **[!UICONTROL chart]**, the data can come from the report context.

Na página que contém a tabela ou o gráfico, a guia **[!UICONTROL Data]** permite selecionar a fonte de dados.

![](assets/s_ncs_advuser_report_datasource_3.png)

* A opção **[!UICONTROL New query]** permite criar uma consulta para coletar dados. Para obter mais informações, consulte [Definição de um filtro direto nos dados](#defining-a-direct-filter-on-data).
* A opção **[!UICONTROL Context data]** permite usar os dados de entrada: o contexto do relatório coincide com as informações contidas na transição de entrada da página que contém o gráfico ou a tabela. Esse contexto pode, por exemplo, conter dados coletados por uma atividade **[!UICONTROL Query]** colocada antes da atividade **[!UICONTROL Page]** e para a qual é necessário especificar a tabela e os campos que o relatório aborda.

Por exemplo, em uma caixa de query, crie a seguinte query para os recipients:

![](assets/s_ncs_advuser_report_datasource_2.png)

Em seguida, indique a fonte de dados no relatório, neste caso: **[!UICONTROL Data from the context]**.

O local de dados é inferido automaticamente. Se necessário, é possível forçar o caminho de dados.

![](assets/s_ncs_advuser_report_datasource_4.png)

Quando selecionar os dados que as estatísticas abordarão, os campos disponíveis correspondem aos dados especificados na query.

![](assets/s_ncs_advuser_report_datasource_1.png)

