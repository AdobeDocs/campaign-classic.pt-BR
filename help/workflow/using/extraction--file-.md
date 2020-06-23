---
title: Extração de dados (arquivo)
description: Saiba mais sobre a atividade de workflow da extração de dados (arquivo).
page-status-flag: never-activated
uuid: c1e3fde3-183c-4602-9cef-760e4648fcf7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: fe4e6f64-eb0a-44bc-8221-6c9bfb99871f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a215109db2d511180c91723059cd8ca10a34a612
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 66%

---


# Extração de dados (arquivo){#extraction-file}

You can extract data from a workflow table in an external file using the **[!UICONTROL Data extraction (file)]** activity.

>[!CAUTION]
>
>Essa atividade sempre deve ter uma transição de entrada que contenha os dados a serem extraídos.

Para configurar a extração de dados, siga as seguintes etapas:

1. Especifique o nome do arquivo de output: esse nome pode conter variáveis, inseridas por meio do botão de personalização à direita do campo.
1. Click **[!UICONTROL Edit the file format...]** to select the data to be extracted.

   ![](assets/s_advuser_extract_file_param.png)

   The **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** option adds an extra step to filter the final result of the aggregate, for example on a given purchase order type, customers who have ordered more than 10 times, etc.

1. Se necessário, você pode adicionar novas colunas ao arquivo de output, como, por exemplo, computar ou processar resultados. To do this, click the **[!UICONTROL Add]** icon.

   ![](assets/s_advuser_extract_file_add_col.png)

   Na linha adicional, clique no ícone **[!UICONTROL Edit expression]** para definir o conteúdo da nova coluna.

   ![](assets/s_advuser_extract_file_add_exp.png)

   Você então acessará a janela de seleção. Clique em **[!UICONTROL Advanced selection]** para escolher o processo a ser aplicado aos dados.

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   Escolha a fórmula desejada na lista.

   ![](assets/s_advuser_extract_file_agregate_values.png)

Você pode definir um pós-processo a ser executado durante a extração de dados, permitindo que você compacte ou criptografe os arquivos. Para fazer isso, o comando desejado deve ser adicionado na **[!UICONTROL Script]** guia da atividade.

Para obter mais informações, consulte esta seção: [Como compactar ou criptografar um arquivo](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

![](assets/postprocessing_dataextraction.png)

## Lista de funções agregadas {#list-of-aggregate-functions}

Veja a seguir uma lista de funções agregadas disponíveis:

* **[!UICONTROL Count]** para contar todos os valores não nulos do campo a ser agregado, incluindo valores duplicados (do campo de agregação),

   **[!UICONTROL Distinct]** para contar o número total de valores diferentes e não nulos do campo a ser agregado (valores duplicados são excluídos antes do cálculo),

* **[!UICONTROL Sum]** para calcular a soma dos valores de um campo numérico,
* **[!UICONTROL Minimum value]** para calcular os valores mínimos de um campo (numérico ou não),
* **[!UICONTROL Maximum value]** para calcular os valores máximos de um campo (numérico ou não),
* **[!UICONTROL Average]** para calcular a média dos valores de um campo numérico.

