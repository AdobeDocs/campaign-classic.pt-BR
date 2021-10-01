---
product: campaign
title: Início e término
description: Saiba mais sobre atividades de workflow de início e término
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 56dfbaf3-93de-4ade-b4ad-9b54d239c7a5
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: ht
source-wordcount: '133'
ht-degree: 100%

---

# Início e término{#start-and-end}

![](../../assets/common.svg)

As atividades **[!UICONTROL Start]** e **[!UICONTROL End]** permitem marcar graficamente o início e o fim de um workflow. Essas atividades não têm impacto funcional e, portanto, são opcionais.

* **[!UICONTROL Start]**

   A execução de um workflow começa com atividades sem uma transição de entrada e atividades tipo início.

   ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL End]**

   É possível configurar a atividade **[!UICONTROL End]** para interromper todas as tarefas em andamento. Para fazer isso, clique duas vezes na atividade para exibir suas propriedades e marque a opção apropriada.

   ![](assets/s_user_segmentation_end.png)

   Os dados na tabela de trabalho são excluídos automaticamente quando a atividade final é habilitada. Se isso não for necessário e para evitar cargas desnecessárias, é possível desabilitar a transição na última saída de atividade. Por exemplo, em uma saída de remessa, se nenhum processo estiver agendado, desmarque a opção relevante conforme mostrado abaixo:

   ![](assets/s_advuser_delivery_option_no_output.png)
