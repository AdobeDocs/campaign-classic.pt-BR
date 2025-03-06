---
product: campaign
title: Filtrar destinatários duplicados
description: Saiba como filtrar destinatários duplicados
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 100%

---

# Filtrar destinatários duplicados {#filtering-duplicated-recipients}



Neste exemplo, queremos filtrar os destinatários que aparecem duas vezes ou mais em uma entrega para recuperar perfis duplicados.

Para criar este exemplo, aplique as seguintes etapas:

1. Arraste e solte uma atividade **[!UICONTROL Query]** em um workflow e abra a atividade.
1. Clique em **[!UICONTROL Edit query]** e defina as dimensões do filtro e do direcionamento para **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Defina a seguinte condição de filtro para o destinatário do target que existe no log de entrega. Escolha **Recipient delivery log (broadlog)** na coluna **Expression**, escolha **exist such as** na coluna **Operator**.

   ![](assets/query_recipients_2.png)

1. Defina a condição de filtro a seguir para direcionar sua entrega. Escolha **[!UICONTROL Internal name]** na coluna Expression e **[!UICONTROL equal to]** na coluna Operator.
1. Na coluna Valor, adicione o nome interno da entrega desejada.

   ![](assets/query_recipients_3.png)

1. Com um operador **[!UICONTROL AND]**, repita as mesmas operações para selecionar outras entregas.

   ![](assets/query_recipients_4.png)

A transição de saída contém os destinatários duplicados alcançados nas entregas.
