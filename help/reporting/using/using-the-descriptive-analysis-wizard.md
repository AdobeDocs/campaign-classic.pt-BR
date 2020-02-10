---
title: Uso do assistente de análise descritiva
seo-title: Uso do assistente de análise descritiva
description: Uso do assistente de análise descritiva
seo-description: null
page-status-flag: never-activated
uuid: 30554909-4b91-46ff-bd8d-fa57ab6304f9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: analyzing-populations
discoiquuid: 18ba04d9-7bab-4eea-8dbb-6c2c138c5293
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Uso do assistente de análise descritiva{#using-the-descriptive-analysis-wizard}

Para criar um relatório de análise descritiva, use o assistente dedicado. A configuração depende dos dados a serem analisados e da renderização desejada.

## Análise de dados no banco de dados {#analyzing-data-in-the-database}

The descriptive analysis wizard can be launched via the **[!UICONTROL Tools > Descriptive analysis]** menu: in this case, the analysis concerns recipients by default (**nms:recipient**). Aplica-se a todos os dados do banco de dados do Adobe Campaign.

![](assets/reporting_descriptive_wz_launch.png)

To analyze a table other than the standard recipients one (**nms:recipient**), click the **[!UICONTROL Advanced settings...]** link in the last stage of the wizard and select the table that matches your settings, in this case **cus:individual**:

![](assets/reporting_descriptive_other_schema.png)

If you want to produce statistics on part of the data, you can define a filter: to do this, click the **[!UICONTROL Advanced settings...]** link and define the filter to apply, as shown below:

![](assets/reporting_descriptive_wz_filter.png)

A análise só abordará os recipients do banco de dados com 16 anos de idade ou mais e que moram em Londres.

## Análise de um conjunto de dados {#analyzing-a-set-of-data}

É possível usar o assistente de análise descritiva por meio de um contexto diferente: uma lista, uma transição de workflow, um ou mais deliveries, uma seleção de recipients, etc.

Ele pode ser acessado por vários nós da árvore do Adobe Campaign que apontam para a tabela de recipients.

Abra o assistente de análise descritiva selecionando os itens e clicando com o botão direito. Somente os dados selecionados serão analisados.

![](assets/reporting_descriptive_from_recipients.png)

* For a set of **recipients**, select the recipients to be analyzed, then right-click and select **[!UICONTROL Actions > Explore...]**, as shown above. Se um filtro for aplicado à lista de recipients, somente seu conteúdo será analisado.

   Para selecionar todos os recipients na pasta ou no filtro atual, use o atalho CTRL+A. Isso significa selecionar até mesmo os recipients não mostrados.

   For an example of the descriptive analysis of recipients, refer to: [Qualitative data analysis](../../reporting/using/use-cases.md#qualitative-data-analysis).

* In the context of a **workflow**, place the cursor on a transition that points towards the recipients table, right-click and select **[!UICONTROL Analyze target]**. Para obter mais informações, consulte o exemplo em [Análise de uma meta de transição em um fluxo de trabalho](../../reporting/using/use-cases.md#analyzing-a-transition-target-in-a-workflow).
* Para **listas**, selecione uma ou mais listas e aplique o mesmo processo dos recipients.
* In the context of a **delivery**, select the deliveries whose target you want to analyze, right-click and select **[!UICONTROL Actions > Explore the target]**, as shown below:

   ![](assets/reporting_descriptive_from_deliveries.png)

   Exemplos de análises descritivas para entregas são fornecidos aqui: [Analisando uma população](../../reporting/using/use-cases.md#analyzing-a-population) e aqui: [Analisando registros](../../reporting/using/use-cases.md#analyzing-recipient-tracking-logs)de rastreamento de destinatários.

## Configuração do template de distribuição qualitativa {#configuring-the-qualitative-distribution-template}

The **[!UICONTROL Qualitative distribution]** template lets you create statistics on all types of data (e.g. company name, email domain).

As opções de configuração disponíveis para um relatório criado por meio do **[!UICONTROL Qualitative distribution]** modelo são detalhadas em [Exibição de dados na tabela](#displaying-data-in-the-table). Um exemplo completo é detalhado na [Análise de uma população](../../reporting/using/use-cases.md#analyzing-a-population).

Ao utilizar o assistente de análise descritiva para analisar seus dados, as opções disponíveis dependem das configurações escolhidas. Veja os detalhes abaixo.

### Compartimentalização de dados {#data-binning}

Quando selecionar as variáveis a serem exibidas, é possível definir compartimentalização de dados, em outras palavras, configurar critérios de agrupamento para os dados selecionados.

![](assets/s_ncs_user_report_wizard_031.png)

>[!NOTE]
>
>When the field concerned by the calculation is computed using an aggregate, check **[!UICONTROL The data is already aggregated]** to improve performances.

As opções serão diferentes dependendo do conteúdo do campo:

* **[!UICONTROL None]** : essa opção permite exibir todos os valores disponíveis para a variável, sem vinculação.

   >[!CAUTION]
   >
   >Essa opção deve ser usada com cuidado: pode ter um grande impacto no relatório e no desempenho da máquina.

* **[!UICONTROL Auto]** : essa opção permite exibir os n valores representados com mais frequência. Eles são calculados automaticamente e cada um representa uma porcentagem das variáveis comparadas ao número de agrupamentos. Para valores numéricos, o Adobe Campaign gera automaticamente n classes para classificar os dados.
* **[!UICONTROL Manual]** : essa opção funciona como a **[!UICONTROL Auto]** opção, exceto que você pode definir esses valores manualmente. To do this, click the **[!UICONTROL Add]** button to the right of the value table.

   Values can be initialized automatically by Adobe Campaign before personalization: to do this, enter the number of bins you want to generate and click the **[!UICONTROL Initialize with]** link, as shown below:

   ![](assets/reporting_descriptive_initialize.png)

   Em seguida, adapte o conteúdo às necessidades:

   ![](assets/reporting_descriptive_initialize_perso.png)

   Dependendo do nível de precisão desejado, os campos contendo datas podem ser agrupados por tempo, dia, mês, ano, etc.

   ![](assets/reporting_descriptive_group_by_year.png)

* **[!UICONTROL Modulo]** : permite criar grupos de valores no caso de valores numéricos. Por exemplo, um módulo com um valor de 10 permite criar um intervalo de valores que variam de dez em dez.

   ![](assets/reporting_descriptive_initialize_modulo.png)

   Esse exemplo permite visualizar o detalhamento dos recipients por faixa etária.

   ![](assets/reporting_descriptive_initialize_modulo_result.png)

### Exibição de dados na tabela {#displaying-data-in-the-table}

Use a barra de ferramentas para personalizar a exibição das variáveis na tabela: exclua uma coluna, exiba dados em linhas em vez de colunas, mova uma coluna para a esquerda ou direita, exiba ou altere o cálculo de valores.

![](assets/s_ncs_user_report_wizard_toolbar.png)

A seção superior da janela permite selecionar as configurações de exibição.

É possível exibir ou ocultar o nome das estatísticas e subtotais e escolher a orientação das estatísticas. Para obter mais informações, consulte as configurações [de exibição do relatório de](../../reporting/using/processing-a-report.md#analysis-report-display-settings)Análise.

### Exibição de dados no gráfico {#displaying-data-in-the-chart}

Na primeira etapa do assistente de análise descritiva, é possível optar por exibir os dados no formulário do gráfico somente sem uma tabela. Nesse caso, a seleção variável deve ser feita ao configurar o gráfico. Primeiro, é necessário selecionar o número de variáveis a serem exibidas e selecionar os campos do banco de dados relevante.

![](assets/s_ncs_user_report_wizard_023.png)

Em seguida, selecione o tipo de gráfico desejado.

![](assets/s_ncs_user_report_wizard_024.png)

>[!NOTE]
>
>É possível exibir as variáveis em um gráfico e uma tabela ao mesmo tempo. To do this, enter the variables in the **[!UICONTROL Table configuration]** window. Click **[!UICONTROL Next]** and select the type of chart in the chart configuration window. Se subdimensões forem definidas na tabela, elas não serão exibidas no gráfico.

Click the **[!UICONTROL Variants]** link to modify the chart properties.

![](assets/reporting_descriptive_graphe_options.png)

As opções oferecidas dependem do tipo de gráfico selecionado. Para obter mais informações, consulte [esta página](../../reporting/using/creating-a-chart.md#chart-types-and-variants).

### Cálculo de estatísticas {#statistics-calculation}

O assistente de análise descritiva permite calcular vários tipos de estatística dos dados. Por padrão, somente uma contagem simples é configurada.

Click **[!UICONTROL Add]** to create a new statistic.

![](assets/reporting_descriptive_create_stat.png)

As seguintes operações são possíveis:

* **[!UICONTROL Count]** para contar todos os valores não nulos do campo a ser agregado, incluindo valores duplicados (do campo agregado),
* **[!UICONTROL Average]** para calcular a média dos valores em um campo numérico,
* **[!UICONTROL Minimum]** para calcular o mínimo dos valores em um campo numérico,
* **[!UICONTROL Maximum]** para calcular o máximo dos valores em um campo numérico,
* **[!UICONTROL Sum]** para calcular a soma dos valores em um campo numérico,
* **[!UICONTROL Standard deviation]** para calcular como os valores retornados são dispersos em torno da média,
* **[!UICONTROL Row percentage distribution]** calcular o rácio do valor numa coluna e o valor numa linha (disponível apenas para tabelas),
* **[!UICONTROL Column percentage distribution]** para calcular a relação entre o valor numa linha e o valor numa coluna (disponível apenas para tabelas),
* **[!UICONTROL Total percentage distribution]** calcular a distribuição dos destinatários em causa pelos valores,

   ![](assets/s_ncs_user_report_wizard_026.png)

* **[!UICONTROL Calculated field]** para criar um operador personalizado (disponível somente para tabelas). The **[!UICONTROL User function]** field lets you enter the calculation to be applied to the data.

   Exemplo: Calculando o valor médio de compra por cliente com base no país e na origem

   ![](assets/report_compute_data_sample1.png)

   Para exibir as informações acima em uma tabela, é preciso criar um campo calculado para armazenar o valor médio de compra por cliente.

   Para fazer isso:

   1. Calcule o total de compras.

      ![](assets/report_compute_data_sample2.png)

   1. Esta estatística não será exibida na tabela. É necessário desmarcar a opção **[!UICONTROL Display in the table]** da **[!UICONTROL Advanced]** guia.

      ![](assets/report_compute_data_sample3.png)

   1. Crie uma nova estatística de **[!UICONTROL Calculated field]** tipo e informe a seguinte fórmula no **[!UICONTROL User function]** campo: **@buy/@count**.

      ![](assets/report_compute_data_sample4.png)

### Exibição do relatório {#displaying-the-report}

A última etapa do assistente permite exibir o relatório, ou seja, a tabela ou o gráfico como foram configurados.

Quando o relatório contém uma tabela, a célula do resultado do cálculo é colorida. Quanto maior o resultado, mais intensa será a cor.

![](assets/report_compute_data_sample1.png)

É possível alterar o layout dos resultados. Para fazer isso, clique com o botão direito do mouse na variável correspondente e selecione a entrada do menu de atalho.

![](assets/s_ncs_user_report_wizard_029.png)

Quando o relatório inclui um gráfico, os rótulos da legenda permitem filtrar as informações exibidas: clique em um rótulo para ativar/desativar exibição no gráfico.

![](assets/report_display_data_in_graph.png)

## Configuração do template de distribuição quantitativa {#configuring-the-quantitative-distribution-template}

Para gerar uma análise descritiva por conta própria, selecione a opção **New descriptive analysis from a template** se não estiver definida por padrão.

The **[!UICONTROL Quantitative distribution]** template that lets you generate statistics on data which can be measured or counted (e.g. invoice amount, age of recipients).

The configuration mode of an analysis report created via the **[!UICONTROL Quantitative distribution]** template is detailed in an implementation example [Quantitative data analysis](../../reporting/using/use-cases.md#quantitative-data-analysis).

As opções disponíveis ao utilizar o assistente de análise descritiva para criar um relatório quantitativo são detalhadas abaixo.

Comece selecionando a variável que os cálculos abordarão:

![](assets/s_ncs_user_report_wizard_017.png)

Por padrão, o Adobe Campaign oferece uma série de estatísticas a serem calculadas para os dados selecionados. É possível alterar essa lista, adicionar a ela ou excluir estatísticas, dependendo das necessidades.

As seguintes operações são possíveis:

* **[!UICONTROL Count]** para contar todos os valores não nulos do campo a ser agregado, incluindo valores duplicados (do campo agregado),
* **[!UICONTROL Average]** para calcular a média dos valores em um campo numérico,
* **[!UICONTROL Minimum]** para calcular o mínimo dos valores em um campo numérico,
* **[!UICONTROL Maximum]** para calcular o máximo de valores em um campo numérico.
* **[!UICONTROL Sum]** para calcular a soma dos valores em um campo numérico,
* **[!UICONTROL Standard deviation]** para calcular como os valores retornados são distribuídos em torno da média.
* **[!UICONTROL Number of missing values]** para calcular o número de campos numéricos sem valores definidos.
* **[!UICONTROL Decile distribution]** para distribuir os valores retornados de forma que cada um represente 1/10 dos valores em um campo numérico.
* **[!UICONTROL Custom distribution]** para distribuir os valores retornados com base em limites definidos pelo usuário.

   The **[!UICONTROL Detail...]** button lets you edit a statistic and, if needed, personalize its calculation or its display:

   ![](assets/s_ncs_user_report_wizard_030.png)

   A última etapa do assistente mostra o relatório de análise quantitativa.

   ![](assets/reporting_descriptive_view_report.png)

   Para fazer alterações no relatório, consulte [Processamento de um relatório](../../reporting/using/processing-a-report.md).

