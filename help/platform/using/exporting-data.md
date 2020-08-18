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
source-git-commit: b690e6c7141ba88c8ce72f631ec24fc068ade8f5
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 86%

---


# Exportação de dados{#exporting-data}

## Assistente de exportação {#export-wizard}

Os parâmetros de exportação são registrados por meio de um assistente. O módulo de exportação genérico está disponível como padrão e permite que você acesse e extraia dados do banco de dados: contatos, clientes, listas, segmentos etc. Por exemplo, pode ser útil usar dados de rastreamento de campanha (histórico de rastreamento etc.) em uma planilha. Os dados de saída podem estar em formato txt, CSV, TAB ou XML.

### Etapa 1 - Escolha do template de exportação {#step-1---choosing-the-export-template}

Ao iniciar o assistente de exportação, primeiro é necessário selecionar um template. Como exemplo, para configurar a exportação de destinatários que se registraram recentemente, siga as etapas abaixo:

1. Selecione a **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]** pasta.
1. Clique em **New** e em **Export** para criar o template de exportação.

   ![](assets/s_ncs_user_export_wizard01.png)

1. Clique na seta à direita do campo **[!UICONTROL Export template]** para selecionar o modelo ou clique em **[!UICONTROL Select link]** para navegar na árvore.

   The native template is **[!UICONTROL New text export]**. Este template não deve ser modificado, mas você pode duplicá-lo para configurar um novo template. By default, export templates are saved in the **[!UICONTROL Resources > Templates > Job templates]** node.

1. Insira um nome para a exportação no campo **[!UICONTROL Label]**. Você pode adicionar uma descrição.
1. Selecione o tipo de exportação. There are two possible types of export: **[!UICONTROL Simple export]** to export only one file, and **[!UICONTROL Multiple export]** to export several files in a single execution, from one or more types of source document.

### Etapa 2 - Tipo de arquivo a ser exportado {#step-2---type-of-file-to-export}

Selecione o tipo de documento a ser exportado, ou seja, o schema dos dados para exportar.

Por padrão, quando a exportação é iniciada a partir do nó **[!UICONTROL Jobs]**, os dados são obtidos a partir da tabela de destinatários. When the export is launched from a list of data (from the **[!UICONTROL right click > Export]** menu), the table to which the data belongs is automatically filled in in the **[!UICONTROL Document type]** field.

![](assets/s_ncs_user_export_wizard02.png)

* By default, the **[!UICONTROL Download the file generated on the server after the export]** option is selected. No campo **[!UICONTROL Local file]**, preencha o nome e o caminho do arquivo que será criado ou procure o disco local clicando na pasta à direita do campo. Você pode desmarcar essa opção para inserir o caminho de acesso e o nome do arquivo de saída do servidor.

   >[!NOTE]
   >
   >Os trabalhos de importação e exportação automáticos são sempre executados no servidor.
   >
   >Para exportar apenas alguns dados, clique em **[!UICONTROL Advanced parameters]** e insira o número de linhas que devem ser exportadas no campo apropriado.

* É possível criar uma exportação diferencial para exportar apenas registros que foram modificados desde a última execução. To do this, click the **[!UICONTROL Advanced parameters]** link, then click the **[!UICONTROL Differential export]** tab, then select **[!UICONTROL Activate differential export]**.

   ![](assets/s_ncs_user_export_wizard02_b.png)

   Você deve inserir a data da última modificação. Ele pode ser calculado ou recuperado de um campo.

### Etapa 3 - Definição do formato de saída {#step-3---defining-the-output-format}

Selecione um formato de saída para o arquivo de exportação. Os formatos a seguir podem ser usados: texto, texto fixed-column, CSV e XML.

![](assets/s_ncs_user_export_wizard03.png)

* Para o formato **[!UICONTROL Text]**, selecione os delimitadores para separar as colunas (guias, vírgulas, ponto e vírgula ou personalizado) e as strings (aspas simples, duplas ou nenhuma).
* Para **[!UICONTROL text]** e **[!UICONTROL CSV]**, você pode selecionar a opção **[!UICONTROL Use first lines as column titles]**.
* Indique o formato de data e o formato do número. Para isso, clique no botão **[!UICONTROL Edit]** do campo correspondente e utilize o editor.
* For fields containing enumerated values, you can select **[!UICONTROL Export labels instead of internal values of enumerations]**. Por exemplo, o título pode ser armazenado no formato **1=Sr.**, **2=Srta.**,**3=Sra.**. Se essa opção estiver selecionada, **Sr.**, **Srta.**, **Sra.** serão exportados.

### Etapa 4 - Seleção de dados {#step-4---data-selection}

Selecione os campos a serem exportados. Para fazer isso:

1. Double-click the desired fields in the **[!UICONTROL Available fields]** list in order to add them to the **[!UICONTROL Output columns]** section.
1. Use as setas à direita da lista para definir a ordem dos campos no arquivo de saída.

   ![](assets/s_ncs_user_export_wizard04.png)

1. Clique no botão **[!UICONTROL Add]** para chamar as funções. Para mais informações, consulte as [Lista de funções](../../platform/using/defining-filter-conditions.md#list-of-functions).

### Etapa 5 - Classificação das colunas {#step-5---sorting-columns}

Selecione a ordem de classificação das colunas.

![](assets/s_ncs_user_export_wizard05.png)

### Etapa 6 - Condições de filtro {#step-6---filter-conditions-}

Você pode adicionar condições de filtro para evitar a exportação de todos os dados. A configuração dessa filtragem é a mesma que o direcionamento do destinatário no assistente de delivery. Consulte [esta página](../../delivery/using/steps-defining-the-target-population.md).

![](assets/s_ncs_user_export_wizard05_b.png)

### Passo 7 - Formatação de dados {#step-7---data-formatting}

Você pode modificar a ordem e o rótulo dos campos do arquivo de saída e aplicar transformações aos dados de origem.

* Para alterar a ordem das colunas a serem exportadas, selecione a coluna indicada e use as setas azuis à direita da tabela.
* Para alterar o rótulo de um campo, clique na célula da coluna **[!UICONTROL Label]** que corresponde ao campo que deve ser modificado e insira o novo rótulo. Pressione Enter no teclado para confirmar.
* Para aplicar uma transformação de caso ao conteúdo, selecione o respectivo campo na coluna **[!UICONTROL Transformation]**. É possível selecionar:

   * Alterar para minúsculas
   * Alterar para maiúsculas
   * Primeira letra em maiúscula

   ![](assets/s_ncs_user_export_wizard06.png)

* Clique em **[!UICONTROL Add a calculated field]** para criar um novo campo calculado (por exemplo, uma coluna contendo o sobrenome + nome). Para obter mais informações, consulte os [Campos calculados](../../platform/using/importing-data.md#calculated-fields).

Se você estiver exportando uma coleção de elementos (por exemplo, assinaturas dos destinatários, as listas às quais elas pertencem etc.), você deverá especificar o número de elementos na coleção que deseja exportar.

![](assets/s_ncs_user_export_wizard06_c.png)

### Etapa 8 - Visualização de dados {#step-8---data-preview}

Click **[!UICONTROL Start the preview of the data]** for a preview of the export result. Por padrão, as 200 primeiras linhas são exibidas. Para alterar esse valor, clique nas setas à direita do campo **[!UICONTROL Lines to display]**.

![](assets/s_ncs_user_export_wizard07.png)

Clique nas guias na parte inferior do assistente para alternar da visualização dos resultados nas colunas para os resultados em XML. Você também pode visualizar as consultas SQL geradas.

### Etapa 9 - Iniciar a exportação {#step-9---launching-the-export}

Clique em **[!UICONTROL Start]** para iniciar a exportação de dados.

![](assets/s_ncs_user_export_wizard08.png)

## Exportação de dados por meio de um workflow {#exporting-data-via-a-workflow}

Os workflows podem ser uma maneira útil de automatizar alguns dos processos de exportação ou exportar conjuntos precisos de dados após usar algumas atividades disponíveis de gestão de dados disponíveis para transformar seus dados.

Para saber mais sobre como exportar dados de workflow, consulte [esta seção](../../workflow/using/how-to-use-workflow-data.md).
