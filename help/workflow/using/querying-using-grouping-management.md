---
title: Consultando o gerenciamento de agrupamento
description: Saiba como executar consultas usando o gerenciamento de agrupamento
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f99e3a4f69cb2b0122f2f6957d419d6b95ad54b1
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 64%

---


# Consultando o gerenciamento de agrupamento {#querying-using-grouping-management}

Neste exemplo, devemos executar uma query para localizar todos os domínios de e-mail selecionados mais de 30 vezes durante as deliveries anteriores.

* Qual tabela precisa ser selecionada?

   A tabela de recipient (nms:recipient)

* Campos a serem selecionados nas colunas de saída?

   Email domain e primary key (with count).

* Agrupamento de dados?

   Com base no domínio de e-mail com uma contagem de chaves primárias acima de 30. This operation is carried out with the **[!UICONTROL Group by + Having]** option. O **[!UICONTROL Group by + Having]** permite agrupar dados (&quot;agrupar por&quot;) e criar uma seleção do que foi agrupado (&quot;ter&quot;).

Para criar este exemplo, aplique as seguintes etapas:

1. Open the **[!UICONTROL Generic query editor]** and choose the Recipient table (**nms:recipient**).

   ![](assets/query_editor_02.png)

1. Na **[!UICONTROL Data to extract]** janela, selecione os campos **[!UICONTROL Email domain]** e **[!UICONTROL Primary key]** . Run a count on the **[!UICONTROL Primary key]** field.

   Para obter mais informações sobre a contagem da chave principal, consulte [this section](../../platform/using/defining-filter-conditions.md#building-expressions).

1. Marque a caixa **[!UICONTROL Handle groupings (GROUP BY + HAVING)]**.

   ![](assets/query_editor_nveau_29.png)

1. Na janela **[!UICONTROL Sorting]**, classifique os domínios de email em ordem decrescente. To do this, check **[!UICONTROL Yes]** in the **[!UICONTROL Descending sort]** column. Clique em **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_70.png)

1. Em **[!UICONTROL Data filtering]**, selecione **[!UICONTROL Filtering conditions]**. Go to the **[!UICONTROL Target elements]** window and click **[!UICONTROL Next]**.
1. Na **[!UICONTROL Data grouping]** janela, selecione o **[!UICONTROL Email domain]** clicando em **[!UICONTROL Add]**.

   This data grouping window is only displayed if the **[!UICONTROL Handle groupings (GROUP BY + HAVING]**) box was checked.

   ![](assets/query_editor_blocklist_04.png)

1. Na janela **[!UICONTROL Grouping condition]**, indique uma contagem de chaves primária maior que 30, pois desejamos que apenas domínios de e-mail alcançados mais de 30 vezes sejam retornados como resultados.

   This window appears when the **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** box was checked: this is where the grouping result is filtered (HAVING).

   ![](assets/query_editor_blocklist_05.png)

1. In the **[!UICONTROL Data formatting]** window, click **[!UICONTROL Next]**: no formatting is necessary here.
1. Na janela de visualização de dados, clique em **[!UICONTROL Launch data preview]**: aqui, três domínios de e-mail diferentes alcançados mais de 30 vezes são retornados.

   ![](assets/query_editor_blocklist_06.png)
