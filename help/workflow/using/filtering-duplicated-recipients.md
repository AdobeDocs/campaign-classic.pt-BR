---
product: campaign
title: Filtrar recipients duplicados
description: Saiba como filtrar destinatários duplicados
feature: Workflows
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 100%

---

# Filtrar recipients duplicados {#filtering-duplicated-recipients}

![](../../assets/common.svg)

Neste exemplo, queremos filtrar os recipients que aparecem duas vezes ou mais em uma delivery para recuperar perfis duplicados.

Para criar este exemplo, aplique as seguintes etapas:

1. Arraste e solte uma atividade **[!UICONTROL Query]** em um workflow e abra a atividade.
1. Clique em **[!UICONTROL Edit query]** e defina as dimensões do filtro e do direcionamento para **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Defina a seguinte condição de filtro para o recipient do target que existe no log de delivery. Escolha **Recipient delivery log (broadlog)** na coluna **Expression**, escolha **exist such as** na coluna **Operator**.

   ![](assets/query_recipients_2.png)

1. Defina a condição de filtro a seguir para direcionar sua delivery. Escolha **[!UICONTROL Internal name]** na coluna Expression e **[!UICONTROL equal to]** na coluna Operator.
1. Na coluna Valor, adicione o nome interno da delivery desejada.

   ![](assets/query_recipients_3.png)

1. Com um operador **[!UICONTROL AND]**, repita as mesmas operações para selecionar outros deliveries.

   ![](assets/query_recipients_4.png)

A transição de saída contém os recipients duplicados alcançados nas deliveries.
