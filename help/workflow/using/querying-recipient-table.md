---
title: Consulta à tabela de recipients
description: Saiba como consultar a tabela de destinatários
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
source-git-commit: ab2c133aaa2f754e56fe8fdfc76d10526d4d1ce2

---


# Consulta à tabela de recipients {#querying-recipient-table}

Neste exemplo, queremos recuperar os nomes e e-mails dos recipients cujos domínios de e-mail são &quot;orange.co.uk&quot; e que não estão em Londres.

* Qual tabela devemos selecionar?

   A tabela do recipient (nms:recipient)

* Campos a serem selecionados como colunas de saída

   E-mail, nome, cidade e número da conta

* Quais são as condições do filtro dos recipients?

   domínio de e-mail e cidade

* É configurada uma classificação?

   Sim, com base em **[!UICONTROL Account number]** e **[!UICONTROL Last name]**

Para criar este exemplo, aplique as seguintes etapas:

1. Click **[!UICONTROL Tools > Generic query editor...]** and choose the **Recipients** (**nms:recipient**) table. Em seguida, clique em **[!UICONTROL Next]**.
1. Escolha: **[!UICONTROL Last name]**, **[!UICONTROL First name]**, **[!UICONTROL Email]**, **[!UICONTROL City]** e **[!UICONTROL Account number]**. Esses campos são adicionados a **[!UICONTROL Output columns]**. Em seguida, clique em **[!UICONTROL Next]**.

   ![](assets/query_editor_03.png)

1. Classifique as colunas para exibi-las na ordem correta. Aqui, devemos classificar números de conta em ordem decrescente e nomes em ordem alfabética. Em seguida, clique em **[!UICONTROL Next]**.

   ![](assets/query_editor_04.png)

1. Na **[!UICONTROL Data filtering]** janela, refine sua pesquisa: escolha **[!UICONTROL Filtering conditions]** e clique em **[!UICONTROL Next]**.
1. The **[!UICONTROL Target element]** window lets you enter the filter settings.

   Defina a seguinte condição de filtro: recipients com um domínio de e-mail igual a &quot;orange.co.uk&quot;. To do this, choose **Email domain (@email)** in the **[!UICONTROL Expression]** column, choose **equal to** in the **[!UICONTROL Operator]** column and enter &quot;orange.co.uk&quot; in the **[!UICONTROL Value]** column.

   ![](assets/query_editor_05.png)

1. If needed, click the **[!UICONTROL Distribution of values]** button to view a distribution based on the email domain of prospects. Uma porcentagem está disponível para cada domínio de e-mail no banco de dados. Domínios diferentes de &quot;orange.co.uk&quot; são exibidos até o filtro ser aplicado.

   Um resumo da consulta é exibido na parte inferior da janela: Domínio de **email igual a &#39;orange.co.uk&#39;**.

1. Click the **[!UICONTROL Preview]** to get an idea of the query result: only &quot;orange.co.uk&quot; email domains are displayed.

   ![](assets/query_editor_nveau_17.png)

1. Agora, vamos alterar a query para localizar os contatos que não moram em Londres.

   Selecione **[!UICONTROL City (location/@city)]** na **[!UICONTROL Expression]** coluna, **[!UICONTROL different from]** como um operador e digite **[!UICONTROL London]** na **[!UICONTROL Value]** coluna.

   ![](assets/query_editor_08.png)

1. This will take you to the **[!UICONTROL Data formatting]** window. Verifique a ordem da coluna. Mova a coluna &quot;City&quot; logo ao lado da coluna &quot;Account number&quot;.

   Desmarque a coluna &quot;First name&quot; para removê-la da lista.

   ![](assets/query_editor_nveau_15.png)

1. Na **[!UICONTROL Data preview]** janela, clique em **[!UICONTROL Start the preview of the data]**. Essa função calcula o resultado da query.

   The **[!UICONTROL Column results]** tab shows the query result in columns.

   O resultado mostra todos os recipients com um domínio de e-mail &quot;orange.co.uk&quot; que não vivem em Londres. A coluna &quot;First name&quot; não é mostrada porque foi desmarcada durante o estágio anterior. Os números de conta são classificados em ordem decrescente.

   ![](assets/query_editor_nveau_12.png)

   The **[!UICONTROL XML result]** tab shows the result in XML format.

   ![](assets/query_editor_nveau_13.png)

   The **[!UICONTROL Generated QSL queries]** tab shows the query result in SQL format.

   ![](assets/query_editor_nveau_14.png)
