---
title: Exportação de dados
seo-title: Exportação de dados
description: Exportação de dados
seo-description: null
page-status-flag: never-activated
uuid: 818de79a-587f-4735-b333-4bc702c3b450
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: fecadb66-b81d-4fb6-9971-7bfd024d70b7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0ce6e5277c32bc18c20dca62e5b276f654d1ace5

---


# Exportação de dados{#exporting-data}

## Assistente de exportação {#export-wizard}

Os parâmetros de exportação são registrados por meio de um assistente. O módulo de exportação genérico está disponível como padrão e permite que você acesse e extraia dados do banco de dados: contatos, clientes, listas, segmentos etc. Por exemplo, pode ser útil usar dados de rastreamento de campanha (histórico de rastreamento etc.) em uma planilha. Os dados de saída podem estar em formato txt, CSV, TAB ou XML.

### Etapa 1 - Escolha do template de exportação {#step-1---choosing-the-export-template}

Ao iniciar o assistente de exportação, primeiro é necessário selecionar um template. Como exemplo, para configurar a exportação de destinatários que se registraram recentemente, siga as etapas abaixo:

1. Selecione a **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]** pasta.
1. Clique em **New** e em **Export** para criar o template de exportação.

   ![](assets/s_ncs_user_export_wizard01.png)

1. Click the arrow to the right of the **[!UICONTROL Export template]** field to select your template, or click **[!UICONTROL Select link]** to browse the tree.

   O modelo nativo é **[!UICONTROL New text export]**. Este template não deve ser modificado, mas você pode duplicá-lo para configurar um novo template. By default, export templates are saved in the **[!UICONTROL Resources > Templates > Job templates]** node.

1. Enter a name for export in the **[!UICONTROL Label]** field. Você pode adicionar uma descrição.
1. Selecione o tipo de exportação. Existem dois tipos possíveis de exportação: **[!UICONTROL Simple export]** para exportar apenas um arquivo e **[!UICONTROL Multiple export]** para exportar vários arquivos em uma única execução, de um ou mais tipos de documento de origem.

### Etapa 2 - Tipo de arquivo a ser exportado {#step-2---type-of-file-to-export}

Selecione o tipo de documento a ser exportado, ou seja, o schema dos dados para exportar.

By default, when the export is launched from the **[!UICONTROL Jobs]** node the data comes from the recipient table. When the export is launched from a list of data (from the **[!UICONTROL right click > Export]** menu), the table to which the data belongs is automatically filled in in the **[!UICONTROL Document type]** field.

![](assets/s_ncs_user_export_wizard02.png)

* Por padrão, a **[!UICONTROL Download the file generated on the server after the export]** opção é selecionada. In the **[!UICONTROL Local file]** field, fill in the name and path of the file to be created, or browse your local disk by clicking the folder to the right of the field. Você pode desmarcar essa opção para inserir o caminho de acesso e o nome do arquivo de saída do servidor.

   >[!NOTE]
   >
   >Os trabalhos de importação e exportação automáticos são sempre executados no servidor.
   >
   >To export only some of the data, click **[!UICONTROL Advanced parameters]** and enter the number of lines to be exported in the appropriate field.

* É possível criar uma exportação diferencial para exportar apenas registros que foram modificados desde a última execução. Para fazer isso, clique no **[!UICONTROL Advanced parameters]** link, clique na **[!UICONTROL Differential export]** guia e selecione **[!UICONTROL Activate differential export]**.

   ![](assets/s_ncs_user_export_wizard02_b.png)

   Você deve inserir a data da última modificação. Ele pode ser calculado ou recuperado de um campo.

### Etapa 3 - Definição do formato de saída {#step-3---defining-the-output-format}

Selecione um formato de saída para o arquivo de exportação. Os formatos a seguir podem ser usados: texto, texto fixed-column, CSV e XML.

![](assets/s_ncs_user_export_wizard03.png)

* For **[!UICONTROL Text]** format, select the delimiters to separate the columns (tabs, commas, semi-colons, or custom) and the strings (single or double quotes, or none).
* Para **[!UICONTROL text]** e **[!UICONTROL CSV]**, você pode selecionar a opção **[!UICONTROL Use first lines as column titles]**.
* Indique o formato de data e o formato do número. To do this, click the **[!UICONTROL Edit]** button for the field concerned and use the editor.
* Para campos que contêm valores enumerados, você pode selecionar **[!UICONTROL Export labels instead of internal values of enumerations]**. For example, the title can be stored in the form **1=Mr.**, **2=Miss**,** 3=Mrs.**. Se essa opção estiver selecionada, **Sr.**, **Srta.**, **Sra.** serão exportados.

### Etapa 4 - Seleção de dados {#step-4---data-selection}

Selecione os campos a serem exportados. Para fazer isso:

1. Double-click the desired fields in the **[!UICONTROL Available fields]** list in order to add them to the **[!UICONTROL Output columns]** section.
1. Use as setas à direita da lista para definir a ordem dos campos no arquivo de saída.

   ![](assets/s_ncs_user_export_wizard04.png)

1. Click the **[!UICONTROL Add]** button to call on functions. Para obter mais informações, consulte a [Lista de funções](../../platform/using/defining-filter-conditions.md#list-of-functions).

### Etapa 5 - Classificação das colunas {#step-5---sorting-columns}

Selecione a ordem de classificação das colunas.

![](assets/s_ncs_user_export_wizard05.png)

### Etapa 6 - Condições de filtro {#step-6---filter-conditions-}

Você pode adicionar condições de filtro para evitar a exportação de todos os dados. A configuração dessa filtragem é a mesma que o direcionamento do destinatário no assistente de delivery. Consulte [esta página](../../delivery/using/steps-defining-the-target-population.md).

![](assets/s_ncs_user_export_wizard05_b.png)

### Passo 7 - Formatação de dados {#step-7---data-formatting}

Você pode modificar a ordem e o rótulo dos campos do arquivo de saída e aplicar transformações aos dados de origem.

* Para alterar a ordem das colunas a serem exportadas, selecione a coluna indicada e use as setas azuis à direita da tabela.
* To change the label of a field, click in the cell of the **[!UICONTROL Label]** column that matches the field to be modified, and enter the new label. Pressione Enter no teclado para confirmar.
* To apply a case transformation to the content of a field, select it from the **[!UICONTROL Transformation]** column. É possível selecionar:

   * Alterar para minúsculas
   * Alterar para maiúsculas
   * Primeira letra em maiúscula
   ![](assets/s_ncs_user_export_wizard06.png)

* Click **[!UICONTROL Add a calculated field]** if you want to create a new calculated field (for example, a column containing last name + first name). For more on this, refer to [Calculated fields](../../platform/using/importing-data.md#calculated-fields).

Se você estiver exportando uma coleção de elementos (por exemplo, assinaturas dos destinatários, as listas às quais elas pertencem etc.), você deverá especificar o número de elementos na coleção que deseja exportar.

![](assets/s_ncs_user_export_wizard06_c.png)

### Etapa 8 - Visualização de dados {#step-8---data-preview}

Clique **[!UICONTROL Start the preview of the data]** para obter uma visualização do resultado da exportação. Por padrão, as 200 primeiras linhas são exibidas. To change this value, click the arrows to the right of the **[!UICONTROL Lines to display]** field.

![](assets/s_ncs_user_export_wizard07.png)

Clique nas guias na parte inferior do assistente para alternar da visualização dos resultados nas colunas para os resultados em XML. Você também pode visualizar as consultas SQL geradas.

### Etapa 9 - Iniciar a exportação {#step-9---launching-the-export}

Clique em **[!UICONTROL Start]** para iniciar a exportação de dados.

![](assets/s_ncs_user_export_wizard08.png)

## Exportação de dados por meio de um workflow {#exporting-data-via-a-workflow}

Os workflows podem ser uma maneira útil de automatizar alguns dos processos de exportação ou exportar conjuntos precisos de dados após usar algumas atividades disponíveis de gestão de dados disponíveis para transformar seus dados.

Para saber mais sobre como exportar dados de workflow, consulte [esta seção](../../workflow/using/how-to-use-workflow-data.md).
