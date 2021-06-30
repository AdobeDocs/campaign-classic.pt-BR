---
product: campaign
title: Criação de um gráfico
description: Criação de um gráfico
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: d32b614f-82c1-4363-816c-4ebedaa5cfe9
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: ht
source-wordcount: '730'
ht-degree: 100%

---

# Criação de um gráfico{#creating-a-chart}

Os dados no banco de dados também podem ser coletados e exibidos em um gráfico. O Adobe Campaign fornece um conjunto de representações gráficas. Sua configuração é detalhada abaixo.

Os gráficos são inseridos diretamente em uma página de relatório por meio do menu do botão direito do mouse ou da barra de ferramentas.

## Etapas de criação {#creation-steps}

Para criar um gráfico em um relatório, siga as etapas abaixo:

1. Edite a página onde deseja exibir o gráfico e selecione o tipo de gráfico na barra de ferramentas.

   ![](assets/s_advuser_report_page_activity_04.png)

1. Insira um nome e legenda. Se necessário, é possível alterar a posição da legenda usando a lista suspensa.

   ![](assets/s_ncs_advuser_report_wizard_018.png)

1. Clique na guia **[!UICONTROL Data]** para definir a fonte de dados e a série a ser calculada.

   A estatística a ser exibida no gráfico pode ser calculada com base em um query ou nos dados de contexto, ou seja, os dados fornecidos pela transição de entrada da página atual (para obter mais informações, consulte [Usar dados de contexto](../../reporting/using/using-the-context.md#using-context-data)).

   * Clique no link **[!UICONTROL Filter data...]** para definir os critérios de filtragem para os dados no banco de dados.

      ![](assets/reporting_graph_add_filter.png)

   * Para usar dados contextuais, selecione essa opção e clique no link **[!UICONTROL Advanced settings...]**. Selecione os dados que a estatística abordará.

      ![](assets/reporting_graph_from_context.png)

      É possível acessar os dados contextuais para definir os valores a serem exibidos no gráfico:

      ![](assets/reporting_graph_select-from_context.png)

## Tipos e variantes de gráfico {#chart-types-and-variants}

O Adobe Campaign oferece vários tipos de representações gráficas. Elas estão detalhadas abaixo.

O tipo de gráfico é selecionado quando inserido na página.

![](assets/s_advuser_report_page_activity_04.png)

Ele também pode ser alterado por meio da seção **[!UICONTROL Chart type]** da guia no gráfico **[!UICONTROL General]**.

![](assets/reporting_change_graph_type.png)

As variantes dependem do tipo de gráfico selecionado. Elas são selecionadas por meio do link **[!UICONTROL Variants...]**.

### Análise: gráficos de pizza {#breakdown--pie-charts}

Esse tipo de representação gráfica permite exibir uma visão geral dos elementos medidos.

Os gráficos de pizza permitem analisar uma variável somente.

![](assets/reporting_graph_type_sector_1.png)

O link **[!UICONTROL Variants]** permite personalizar a renderização geral do gráfico.

![](assets/reporting_graph_type_sector_2.png)

Os gráficos de pizza permitem inserir o valor do raio interno no campo apropriado.

Por exemplo:

0,00 traça um círculo completo.

![](assets/s_ncs_advuser_report_sector_exple1.png)

0.40 traça um círculo com um raio de 40%.

![](assets/s_ncs_advuser_report_sector_exple2.png)

1,00 traça somente o exterior do círculo.

![](assets/s_ncs_advuser_report_sector_exple3.png)

### Evolução: curvas e áreas {#evolution--curves-and-areas}

Esse tipo de representação gráfica permite entender a evolução de uma ou mais medidas no tempo.

![](assets/reporting_graph_type_curve.png)

### Comparação: histogramas {#comparison--histograms}

Os histogramas permitem comprar os valores de uma ou mais variáveis.

Para esses tipos de gráficos, as seguintes opções são oferecidas na janela **[!UICONTROL Variants]**:

![](assets/reporting_select_graph_var.png)

Marque a opção **[!UICONTROL Display caption]** para exibir a legenda com o gráfico e escolha sua posição:

![](assets/reporting_select_graph_legend.png)

Quando apropriado, é possível empilhar valores juntos.

![](assets/reporting_graph_type_histo.png)

Se necessário, é possível inverter a sequência de exibição do valor. Para fazer isso, selecione a opção **[!UICONTROL Reverse stacking]**.

### Conversão: funil {#conversion--funnel}

Esse tipo de gráfico permite rastrear a taxa de conversa de elementos medidos.

### Progresso: medidor {#progress--gauge}

Esse tipo de gráfico permite exibir o progresso de um valor em comparação com um objetivo definido. No exemplo abaixo, o mostrador preto mostra o número de deliveries enviados com êxito (76) de um objetivo de 100 deliveries. O medidor divide-se em três intervalos que correspondem a status específicos.

![](assets/reporting_graph_type_gauge.png)

Esses elementos são definidos ao configurar o gráfico.

![](assets/reporting_graph_type_gauge1.png)

* O campo **[!UICONTROL Value]** é representado por um mostrador preto no gráfico. Ele representa o elemento cujo progresso deseja calcular. O valor a ser representado deve já ter sido salvo para ser usado.
* O campo **[!UICONTROL Goal]** representa o valor máximo a ser alcançado.
* Usando o campo **[!UICONTROL Other mark]**, é possível adicionar um segundo indicador ao gráfico.
* Os campos **[!UICONTROL Display range]** permitem especificar os valores entre os quais o relatório é calculado.
* O campo **[!UICONTROL Value ranges]** permite atribuir status (None, Bad, Acceptable, Good) a um conjunto de valores para ilustrar melhor o progresso.

Na seção **[!UICONTROL Display settings]**, o **[!UICONTROL Change appearance...]** permite configurar o modo como o gráfico é exibido.

![](assets/reporting_graph_type_gauge2.png)

A opção **[!UICONTROL Display the value below the gauge]** permite exibir o progresso do valor abaixo do gráfico.

O campo **[!UICONTROL Aperture ratio]**, que deve estar entre 0 e 1, permite editar a abertura do relatório em um círculo mais ou menos completo. No exemplo acima, o valor 0,50 corresponde a um semicírculo.

O campo **[!UICONTROL Width]** permite editar o tamanho do gráfico.

## Interação com o gráfico {#interaction-with-the-chart}

É possível definir uma ação quando o usuário clica no gráfico. Abra a janela **[!UICONTROL Interaction events]** e selecione a ação que deseja realizar.

Possíveis tipos de interação e suas configurações são detalhadas [nesta seção](../../web/using/static-elements-in-a-web-form.md#inserting-html-content).

![](assets/s_ncs_advuser_report_wizard_017.png)

## Cálculo estatístico {#calculating-statistics}

Os gráficos permitem exibir estatísticas nos dados coletados.

Essas estatísticas são definidas na seção **[!UICONTROL Series parameters]** da guia **[!UICONTROL Data]**.

Para criar uma nova estatística, clique no ícone **[!UICONTROL Add]** e configure a janela apropriada. Os tipos de cálculo disponíveis são detalhados abaixo.

![](assets/reporting_add_statistics.png)

Para obter mais informações, consulte [esta seção](../../reporting/using/using-the-descriptive-analysis-wizard.md#statistics-calculation).
