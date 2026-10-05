---
product: campaign
title: Início e término
description: Saiba mais sobre atividades de fluxo de trabalho de início e término
feature: Workflows
hide: true
exl-id: 56dfbaf3-93de-4ade-b4ad-9b54d239c7a5
TQID: 'https://experienceleague.adobe.com/Vw3JK6VyMf4HrEkvYk4-34dGTp0e3e1xPZ8jG0bAxz8'
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
source-wordcount: '135'
ht-degree: 100%
---
# Início e término{#start-and-end}



As atividades **[!UICONTROL Start]** e **[!UICONTROL End]** permitem marcar graficamente o início e o fim de um fluxo de trabalho. Essas atividades não têm impacto funcional e, portanto, são opcionais.

* **[!UICONTROL Start]**

  A execução de um fluxo de trabalho começa com atividades sem uma transição de entrada e atividades tipo início.

  ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL End]**

  É possível configurar a atividade **[!UICONTROL End]** para interromper todas as tarefas em andamento. Para fazer isso, clique duas vezes na atividade para exibir suas propriedades e marque a opção apropriada.

  ![](assets/s_user_segmentation_end.png)

  Os dados na tabela de trabalho são excluídos automaticamente quando a atividade final é habilitada. Se isso não for necessário e para evitar cargas desnecessárias, é possível desabilitar a transição na última saída de atividade. Por exemplo, em uma saída de remessa, se nenhum processo estiver agendado, desmarque a opção relevante conforme mostrado abaixo:

  ![](assets/s_advuser_delivery_option_no_output.png)

