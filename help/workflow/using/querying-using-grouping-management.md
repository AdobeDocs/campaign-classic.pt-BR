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
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# Consultando o gerenciamento de agrupamento {#querying-using-grouping-management}

Neste exemplo, devemos executar uma query para localizar todos os domínios de e-mail selecionados mais de 30 vezes durante as deliveries anteriores.

* Qual tabela precisa ser selecionada?

   A tabela do recipient (nms:recipient)

* Campos a serem selecionados nas colunas de saída?

   Email domain e primary key (with count).

* Agrupamento de dados?

   Com base no domínio de e-mail com uma contagem de chaves primárias acima de 30. This operation is carried out with the **[!UICONTROL Group by + Having]** option. **[!UICONTROL Group by + Having]** permite agrupar dados (&quot;grupo por&quot;) e fazer uma seleção do que foi agrupado (&quot;tendo&quot;).

Para criar este exemplo, aplique as seguintes etapas:

1. Open the **[!UICONTROL Generic query editor]** and choose the Recipient table (**nms:recipient**).

   ![](assets/query_editor_02.png)

1. Na **[!UICONTROL Data to extract]** janela, selecione os campos **[!UICONTROL Email domain]** e **[!UICONTROL Primary key]** . Execute uma contagem no **[!UICONTROL Primary key]** campo.

   Para obter mais informações sobre a contagem da chave principal, consulte [this section](../../platform/using/defining-filter-conditions.md#building-expressions).

1. Marque a **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** caixa.

   ![](assets/query_editor_nveau_29.png)

1. In the **[!UICONTROL Sorting]** window, sort email domains in descending order. Para fazer isso, verifique **[!UICONTROL Yes]** a **[!UICONTROL Descending sort]** coluna. Clique em **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_70.png)

1. Em **[!UICONTROL Data filtering]**, selecione **[!UICONTROL Filtering conditions]**. Vá para a **[!UICONTROL Target elements]** janela e clique em **[!UICONTROL Next]**.
1. Na **[!UICONTROL Data grouping]** janela, selecione o **[!UICONTROL Email domain]** clicando em **[!UICONTROL Add]**.

   This data grouping window is only displayed if the **[!UICONTROL Handle groupings (GROUP BY + HAVING]**) box was checked.

   ![](assets/query_editor_blacklist_04.png)

1. In the **[!UICONTROL Grouping condition]** window, indicate a primary key count greater than 30 since we only want email domains targeted more than 30 times to be returned as results.

   This window appears when the **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** box was checked: this is where the grouping result is filtered (HAVING).

   ![](assets/query_editor_blacklist_05.png)

1. Na **[!UICONTROL Data formatting]** janela, clique em **[!UICONTROL Next]**: nenhuma formatação é necessária aqui.
1. In the data preview window, click **[!UICONTROL Launch data preview]**: here, three different email domains targeted over 30 times are returned.

   ![](assets/query_editor_blacklist_06.png)
