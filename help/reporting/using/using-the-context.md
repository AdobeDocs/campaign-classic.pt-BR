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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Uso do contexto{#using-the-context}

Quando você deseja representar dados na forma de **[!UICONTROL tables]** ou **[!UICONTROL charts]**, eles podem ser obtidos de duas fontes: uma nova consulta (consulte [Definição de um filtro direto em dados](#defining-a-direct-filter-on-data)) ou o contexto do relatório (consulte [Uso de dados](#using-context-data)de contexto).

## Definição de um filtro direto em dados {#defining-a-direct-filter-on-data}

### Filtrar dados {#filtering-data}

Using a **[!UICONTROL Query]** type activity isn&#39;t mandatory when building a report. Os dados podem ser filtrados diretamente nas tabelas e nos gráficos que compõem o relatório.

This enables you to select the data to display in the report directly via the **[!UICONTROL Page]** activity of the report.

To do this, click the **[!UICONTROL Filter data...]** link in the **[!UICONTROL Data]** tab: this link lets you access the expressions editor to define a query on the data to be analyzed.

![](assets/reporting_filter_data_from_page.png)

### Exemplo: usar um filtro em um gráfico {#example--use-a-filter-in-a-chart}

No exemplo a seguir, queremos que o gráfico mostre apenas perfis de recipients que vivem na França e que tenham efetuado uma compra durante o ano.

Para definir esse filtro, coloque uma página no gráfico e edite-o. Click the **[!UICONTROL Filter data]** link and create the filter that matches the data you want to display. Para obter mais informações sobre criação de queries no Adobe Campaign, consulte [esta seção](../../platform/using/about-queries-in-campaign.md).

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
1. Go to the **[!UICONTROL Data]** tab and select the cube to be used.
1. Click the **[!UICONTROL Filter data...]** link and define the following query to remove Adobe from the list of companies.

   ![](assets/s_ncs_advuser_report_display_03.png)

Somente os recipients que atenderem aos critérios de filtragem aparecerão no relatório.

![](assets/s_ncs_advuser_report_display_04.png)

## Uso de dados de contexto {#using-context-data}

To represent data in the form of a **[!UICONTROL table]** or a **[!UICONTROL chart]**, the data can come from the report context.

In the page that contains the table or the chart, the **[!UICONTROL Data]** tab lets you select the data source.

![](assets/s_ncs_advuser_report_datasource_3.png)

* The **[!UICONTROL New query]** option lets you build a query to collect data. Para obter mais informações, consulte [Definição de um filtro direto nos dados](#defining-a-direct-filter-on-data).
* The **[!UICONTROL Context data]** option lets you use the input data: the context of the report coincides with the information contained in the inbound transition of the page that contains the chart or the table. This context may, for instance, contain data collected via a **[!UICONTROL Query]** activity placed before the **[!UICONTROL Page]** activity and for which you need to specify the table and the fields that the report concerns.

Por exemplo, em uma caixa de query, crie a seguinte query para os recipients:

![](assets/s_ncs_advuser_report_datasource_2.png)

Em seguida, indique a fonte de dados no relatório, neste caso: **[!UICONTROL Data from the context]**.

O local de dados é inferido automaticamente. Se necessário, é possível forçar o caminho de dados.

![](assets/s_ncs_advuser_report_datasource_4.png)

Quando selecionar os dados que as estatísticas abordarão, os campos disponíveis correspondem aos dados especificados na query.

![](assets/s_ncs_advuser_report_datasource_1.png)

