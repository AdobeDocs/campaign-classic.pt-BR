---
product: campaign
title: Crie seu primeiro relatório de análise descritiva
description: Saiba como usar o assistente para criar o seu primeiro relatório de análise descritiva
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Reporting, Monitoring
exl-id: 848d67c7-d1dc-4eba-bcb8-672e76d8ce87
source-git-commit: 5e062f9dbdf6c148e442ac10dbb12cf72ba0179b
workflow-type: ht
source-wordcount: '1580'
ht-degree: 100%

---

# Crie seu primeiro relatório de análise descritiva {#using-the-descriptive-analysis-wizard}

Para criar um relatório de análise descritiva, use o assistente dedicado. A configuração depende dos dados a serem analisados e da renderização desejada.

## Analisar dados no banco de dados {#analyzing-data-in-the-database}

O assistente de análise descritiva pode ser iniciado por meio do menu **[!UICONTROL Tools > Descriptive analysis]**: nesse caso, a análise engloba os destinatários por padrão (**nms:recipient**). Aplica-se a todos os dados do banco de dados do Adobe Campaign.

![](assets/reporting_descriptive_wz_launch.png)

Para analisar uma tabela diferente da dos destinatários padrão (**nms:recipient**), clique no link **[!UICONTROL Advanced settings...]**, na última etapa do assistente, e selecione a tabela que corresponde às suas configurações; neste caso **cus:individual**:

![](assets/reporting_descriptive_other_schema.png)

Se quiser produzir estatísticas sobre parte dos dados, é possível definir um filtro. Para fazer isso, clique no link **[!UICONTROL Advanced settings...]** e defina o filtro a ser aplicado, conforme mostrado abaixo:

![](assets/reporting_descriptive_wz_filter.png)

A análise só abordará os destinatários do banco de dados com 16 anos de idade ou mais e que moram em Londres.

## Analisar um conjunto de dados {#analyzing-a-set-of-data}

É possível usar o assistente de análise descritiva por meio de um contexto diferente: uma lista, uma transição de fluxo de trabalho, uma ou mais entregas, uma seleção de destinatários etc.

Ele pode ser acessado por vários nós da árvore do Adobe Campaign que apontam para a tabela de destinatários.

Abra o assistente de análise descritiva, selecionando os itens e clicando com o botão direito. Somente os dados selecionados serão analisados.

![](assets/reporting_descriptive_from_recipients.png)

* Para um conjunto de **destinatários**, selecione os destinatários que serão analisados, clique com o botão direito do mouse e selecione **[!UICONTROL Actions > Explore...]**, conforme mostrado acima. Se um filtro for aplicado à lista de destinatários, somente seu conteúdo será analisado.

  Para selecionar todos os destinatários na pasta ou no filtro atual, use o atalho CTRL+A. Isso significa selecionar até mesmo os destinatários não mostrados.

  Para obter um exemplo da análise descritiva dos destinatários, consulte [Análise qualitativa de dados](../../reporting/using/use-cases.md#qualitative-data-analysis).

* No contexto de um **workflow**, coloque o cursor em uma transição que aponta para a tabela de destinatários, clique com o botão direito do mouse e selecione **[!UICONTROL Analyze target]**. Para obter mais informações, consulte o exemplo em [Analisar um público alvo de transição em um fluxo de trabalho](../../reporting/using/use-cases.md#analyzing-a-transition-target-in-a-workflow).
* Para **listas**, selecione uma ou mais listas e aplique o mesmo processo dos destinatários.
* No contexto de uma **entrega**, selecione as entregas cujo público alvo deseja analisar, clique com o botão direito do mouse e selecione **[!UICONTROL Actions > Explore the target]**, conforme mostrado abaixo:

  ![](assets/reporting_descriptive_from_deliveries.png)

  Exemplos de análises descritivas para entregas são fornecidos aqui: [Analisar uma população](../../reporting/using/use-cases.md#analyzing-a-population), e aqui: [Analisar registros de rastreamento de destinatários](../../reporting/using/use-cases.md#analyzing-recipient-tracking-logs).

## Configurar o modelo de distribuição qualitativa {#configuring-the-qualitative-distribution-template}

O modelo **[!UICONTROL Qualitative distribution]** permite criar estatísticas em todos os tipos de dados (por exemplo: nome da empresa, domínio de email).

As opções de configuração disponíveis para um relatório criado por meio do modelo **[!UICONTROL Qualitative distribution]** são detalhadas em [Exibir dados na tabela](#displaying-data-in-the-table). Um exemplo completo é detalhado em [Analisar uma população](../../reporting/using/use-cases.md#analyzing-a-population).

Ao utilizar o assistente de análise descritiva para analisar os seus dados, as opções disponíveis dependem das configurações escolhidas. Veja os detalhes abaixo.

### Compartimentalização de dados {#data-binning}

Quando selecionar as variáveis a serem exibidas, é possível definir compartimentalização de dados, em outras palavras, configurar critérios de agrupamento para os dados selecionados.

![](assets/s_ncs_user_report_wizard_031.png)

>[!NOTE]
>
>Quando o campo relacionado ao cálculo é calculado usando uma agregação, marque **[!UICONTROL The data is already aggregated]** para melhorar o desempenho.

As opções serão diferentes dependendo do conteúdo do campo:

* **[!UICONTROL None]**: essa opção permite exibir todos os valores disponíveis para a variável, sem compartimentalização.

  >[!CAUTION]
  >
  >Essa opção deve ser usada com cuidado: pode ter um grande impacto no relatório e no desempenho da máquina.

* **[!UICONTROL Auto]**: essa opção permite exibir os valores n mais frequentemente representados. Eles são calculados automaticamente e cada um representa uma porcentagem das variáveis comparadas ao número de agrupamentos. Para valores numéricos, o Adobe Campaign gera automaticamente n classes para classificar os dados.
* **[!UICONTROL Manual]**: essa opção funciona como a opção **[!UICONTROL Auto]**, exceto que é possível definir esses valores manualmente. Para fazer isso, clique no botão **[!UICONTROL Add]** à direita da tabela de valores.

  Os valores podem ser inicializados automaticamente pelo Adobe Campaign antes da personalização: para fazer isso, insira o número de agrupamentos que deseja gerar e clique no link **[!UICONTROL Initialize with]**, conforme mostrado abaixo:

  ![](assets/reporting_descriptive_initialize.png)

  Em seguida, adapte o conteúdo às necessidades:

  ![](assets/reporting_descriptive_initialize_perso.png)

  Dependendo do nível de precisão desejado, os campos contendo datas podem ser agrupados por tempo, dia, mês, ano, etc.

  ![](assets/reporting_descriptive_group_by_year.png)

* **[!UICONTROL Modulo]**: permite criar grupos de valores no caso de valores numéricos. Por exemplo, um módulo com um valor de 10 permite criar um intervalo de valores que variam de dez em dez.

  ![](assets/reporting_descriptive_initialize_modulo.png)

  Esse exemplo permite visualizar o detalhamento dos destinatários por faixa etária.

  ![](assets/reporting_descriptive_initialize_modulo_result.png)

### Exibir dados na tabela {#displaying-data-in-the-table}

Use a barra de ferramentas para personalizar a exibição das variáveis na tabela: exclua uma coluna, exiba dados em linhas em vez de colunas, mova uma coluna para a esquerda ou direita, exiba ou altere o cálculo de valores.

![](assets/s_ncs_user_report_wizard_toolbar.png)

A seção superior da janela permite selecionar as configurações de exibição.

É possível exibir ou ocultar o nome das estatísticas e subtotais e escolher a orientação das estatísticas. Para obter mais informações, consulte [Configurações da exibição de relatório de análise](../../reporting/using/processing-a-report.md#analysis-report-display-settings).

### Exibir dados no gráfico {#displaying-data-in-the-chart}

Na primeira etapa do assistente de análise descritiva, é possível optar por exibir os dados somente na forma de gráficos, sem tabelas. Nesse caso, a seleção variável deve ser feita ao configurar o gráfico. Primeiro, é necessário selecionar o número de variáveis a serem exibidas e selecionar os campos do banco de dados relevante.

![](assets/s_ncs_user_report_wizard_023.png)

Em seguida, selecione o tipo de gráfico desejado.

![](assets/s_ncs_user_report_wizard_024.png)

>[!NOTE]
>
>É possível exibir as variáveis em um gráfico e uma tabela ao mesmo tempo. Para fazer isso, insira as variáveis na janela **[!UICONTROL Table configuration]**. Clique em **[!UICONTROL Next]** e selecione o tipo de gráfico na janela de configuração do gráfico. Se subdimensões forem definidas na tabela, elas não serão exibidas no gráfico.

Clique no link **[!UICONTROL Variants]** para modificar as propriedades do gráfico.

![](assets/reporting_descriptive_graphe_options.png)

As opções oferecidas dependem do tipo de gráfico selecionado. Para obter mais informações, consulte [esta página](../../reporting/using/creating-a-chart.md#chart-types-and-variants).

### Cálculo de estatísticas {#statistics-calculation}

O assistente de análise descritiva permite calcular vários tipos de estatística em relação aos dados. Por padrão, somente uma contagem simples é configurada.

Clique em **[!UICONTROL Add]** para criar uma nova estatística.

![](assets/reporting_descriptive_create_stat.png)

As seguintes operações são possíveis:

* **[!UICONTROL Count]** para contar todos os valores não nulos do campo a ser agregado, incluindo valores duplicados (do campo de agregação),
* **[!UICONTROL Average]** para calcular a média dos valores em um campo numérico,
* **[!UICONTROL Minimum]** para calcular o mínimo dos valores em um campo numérico,
* **[!UICONTROL Maximum]** para calcular o máximo dos valores em um campo numérico,
* **[!UICONTROL Sum]** para calcular a soma dos valores em um campo numérico,
* **[!UICONTROL Standard deviation]** para calcular como os valores retornados estão distribuídos em relação à média,
* **[!UICONTROL Row percentage distribution]** para calcular a proporção do valor em uma coluna e o valor em uma linha (disponível somente para tabelas),
* **[!UICONTROL Column percentage distribution]** para calcular a proporção do valor em uma linha para o valor em uma coluna (disponível somente para tabelas),
* **[!UICONTROL Total percentage distribution]** para calcular a distribuição de destinatários relacionados aos valores,

  ![](assets/s_ncs_user_report_wizard_026.png)

* **[!UICONTROL Calculated field]** para criar um operador personalizado (disponível somente para tabelas). O campo **[!UICONTROL User function]** permite inserir o cálculo a ser aplicado aos dados.

  Exemplo: cálculo do valor médio de compra por cliente com base no país e na origem

  ![](assets/report_compute_data_sample1.png)

  Para exibir as informações acima em uma tabela, é preciso criar um campo calculado para armazenar o valor médio de compra por cliente.

  Para fazer isso:

   1. Calcule o total de compras.

      ![](assets/report_compute_data_sample2.png)

   1. Esta estatística não será exibida na tabela. É necessário desmarcar a opção **[!UICONTROL Display in the table]** da guia **[!UICONTROL Advanced]**.

      ![](assets/report_compute_data_sample3.png)

   1. Crie uma nova estatística do tipo **[!UICONTROL Calculated field]** e insira a seguinte fórmula no campo **[!UICONTROL User function]**: **@purchases/@count**.

      ![](assets/report_compute_data_sample4.png)

### Exibir o relatório {#displaying-the-report}

A última etapa do assistente permite exibir o relatório, ou seja, a tabela ou o gráfico conforme foram configurados.

Quando o relatório contém uma tabela, a célula do resultado do cálculo é colorida. Quanto maior o resultado, mais intensa será a cor.

![](assets/report_compute_data_sample1.png)

É possível alterar o layout dos resultados. Para fazer isso, clique com o botão direito do mouse na variável correspondente e selecione a entrada do menu de atalho.

![](assets/s_ncs_user_report_wizard_029.png)

Quando o relatório inclui um gráfico, os rótulos da legenda permitem filtrar as informações exibidas: clique em um rótulo para habilitar/desabilitar exibição no gráfico.

![](assets/report_display_data_in_graph.png)

## Configurar o modelo de distribuição quantitativa {#configuring-the-quantitative-distribution-template}

Para gerar uma análise descritiva por conta própria, selecione a opção **New descriptive analysis from a template** se não estiver definida por padrão.

O template **[!UICONTROL Quantitative distribution]** que permite gerar estatísticas em dados que podem ser medidos ou contados (por exemplo, valor da fatura, idade dos destinatários).

O modo de configuração de um relatório de análise criado por meio do template **[!UICONTROL Quantitative distribution]** é detalhado em um exemplo de implementação [Quantitative data analysis](../../reporting/using/use-cases.md#quantitative-data-analysis).

As opções disponíveis ao utilizar o assistente de análise descritiva para criar um relatório quantitativo serão detalhadas abaixo.

Comece selecionando a variável que os cálculos abordarão:

![](assets/s_ncs_user_report_wizard_017.png)

Por padrão, o Adobe Campaign oferece uma série de estatísticas a serem calculadas para os dados selecionados. É possível alterar essa lista, adicionar a ela ou excluir estatísticas, dependendo das necessidades.

As seguintes operações são possíveis:

* **[!UICONTROL Count]** para contar todos os valores não nulos do campo a ser agregado, incluindo valores duplicados (do campo de agregação),
* **[!UICONTROL Average]** para calcular a média dos valores em um campo numérico,
* **[!UICONTROL Minimum]** para calcular o mínimo dos valores em um campo numérico,
* **[!UICONTROL Maximum]** para calcular o máximo dos valores em um campo numérico.
* **[!UICONTROL Sum]** para calcular a soma dos valores em um campo numérico,
* **[!UICONTROL Standard deviation]** para calcular como os valores do resultado estão distribuídos em relação à média.
* **[!UICONTROL Number of missing values]** para calcular o número de campos numéricos sem valores definidos.
* **[!UICONTROL Decile distribution]** para distribuir os valores do resultado de forma que cada um represente 1/10 dos valores em um campo numérico.
* **[!UICONTROL Custom distribution]** para distribuir os valores do resultado com base em limites definidos pelo usuário.

  O botão **[!UICONTROL Detail...]** permite a edição de uma estatística e, se necessário, a personalização do cálculo ou exibição:

  ![](assets/s_ncs_user_report_wizard_030.png)

  A última etapa do assistente mostra o relatório de análise quantitativa.

  ![](assets/reporting_descriptive_view_report.png)

  Para fazer alterações no relatório, consulte [Processar um relatório](../../reporting/using/processing-a-report.md).
