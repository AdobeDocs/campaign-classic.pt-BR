---
title: Extração de dados (arquivo)
description: Saiba mais sobre a atividade de fluxo de trabalho da extração de dados (arquivo).
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
source-git-commit: 5eb82bb5dae589cb18d42695565b25dad36006bd

---


# Extração de dados (arquivo){#extraction-file}

You can extract data from a workflow table in an external file using the **[!UICONTROL Data extraction (file)]** activity.

>[!CAUTION]
>
>Essa atividade sempre deve ter uma transição de entrada que contenha os dados a serem extraídos.

Para configurar a extração de dados, siga as seguintes etapas:

1. Especifique o nome do arquivo de output: esse nome pode conter variáveis, inseridas por meio do botão de personalização à direita do campo.
1. Clique para selecionar **[!UICONTROL Edit the file format...]** os dados a serem extraídos.

   ![](assets/s_advuser_extract_file_param.png)

   The **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** option adds an extra step to filter the final result of the aggregate, for example on a given purchase order type, customers who have ordered more than 10 times, etc.

1. Se necessário, você pode adicionar novas colunas ao arquivo de output, como, por exemplo, computar ou processar resultados. To do this, click the **[!UICONTROL Add]** icon

   ![](assets/s_advuser_extract_file_add_col.png)

   In the additional line, click the **[!UICONTROL Edit expression]** icon to define the content of the new column.

   ![](assets/s_advuser_extract_file_add_exp.png)

   Você então acessará a janela de seleção. Click **[!UICONTROL Advanced selection]** to choose the process to be applied to the data.

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   Escolha a fórmula desejada na lista.

   ![](assets/s_advuser_extract_file_agregate_values.png)

## Lista de funções agregadas {#list-of-aggregate-functions}

Veja a seguir uma lista de funções agregadas disponíveis:

* **[!UICONTROL Count]** para contar todos os valores não nulos do campo a agregar, incluindo valores duplicados (do campo agregado),

   **[!UICONTROL Distinct]** para contar o número total de valores diferentes e não nulos do campo a ser agregado (valores duplicados são excluídos antes do cálculo),

* **[!UICONTROL Sum]** para calcular a soma dos valores de um campo numérico,
* **[!UICONTROL Minimum value]** calcular os valores mínimos de um campo (numéricos ou não),
* **[!UICONTROL Maximum value]** para calcular os valores máximos de um campo (numéricos ou não),
* **[!UICONTROL Average]** para calcular a média dos valores de um campo numérico.

