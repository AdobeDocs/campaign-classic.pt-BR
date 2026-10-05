---
product: campaign
title: Filtrar destinatários duplicados
description: Saiba como filtrar destinatários duplicados
feature: Workflows
hide: true
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
TQID: 'https://experienceleague.adobe.com/qsfiVfgYUq38VWmh5QEq87-WBwFGrc2iCSeAhjaKXbg'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 100%
---
# Filtrar destinatários duplicados {#filtering-duplicated-recipients}



Neste exemplo, queremos filtrar os destinatários que aparecem duas vezes ou mais em uma entrega para recuperar perfis duplicados.

Para criar este exemplo, aplique as seguintes etapas:

1. Arraste e solte uma atividade **[!UICONTROL Query]** em um fluxo de trabalho e abra a atividade.
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
