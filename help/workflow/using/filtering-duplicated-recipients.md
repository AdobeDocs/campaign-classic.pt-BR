---
title: Filtro de recipients duplicados
description: Saiba como filtrar destinatários duplicados
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


# Filtro de recipients duplicados {#filtering-duplicated-recipients}

Neste exemplo, queremos filtrar os recipients que aparecem duas vezes ou mais em uma delivery para recuperar perfis duplicados.

Para criar este exemplo, aplique as seguintes etapas:

1. Drag and drop a **[!UICONTROL Query]** activity in a workflow and open the activity.
1. Click **[!UICONTROL Edit query]** and set the target and filtering dimensions to **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Defina a seguinte condição de filtro para o recipient do target que existe no log de delivery. Escolha **Recipient delivery log (broadlog)** na coluna **Expression**, escolha **exist such as** na coluna **Operator**.

   ![](assets/query_recipients_2.png)

1. Defina a condição de filtro a seguir para direcionar sua delivery. Choose **[!UICONTROL Internal name]** in the Expression column and **[!UICONTROL equal to]** in the Operator column.
1. Na coluna Valor, adicione o nome interno da delivery desejada.

   ![](assets/query_recipients_3.png)

1. With an **[!UICONTROL AND]** operator, repeat the same operations to target other deliveries.

   ![](assets/query_recipients_4.png)

A transição de saída contém os recipients duplicados alcançados nas deliveries.
