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
translation-type: ht
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# Consultando o gerenciamento de agrupamento {#querying-using-grouping-management}

Neste exemplo, devemos executar uma query para localizar todos os domínios de e-mail selecionados mais de 30 vezes durante as deliveries anteriores.

* Qual tabela precisa ser selecionada?

   A tabela de recipient (nms:recipient)

* Campos a serem selecionados nas colunas de saída?

   Email domain e primary key (with count).

* Agrupamento de dados?

   Com base no domínio de e-mail com uma contagem de chaves primárias acima de 30. Esta operação é executada com a opção **[!UICONTROL Group by + Having]**. O **[!UICONTROL Group by + Having]** permite agrupar dados (&quot;agrupar por&quot;) e criar uma seleção do que foi agrupado (&quot;ter&quot;).

Para criar este exemplo, aplique as seguintes etapas:

1. Abra o **[!UICONTROL Generic query editor]** e escolha a tabela &quot;Recipients&quot; (**nms:recipient**).

   ![](assets/query_editor_02.png)

1. Na janela **[!UICONTROL Data to extract]**, selecione os campos **[!UICONTROL Email domain]** e **[!UICONTROL Primary key]**. Execute uma contagem no campo **[!UICONTROL Primary key]**.

   Para obter mais informações sobre a contagem da chave principal, consulte [this section](../../platform/using/defining-filter-conditions.md#building-expressions).

1. Marque a caixa **[!UICONTROL Handle groupings (GROUP BY + HAVING)]**.

   ![](assets/query_editor_nveau_29.png)

1. Na janela **[!UICONTROL Sorting]**, classifique os domínios de email em ordem decrescente. Para fazer isso, marque **[!UICONTROL Yes]** na coluna **[!UICONTROL Descending sort]**. Clique em **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_70.png)

1. Em **[!UICONTROL Data filtering]**, selecione **[!UICONTROL Filtering conditions]**. Vá para a janela **[!UICONTROL Target elements]** e clique em **[!UICONTROL Next]**.
1. Na janela **[!UICONTROL Data grouping]**, selecione o **[!UICONTROL Email domain]** clicando em **[!UICONTROL Add]**.

   Esta janela de agrupamento de dados é exibida somente se a caixa **[!UICONTROL Handle groupings (GROUP BY + HAVING]**) foi marcada.

   ![](assets/query_editor_blacklist_04.png)

1. Na janela **[!UICONTROL Grouping condition]**, indique uma contagem de chaves primária maior que 30, pois desejamos que apenas domínios de e-mail alcançados mais de 30 vezes sejam retornados como resultados.

   Esta janela aparece quando a caixa **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** foi marcada: aqui é onde o resultado do agrupamento é filtrado (HAVING).

   ![](assets/query_editor_blacklist_05.png)

1. Na janela **[!UICONTROL Data formatting]**, clique em **[!UICONTROL Next]**: nenhuma formatação é necessária aqui.
1. Na janela de visualização de dados, clique em **[!UICONTROL Launch data preview]**: aqui, três domínios de e-mail diferentes alcançados mais de 30 vezes são retornados.

   ![](assets/query_editor_blacklist_06.png)
