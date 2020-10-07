---
title: Consulta usando uma relação muitos-para-muitos
description: Saiba como executar consultas usando uma relação muitos para muitos
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 68%

---


# Consulta usando uma relação muitos-para-muitos {#querying-using-a-many-to-many-relationship}

Neste exemplo, queremos recuperar recipients não foram contatados durante os últimos 7 dias. Esta query aborda todas as deliveries.

Este exemplo também mostra como configurar um filtro relacionado à escolha de um elemento de coleção (ou nó laranja). Collection elements are available in the **[!UICONTROL Field to select]** window.

* Qual tabela precisa ser selecionada?

   A tabela de recipient (**nms:recipient**)

* Campos a serem selecionados para a coluna de saída

   Primary key, Last name, First name e Email.

* Com base em quais critérios as informações são filtradas?

   Com base nos registros de delivery de recipients, 7 dias antes de hoje.

Siga as etapas abaixo:

1. Abra o editor de query genérico e selecione a tabela Recipient **[!UICONTROL (nms:recipient)]**.
1. In the **[!UICONTROL Data to extract]** window, select **[!UICONTROL Primary key]**, **[!UICONTROL First name]**, **[!UICONTROL Last name]** and **[!UICONTROL Email]**.

   ![](assets/query_editor_nveau_33.png)

1. Na janela de classificação, classifique os nomes em ordem alfabética.

   ![](assets/query_editor_nveau_34.png)

1. In the **[!UICONTROL Data filtering]** window, select **[!UICONTROL Filtering conditions]**.
1. Na janela **[!UICONTROL Target element]**, a condição do filtro para extrair perfis sem log de rastreamento nos últimos 7 dias envolve duas etapas. O elemento precisa selecionar um link muitos-para-muitos.

   * Start by selecting the **[!UICONTROL Recipient delivery logs (broadlog)]** collection element (orange node) for the first **[!UICONTROL Value]** column.

      ![](assets/query_editor_nveau_67.png)

      Escolha o **[!UICONTROL do not exist as]** operador. Não há necessidade de selecionar um segundo valor nesta linha.

   * O conteúdo da segunda condição do filtro depende da primeira. Here, the **[!UICONTROL Event date]** field is offered directly in the **[!UICONTROL Recipient delivery logs]** table since there is a link to this table.

      ![](assets/query_editor_nveau_36.png)

      Selecione **[!UICONTROL Event date]** com o **[!UICONTROL greater than or equal to]** operador. Select the **[!UICONTROL DaysAgo (7)]** value. To do this, click **[!UICONTROL Edit expression]** in the **[!UICONTROL Value]** field. Na **[!UICONTROL Formula type]** janela, selecione **[!UICONTROL Process on dates]** e **[!UICONTROL Current date minus n days]**, dando &quot;7&quot; como um valor.

      ![](assets/query_editor_nveau_37.png)

      A condição de filtro é configurada.

      ![](assets/query_editor_nveau_38.png)

1. Na janela **[!UICONTROL Data formatting]**, alterne os últimos nomes para caixa alta. Click the **[!UICONTROL Last name]** line in the **[!UICONTROL Transformation]** column and select **[!UICONTROL Switch to upper case]** in the drop-down menu.

   ![](assets/query_editor_nveau_39.png)

1. Use the **[!UICONTROL Add a calculated field]** function to insert a column into the data preview window.

   Neste exemplo, adicione um campo calculado com o nome e o sobrenome dos recipients em uma única coluna. Clique na **[!UICONTROL Add a calculated field]** função. In the **[!UICONTROL Export calculated field definition]** window, enter a label and an internal name and choose the **[!UICONTROL JavaScript Expression]** type. Em seguida, insira a seguinte expressão:

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   Clique em **[!UICONTROL OK]**. The **[!UICONTROL Data formatting]** window is configured.

   Para obter mais informações sobre adição de campos calculados, consulte esta seção.

1. The result is shown in the **[!UICONTROL Data preview]** window. Os recipients que não tiverem sido contatados nos últimos 7 dias serão exibidos em ordem alfabética. Os nomes são exibidos em caixa alta e a coluna com nome e sobrenome é criada.

   ![](assets/query_editor_nveau_41.png)
