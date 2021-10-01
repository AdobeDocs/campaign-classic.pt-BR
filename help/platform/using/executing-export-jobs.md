---
product: campaign
title: Configuração de trabalhos de exportação
description: Saiba como configurar e executar trabalhos de exportação no Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 94fc473a-dc49-41e8-b572-51c162b09996
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: ht
source-wordcount: '926'
ht-degree: 100%

---

# Configurar trabalhos de exportação {#executing-export-jobs}

![](../../assets/common.svg)

Os trabalhos de exportação permitem acessar e extrair dados do banco de dados: contatos, clientes, listas, segmentos etc.

Por exemplo, pode ser útil usar dados de rastreamento de campanha (histórico de rastreamento etc.) em uma planilha. Os dados de output podem estar em formato txt, CSV, TAB ou XML.

O assistente de exportação permite configurar uma exportação, definir suas opções e iniciar a execução. É uma série de telas cujo conteúdo depende do tipo de importação (simples ou múltipla) e dos direitos do operador.

O assistente de exportação é exibido após a criação de um novo trabalho de exportação (consulte [Criar trabalhos de importação e exportação](../../platform/using/creating-import-export-jobs.md).

## Etapa 1 - Escolher o template de exportação {#step-1---choosing-the-export-template}

Ao iniciar o assistente de exportação, primeiro é necessário selecionar um template. Como exemplo, para configurar a exportação de destinatários que se registraram recentemente, siga as etapas abaixo:

1. Selecione a pasta **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]**.
1. Clique em **Novo** e em **Exportar** para criar o template de exportação.

   ![](assets/s_ncs_user_export_wizard01.png)

1. Clique na seta à direita do campo **[!UICONTROL Export template]** para selecionar o modelo ou clique em **[!UICONTROL Select link]** para navegar na árvore.

   O modelo nativo é **[!UICONTROL New text export]**. Este template não deve ser modificado, mas você pode duplicá-lo para configurar um novo template. Por padrão, os modelos de exportação são salvos no nó **[!UICONTROL Resources > Templates > Job templates]**.

1. Insira um nome para a exportação no campo **[!UICONTROL Label]**. Você pode adicionar uma descrição.
1. Selecione o tipo de exportação. Existem dois tipos possíveis de exportação: **[!UICONTROL Simple export]** para exportar apenas um arquivo e **[!UICONTROL Multiple export]** para exportar vários arquivos em uma única execução, de um ou mais tipos de documento de origem.

## Etapa 2 - Tipo de arquivo a ser exportado {#step-2---type-of-file-to-export}

Selecione o tipo de documento a ser exportado, ou seja, o schema dos dados para exportar.

Por padrão, quando a exportação é iniciada a partir do nó **[!UICONTROL Jobs]**, os dados são obtidos a partir da tabela de recipients. Quando a exportação é iniciada a partir de uma lista de dados (do menu **[!UICONTROL right click > Export]**), a tabela à qual os dados pertencem é automaticamente preenchida no campo **[!UICONTROL Document type]**.

![](assets/s_ncs_user_export_wizard02.png)

* A opção **[!UICONTROL Download the file generated on the server after the export]** está selecionada por padrão. No campo **[!UICONTROL Local file]**, preencha o nome e o caminho do arquivo que será criado ou procure o disco local clicando na pasta à direita do campo. Você pode desmarcar essa opção para inserir o caminho de acesso e o nome do arquivo de saída do servidor.

   >[!NOTE]
   >
   >Os trabalhos de importação e exportação automáticos são sempre executados no servidor.
   >
   >Para exportar apenas alguns dados, clique em **[!UICONTROL Advanced parameters]** e insira o número de linhas que devem ser exportadas no campo apropriado.

* É possível criar uma exportação diferencial para exportar apenas registros que foram modificados desde a última execução. Para fazer isso, clique no link **[!UICONTROL Advanced parameters]** e, em seguida, clique na guia **[!UICONTROL Differential export]** e, em seguida, selecione **[!UICONTROL Activate differential export]**.

   ![](assets/s_ncs_user_export_wizard02_b.png)

   Você deve inserir a data da última modificação. Ele pode ser calculado ou recuperado de um campo.

## Etapa 3 - Definir o formato de saída {#step-3---defining-the-output-format}

Selecione um formato de saída para o arquivo de exportação. Os formatos a seguir podem ser usados: texto, texto fixed-column, CSV e XML.

![](assets/s_ncs_user_export_wizard03.png)

* Para o formato **[!UICONTROL Text]**, selecione os delimitadores para separar as colunas (guias, vírgulas, ponto e vírgula ou personalizado) e as strings (aspas simples, duplas ou nenhuma).
* Para **[!UICONTROL text]** e **[!UICONTROL CSV]**, você pode selecionar a opção **[!UICONTROL Use first lines as column titles]**.
* Indique o formato de data e o formato do número. Para fazer isso, clique no botão **[!UICONTROL Edit]** do campo correspondente e utilize o editor.
* Para campos que contém os valores enumerados, é possível selecionar a opção **[!UICONTROL Export labels instead of internal values of enumerations]**. Por exemplo, o título pode ser armazenado no formato **1=Sr.**, **2=Srta.**,**3=Sra.**. Se essa opção estiver selecionada, **Sr.**, **Srta.**, **Sra.** serão exportados.

## Etapa 4 - Seleção de dados {#step-4---data-selection}

Selecione os campos a serem exportados. Para fazer isso:

1. Clique duas vezes nos campos desejados na lista **[!UICONTROL Available fields]** para adicioná-los à seção **[!UICONTROL Output columns]**.
1. Use as setas à direita da lista para definir a ordem dos campos no arquivo de saída.

   ![](assets/s_ncs_user_export_wizard04.png)

1. Clique no botão **[!UICONTROL Add]** para chamar as funções. Para obter mais informações, consulte a [Lista de funções](../../platform/using/defining-filter-conditions.md#list-of-functions).

## Etapa 5 - Classificar colunas {#step-5---sorting-columns}

Selecione a ordem de classificação das colunas.

![](assets/s_ncs_user_export_wizard05.png)

## Etapa 6 - Condições de filtro {#step-6---filter-conditions-}

Você pode adicionar condições de filtro para evitar a exportação de todos os dados. A configuração dessa filtragem é a mesma que o direcionamento do destinatário no assistente de delivery. Consulte [esta página](../../delivery/using/steps-defining-the-target-population.md).

![](assets/s_ncs_user_export_wizard05_b.png)

## Etapa 7 - Formatação de dados {#step-7---data-formatting}

Você pode modificar a ordem e o rótulo dos campos do arquivo de saída e aplicar transformações aos dados de origem.

* Para alterar a ordem das colunas a serem exportadas, selecione a coluna indicada e use as setas azuis à direita da tabela.
* Para alterar o rótulo de um campo, clique na célula da coluna **[!UICONTROL Label]** que corresponde ao campo que deve ser modificado e insira o novo rótulo. Pressione Enter no teclado para confirmar.
* Para aplicar uma transformação de caso ao conteúdo, selecione o respectivo campo na coluna **[!UICONTROL Transformation]**. É possível selecionar:

   * Alterar para minúsculas
   * Alterar para maiúsculas
   * Primeira letra em maiúscula

   ![](assets/s_ncs_user_export_wizard06.png)

* Clique em **[!UICONTROL Add a calculated field]** para criar um novo campo calculado (por exemplo, uma coluna contendo o sobrenome + nome). Para obter mais informações, consulte os [Campos calculados](../../platform/using/executing-import-jobs.md#calculated-fields).

Se você estiver exportando uma coleção de elementos (por exemplo, assinaturas dos destinatários, as listas às quais elas pertencem etc.), você deverá especificar o número de elementos na coleção que deseja exportar.

![](assets/s_ncs_user_export_wizard06_c.png)

## Etapa 8 - Pré-visualização de dados {#step-8---data-preview}

Clique em **[!UICONTROL Start the preview of the data]** para pré-visualizar o resultado da exportação. Por padrão, as 200 primeiras linhas são exibidas. Para alterar esse valor, clique nas setas à direita do campo **[!UICONTROL Lines to display]**.

![](assets/s_ncs_user_export_wizard07.png)

Clique nas guias na parte inferior do assistente para alternar da visualização dos resultados nas colunas para os resultados em XML. Você também pode visualizar as consultas SQL geradas.

## Etapa 9 - Iniciar a exportação {#step-9---launching-the-export}

Clique em **[!UICONTROL Start]** para iniciar a exportação de dados.

![](assets/s_ncs_user_export_wizard08.png)

Você pode monitorar a execução do trabalho de importação (consulte [Monitorar trabalhos de exportação](../../platform/using/monitoring-jobs-execution.md).
