---
title: Iniciar e finalizar
seo-title: Iniciar e finalizar
description: Iniciar e finalizar
seo-description: null
page-status-flag: never-activated
uuid: ec0c818c-c307-4f50-908c-507bce0ea27b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 8b239d5e-2317-42c8-9fee-7d40bea624da
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 100%

---


# Iniciar e finalizar{#start-and-end}

As atividades **[!UICONTROL Start]** e **[!UICONTROL End]** permitem marcar graficamente o início e o fim de um workflow. Essas atividades não têm impacto funcional e, portanto, são opcionais.

* **[!UICONTROL Start]**

   A execução de um workflow começa com atividades sem uma transição de entrada e atividades tipo início.

   ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL End]**

   É possível configurar a atividade **[!UICONTROL End]** para interromper todas as tarefas em andamento. Para fazer isso, clique duas vezes na atividade para exibir suas propriedades e marque a opção apropriada.

   ![](assets/s_user_segmentation_end.png)

   Os dados na tabela de trabalho são excluídos automaticamente quando a atividade final é habilitada. Se isso não for necessário e para evitar cargas desnecessárias, é possível desabilitar a transição na última saída de atividade. Por exemplo, em uma saída de remessa, se nenhum processo estiver agendado, desmarque a opção relevante conforme mostrado abaixo:

   ![](assets/s_advuser_delivery_option_no_output.png)

