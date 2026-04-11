---
product: campaign
title: Início e término
description: Saiba mais sobre atividades de fluxo de trabalho de início e término
feature: Workflows
hide: true
exl-id: 56dfbaf3-93de-4ade-b4ad-9b54d239c7a5
source-git-commit: 76f483dcda9f8a5ed93355d68bb1d1a589d55722
workflow-type: tm+mt
source-wordcount: '133'
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
