---
title: Criação de uma tabela
seo-title: Criação de uma tabela
description: Criação de uma tabela
seo-description: null
page-status-flag: never-activated
uuid: c5bca799-a5d6-4d98-8fc5-25d7f71be5f7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 74084618-2b35-42c5-8a86-87ce137abb71
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Criação de uma tabela{#creating-a-table}

É possível adicionar uma tabela a um relatório para exibir dados. Pode ser uma tabela dinâmica criada com base em medições de cubo, uma lista com grupo ou uma tabela contendo uma análise de valores.

![](assets/s_advuser_report_page_activity_05.png)

## Criação de uma lista com grupo {#creating-a-list-with-group}

A **[!UICONTROL List with group]** type table lets you group data in the table and produce statistics on it. Por exemplo, é possível criar totais e subtotais para os dados. Cada grupo tem sua própria linha de cabeçalho, detalhe e rodapé.

>[!CAUTION]
>
>The **[!UICONTROL Page]** activity containing the table must be preceded by a **[!UICONTROL Query]** or **[!UICONTROL Script]** activity to collect the data to be analyzed in the report. Para obter mais informações sobre essas atividades, consulte [Coleta de dados para analisar](../../reporting/using/collecting-data-to-analyze.md) e analisar a atividade [de](../../reporting/using/advanced-functionalities.md#script-activity)Script.

### Princípio operacional {#operating-principle}

Talvez seja necessário analisar várias categorias de dados de uma vez. Uma lista com grupo permite combinar dados e criar estatísticas em vários grupos de dados dentro da mesma tabela. Para fazer isso, é possível criar um grupo na tabela.

No exemplo a seguir, o grupo mostra todas as campanhas no banco de dados, os deliveries e o número de mensagens enviadas por delivery e por campanha.

It lets you list the campaigns (**[!UICONTROL Label (Campaign)]**, the list of deliveries (**[!UICONTROL Label]** ) linked to the campaign, and lets you count the number of messages sent per delivery (**[!UICONTROL Processed)]**, before adding them up for each campaign (**[!UICONTROL Sum(@processed)]** ).

![](assets/s_advuser_ergo_listgroup_005.png)

### Etapas de implementação {#implementation-steps}

Um exemplo completo de implementação é fornecido aqui: Caso de [uso: Crie um relatório com uma lista](#use-case--create-a-report-with-a-group-list)de grupos.

Observe as seguintes etapas para criar uma tabela do tipo &quot;Lista com grupo&quot;:

1. Go to the report chart and place a **[!UICONTROL Query]** activity. Consulte [Coleta de dados para analisar](../../reporting/using/collecting-data-to-analyze.md).
1. Preencha a tabela de origem e selecione os campos da tabela que as estatísticas abordarão.
1. Place a **[!UICONTROL Page]** activity in the chart. Para obter mais informações, consulte [Elementos estáticos](../../reporting/using/creating-a-new-report.md#static-elements).
1. Insira uma tabela de **[!UICONTROL List with group]** tipos na página.
1. Especifique o caminho de dados ou a tabela selecionada como uma fonte de dados na query.

   Essa etapa é obrigatória se desejar recuperar os campos na tabela de origem posteriormente e inseri-los nas células da tabela.

1. Criação da tabela e seu conteúdo
1. Display the finalized report in the **[!UICONTROL Preview]** tab. É possível então publicar o relatório e exportá-lo em um formato diferente se necessário. Para obter mais informações, consulte [Exportação de um relatório](../../reporting/using/actions-on-reports.md#exporting-a-report).

### Adição de linhas e colunas {#adding-lines-and-columns}

By default, a **[!UICONTROL List with group]** type table includes a header, a detail line, and a footer line.

O próprio grupo inclui linhas de cabeçalho, detalhe e rodapé.

* **Linha de cabeçalho**: esta linha permite fornecer um título para as colunas da tabela.

   ![](assets/s_advuser_ergo_listgroup_003a.png)

* **Linha de detalhe**: esta linha contém valores de estatística.

   ![](assets/s_advuser_ergo_listgroup_004.png)

* **Linha de rodapé**: esta linha permite exibir os valores totais.

   ![](assets/s_advuser_ergo_listgroup_003.png)

Linhas e colunas podem ser adicionadas para satisfazer qualquer necessidade.

O grupo pode ser colocado em qualquer linha da tabela e inclui sua própria linha de cabeçalho, detalhe e rodapé.

![](assets/s_advuser_ergo_listgroup_019.png)

**Linha e coluna**: para adicionar ou excluir uma linha ou coluna, vá para uma linha ou coluna existente e use o menu do botão direito do mouse.

![](assets/s_advuser_ergo_listgroup_006.png)

A natureza da linha que adicionar depende do local do cursor. For example, to add a header line, place your cursors on a header, then click **[!UICONTROL Add > A line above/below]**.

![](assets/s_advuser_ergo_listgroup_006a.png)

The width of the columns can be modified via the **[!UICONTROL Column format]** item.

**Grupo**: para adicionar um grupo, vá para uma linha e selecione o item correspondente no menu suspenso.

![](assets/s_advuser_ergo_listgroup_007.png)

### Definição do conteúdo da célula {#defining-cell-content}

Para editar uma célula da tabela e definir seu conteúdo e formato, vá para a célula e use o menu do botão direito do mouse.

Use the **[!UICONTROL Expression]** menu entry to select the values to display.

![](assets/s_advuser_ergo_listgroup_010.png)

* Para inserir os valores a serem analisados diretamente na tabela, selecione-os entre os campos disponíveis.

   A lista de campos disponíveis coincide com o conteúdo da query antes da tabela no gráfico de criação de relatório.

   ![](assets/s_advuser_ergo_listgroup_011.png)

* Insira um rótulo para uma célula, o cabeçalho um, por exemplo.

   Para fazer isso, use o mesmo processo de inserção de um campo no banco de dados, mas não selecione uma expressão. Enter the label in the **[!UICONTROL Label]** field. Ele será exibido como está.

* Cálculo de uma agregação (uma média, uma soma, etc.) e sua exibição na célula

   To do this, use the **[!UICONTROL Aggregates]** menu entry and select the desired campaign.

   ![](assets/s_advuser_ergo_listgroup_008.png)

### Definição do formato de célula {#defining-cell-format}

![](assets/s_advuser_ergo_listgroup_017.png)

To define the cell format, the **[!UICONTROL Cell format...]** menu lets you access all formatting options available for the selected cell.

Essas opções permitem personalizar a renderização final do relatório e facilitar a leitura das informações.

Use the **[!UICONTROL Carriage return]** field when exporting data to Excel: select the **[!UICONTROL Yes]** value to force the carriage return. Esse valor será mantido ao exportar. Para obter mais informações, consulte [Exportação de um relatório](../../reporting/using/actions-on-reports.md#exporting-a-report).

The **[!UICONTROL Cell format]** window lets you access the following tab:

* A **[!UICONTROL Value]** guia
* A **[!UICONTROL Borders]** guia
* A **[!UICONTROL Click]** guia
* A **[!UICONTROL Extra]** guia

The **[!UICONTROL Value]** tab lets you change the font and the various value attributes or to define a format based on their nature.

![](assets/s_advuser_ergo_listgroup_009.png)

The format changes data display: for example, the **[!UICONTROL Number]**, **[!UICONTROL Monetary]** and **[!UICONTROL Percentage]** formats allow you to align the figures on the right and display decimal points.

Exemplo de como configurar um formato de moeda: é possível especificar a moeda em que os valores são expressos, escolher separar milhares e mostrar valores negativos em vermelho. A posição do símbolo de moeda depende do idioma do operador definido em seu perfil.

![](assets/s_advuser_ergo_listgroup_012.png)

Exemplo de configuração para datas: é possível escolher se deseja ou não exibir o tempo.

![](assets/s_advuser_ergo_listgroup_013.png)

A guia **Bordas** permite adicionar bordas às linhas e colunas na tabela. A adição de bordas às células pode levar a problemas de desempenho ao exportar relatórios grandes para o Excel.

![](assets/s_advuser_ergo_listgroup_014.png)

If necessary, you can define borders in the table template (**[!UICONTROL Administration > Configuration > Form rendering]** ).

Nesse caso, haverá a seguinte sintaxe:

Na guia Web:

```
 .tabular td {
 border: solid 1px #000000;
 }
```

Na guia Excel:

```
 <style name="odd" fillColor="#fdfdfd">
  <border>
   <borderTop value="solid 0.05pt #000000" />
   <borderBottom value="solid 0.05pt #000000" />
   <borderLeft value="solid 0.05pt #000000" />
   <borderRight value="solid 0.05pt #000000" />
  </border>
 </style> 
 
 <style name="even" fillColor="#f7f8fa">
  <border>
   <borderTop value="solid 0.05pt #000000" />
   <borderBottom value="solid 0.05pt #000000" />
   <borderLeft value="solid 0.05pt #000000" />
   <borderRight value="solid 0.05pt #000000" />
  </border>
 </style> 
```

The **[!UICONTROL Click]** tab lets you define an action when the user clicks the content of a cell or of the table.

No exemplo abaixo, clicar no valor na célula permite exibir a segunda página do relatório: ela conterá informações sobre o delivery na célula.

![](assets/s_advuser_ergo_listgroup_015.png)

A guia **Extra** permite vincular um visual a seus dados, como uma marca colorida ou uma barra de valores. A marca colorida é usada quando a tabela é mostrada como uma legenda em um gráfico. Para obter mais informações, consulte o exemplo de implementação: [Etapa 5 - Criar a segunda página](#step-5---create-the-second-page)

![](assets/s_advuser_ergo_listgroup_016.png)

## Use case: Create a report with a group list {#use-case--create-a-report-with-a-group-list}

Neste exemplo, vamos criar um relatório de duas páginas: a primeira página conterá a lista e os deliveries totais por campanha, bem como o número de mensagens enviadas. Os nomes dos deliveries serão links clicáveis e permitirão ir para a segunda página do relatório para exibir a análise dos deliveries por domínio de email para o delivery selecionado com uma tabela e um gráfico. Na segunda página, a tabela servirá como uma legenda para o gráfico.

![](assets/reporting_quick_start_report-final.png)

### Etapa 1 - Criar um relatório {#step-1---create-a-report}

Create a new report that concerns the campaign schema, **[!UICONTROL Campaigns (nms)]**.

![](assets/s_advuser_report_listgroup_001.png)

Clique em **[!UICONTROL Save]** para criar o relatório.

Vá para o gráfico e adicione os primeiros componentes a serem usados para criar o conteúdo do relatório: uma primeira query e uma primeira página.

![](assets/reporting_quick_start_diagram.png)

### Etapa 2 – Criar a primeira query {#step-2---create-the-first-query}

A primeira query permite coletar os deliveries vinculados a cada campanha. O objetivo é exibir um relatório sobre os vários deliveries do banco de dados do Adobe Campaign vinculados a cada campanha.

Clique duas vezes na primeira query para editá-la e siga as etapas abaixo para configurá-la:

1. Start by changing the schema on which the query&#39;s source is applied: select the **[!UICONTROL Deliveries (nms)]** schema.
1. Click the **[!UICONTROL Edit query]** link and display the advanced fields.

   ![](assets/reporting_quick_start_query-1.png)

1. Selecione os seguintes campos:

   * o rótulo do delivery,
   * a chave primária do delivery,
   * o rótulo da campanha,
   * o indicador dos deliveries processados,
   * a chave externa do link Campaign,
   * o indicador de taxa de erro.
   ![](assets/s_advuser_report_listgroup_002.png)

   Vincular um alias a cada campo: é recomendável para facilitar a seleção de dados da tabela que será adicionada à primeira página do relatório.

   Neste exemplo, usaremos os seguintes aliases:

   * Rótulo: **@label**
   * Chave primária: **@deliveryId**
   * Rótulo (Campanha): **@label1**
   * Processado: **@processado**
   * Foreign key of the &#39;Campaign&#39; (&#39;id&#39; field) link: **@operationId**
   * Taxa de erro: **@errorRatio**


1. Clique duas vezes no **[!UICONTROL Next]** botão para chegar à **[!UICONTROL Data filtering]** etapa.

   Adicione uma condição de filtragem para coletar apenas os deliveries vinculados a uma campanha.

   A sintaxe desse filtro é a seguinte: &quot;Chave estrangeira do link &#39;Campanhas&#39; maior que 0&quot;.

   ![](assets/reporting_quick_start_query_filter.png)

1. Click **[!UICONTROL Finish]** to save these conditions, then click **[!UICONTROL Ok]** to close the query editor.

### Step 3: Create the first page {#step-3--create-the-first-page}

Nesta etapa, vamos configurar a primeira página do relatório. Para fazer isso, siga as etapas abaixo:

1. Open the **[!UICONTROL Page]** activity and enter its title, for instance **Deliveries** in this case.

   ![](assets/s_advuser_report_listgroup_003.png)

1. Insira uma lista com um grupo na barra de ferramentas e insira seu rótulo, por exemplo: Lista de entregas por campanha.

   ![](assets/s_advuser_report_listgroup_004.png)

1. Click the **[!UICONTROL Table data XPath...]** link and select the delivery link, i.e. `[query/delivery]`.

   ![](assets/s_advuser_report_listgroup_005.png)

1. Click the **[!UICONTROL Data]** tab and change layout of the table: add three columns on the right.

   ![](assets/s_advuser_report_listgroup_006.png)

1. Adicione um grupo.

   ![](assets/s_advuser_report_listgroup_008.png)

   Este grupo permitirá agrupar campanhas e os deliveries vinculadas a elas.

1. Na janela do grupo, faça referência à **chave externa do link &quot;Campaign&quot;** e feche a janela.

   ![](assets/s_advuser_report_listgroup_007.png)

1. Edit the first cell of the group header and insert the **[!UICONTROL Label]** field of the campaigns as an expression.

   ![](assets/s_advuser_report_listgroup_009.png)

1. Edit the second cell of the details line and select the deliveries **[!UICONTROL Label]**.

   ![](assets/s_advuser_report_listgroup_011.png)

1. Edit the format of this cell and open the **[!UICONTROL Click]** tab. Configure as opções adequadas para que, quando os usuários clicarem no nome de um delivery, ele seja aberto na mesma janela.

   ![](assets/s_advuser_report_listgroup_0111.png)

   Para fazer isso, selecione uma ação de **[!UICONTROL Next page]** tipo e selecione **[!UICONTROL In the same window]** como uma opção aberta.

   ![](assets/s_advuser_report_listgroup_0112.png)

1. Na seção inferior da janela, clique em **[!UICONTROL Add]** e especifique o **`/vars/selectedDelivery`** caminho e a **[!UICONTROL @deliveryId]** expressão que corresponde ao alias da chave primária da entrega, conforme definido na consulta criada anteriormente. Essa fórmula permite acessar o delivery selecionado.

   ![](assets/s_advuser_report_listgroup_010.png)

1. Edit the second cell of the footer line of the group and enter **[!UICONTROL Total per campaign]** as a label.

   ![](assets/s_advuser_report_listgroup_012.png)

1. Edit the third cell of the header line of the group and enter **[!UICONTROL Number of messages sent]** as a label.

   ![](assets/s_advuser_report_listgroup_013.png)

   Essas informações coincidem com o título da coluna.

1. Edite a terceira célula da linha de detalhes e selecione o indicador de mensagem processada como uma expressão.

   ![](assets/s_advuser_report_listgroup_014.png)

1. Edit the third cell of the footer line of the group, select the processed delivery indicator and apply the **[!UICONTROL Sum]** aggregate to it.

   ![](assets/s_advuser_report_listgroup_015.png)

1. Edite a quarta célula da linha de detalhes e selecione **error delivery error rate** como uma expressão.

   ![](assets/s_advuser_report_listgroup_016.png)

1. Selecione essa célula para exibir uma barra de valores que representa a taxa de erro de delivery.

   To do this, access the cell format, then go to the **[!UICONTROL More]** tab. Selecione a **[!UICONTROL Value bar]** entrada na lista suspensa e selecione a **[!UICONTROL Hide the cell value]** opção.

   ![](assets/s_advuser_report_listgroup_023.png)

   Agora é possível exibir uma renderização do relatório. Click the **[!UICONTROL Preview]** tab and select the **[!UICONTROL Global]** option: this shows the list of all deliveries in the Adobe Campaign database that are linked to a campaign.

   ![](assets/s_advuser_report_listgroup_025.png)

   We recommend using the **[!UICONTROL Preview]** tab to make sure the data in your table is properly selected and configured. Assim que isso for feito, é possível formatar a tabela.

1. Apply the **[!UICONTROL Bold]** style to the cells that show the total per campaign and the total number of messages processed.

   ![](assets/s_advuser_report_listgroup_024.png)

1. Click the 1st cell of the group header line, the one that displays the campaign name, and select **[!UICONTROL Edit > Merge to right]**.

   ![](assets/s_advuser_report_listgroup_026.png)

   Mesclar as duas primeiras células da linha de cabeçalho do grupo realinha o título da campanha e a lista de deliveries vinculadas a ela.

   ![](assets/s_advuser_report_listgroup_027.png)

   >[!CAUTION]
   >
   >Recomendamos aguardar até que o relatório seja criado antes de mesclar células já que a mescla é irreversível.

### Etapa 4 – Criação da segunda query {#step-4---create-the-second-query}

Queremos adicionar uma segunda query e uma segunda página para exibir o detalhe de um delivery quando o usuário do relatório clicar nele. Antes de adicionar a query, edite a página criada e habilite a transição de saída para que ela possa ser vinculada à query.

1. Add a new query after the **[!UICONTROL Page]** activity and edit its schema: select the **[!UICONTROL Recipient delivery logs]** schema.

   ![](assets/reporting_quick_start_query-2.png)

1. Edite a query e defina as colunas de saída. Para exibir o número de fornecimentos por domínio de email, é preciso:

   * calcular a soma das chaves primárias para contar o número de logs do delivery:

      ![](assets/reporting_quick_start_query-2_count.png)

   * collect recipient email domains and group information on this field: to do this, select the **[!UICONTROL Group]** option in the domain name column.
   ![](assets/reporting_quick_start_query-2_filter.png)

   Vincule os seguintes aliases aos campos:

   * count(chave primária): **@count**
   * Domínio de email (destinatário): **@domínio**

      ![](assets/reporting_quick_start_query-2_alias.png)


1. Clique duas vezes no **[!UICONTROL Next]** botão: isso leva você ao **[!UICONTROL Data filtering]** passo.

   Adicione uma condição de filtro para coletar apenas as informações vinculadas ao delivery selecionado.

   A sintaxe é a seguinte: Chave estrangeira do link &quot;Entrega&quot; é igual ao valor da configuração `$([vars/selectedDelivery])`

   ![](assets/s_advuser_report_listgroup_017.png)

1. Feche a janela de configuração de query e adicione uma página ao gráfico, logo após a segunda query.

### Etapa 5 – Criação da segunda página {#step-5---create-the-second-page}

1. Edit the page and enter its label: **Email domains**.
1. Uncheck the **[!UICONTROL Enable output transitions]** option: this is the last page of the report and will not be followed by another activity.

   ![](assets/s_advuser_report_listgroup_028.png)

1. Adicione uma nova lista com um grupo usando o menu do botão direito do mouse e rotule de **Email domains per recipient**.
1. Clique no link **[!UICONTROL Table data XPath...]** e selecione o **[!UICONTROL Recipient delivery logs]** link.

   ![](assets/s_advuser_report_listgroup_029.png)

1. In the **[!UICONTROL Data]** tab, adapt the table as follows:

   * Adicione duas colunas ao lado direito.
   * In the first cell of the detail line, add the **[!UICONTROL rowNum()-1]** expression to count the number of lines. Em seguida, altere o formato da célula: na **[!UICONTROL Extra]** guia, selecione **[!UICONTROL Color tab]** e clique em **[!UICONTROL Ok]**.

      ![](assets/s_advuser_report_listgroup_018.png)

      Essa configuração permitirá usar a tabela como legenda do gráfico.

   * In the second cell of the detail line, add the **[!UICONTROL Email domain(Recipient)]** expression.
   * In the third cell of the detail line, add the **[!UICONTROL count(primary key)]** expression.
   ![](assets/s_advuser_report_listgroup_019.png)

1. Adicione um gráfico de pizza à página usando o menu do botão direito e atribua o rótulo **Email domains** a ele. Para obter mais informações, consulte Tipos e variantes de [gráfico](../../reporting/using/creating-a-chart.md#chart-types-and-variants).
1. Clique no **[!UICONTROL Variants]** link e desmarque as opções **[!UICONTROL Display label]** e **[!UICONTROL Display caption]** .
1. Verifique se nenhuma classificação de valor está configurada. Para obter mais informações, consulte [esta seção](../../reporting/using/processing-a-report.md#configuring-the-layout-of-a-descriptive-analysis-report).

   ![](assets/s_advuser_report_listgroup_0191.png)

1. In the **[!UICONTROL Data]** tab, change the data source: select **[!UICONTROL Context data]** from the drop-down list.

   ![](assets/s_advuser_report_listgroup_020.png)

1. Then click **[!UICONTROL Advanced settings]** and select the link to the recipient delivery logs.

   ![](assets/s_advuser_report_listgroup_0201.png)

1. Na **[!UICONTROL Chart type]** seção, selecione a **[!UICONTROL Email domain]** variável.
1. Em seguida, adicione o cálculo a ser executado: selecione a soma como um operador.

   ![](assets/s_advuser_report_listgroup_0202.png)

1. Click the **[!UICONTROL Detail]** button to select the field which the count will concern, then close the configuration window.

   ![](assets/s_advuser_report_listgroup_030.png)

1. Salve o relatório.

   A página está configurada agora.

### Etapa 6 - Exibição do relatório {#step-6---viewing-the-report}

To view the result of this configuration, click the **[!UICONTROL Preview]** tab and select the **[!UICONTROL Global]** option.

A primeira página do relatório detalha a lista de todos os deliveries incluídos no banco de dados.

![](assets/s_advuser_report_listgroup_021.png)

Se clicar no link de um desses deliveries, ele mostrará o gráfico com a análise dos domínios de email para esse delivery. Agora, essa é a segunda página do relatório e é possível retornar à página anterior clicando no botão apropriado.

![](assets/s_advuser_report_listgroup_022.png)

## Criação de uma análise ou tabela dinâmica {#creating-a-breakdown-or-pivot-table}

Esse tipo de tabela permite exibir estatísticas calculadas dos dados do banco de dados.

A configuração desses tipos de relatórios é semelhante à utilizada para o assistente de análise descritiva. Para obter mais informações, consulte [esta página](../../reporting/using/using-the-descriptive-analysis-wizard.md#configuring-the-quantitative-distribution-template).

Para obter mais informações sobre criação de uma tabela dinâmica, consulte [esta seção](../../reporting/using/using-cubes-to-explore-data.md).
