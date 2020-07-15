---
title: Agendador
seo-title: Agendador
description: Agendador
seo-description: null
page-status-flag: never-activated
uuid: e814b978-2edd-442e-9334-9633bc9ec63a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 093dbe8a-494f-4fe7-8614-3bf58486e34c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 23629289ac5da3f9bef01f50c452f7c761a6fa44
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 77%

---


# Agendador {#scheduler}

O **Scheduler** é uma tarefa persistente que ativa sua transição nos momentos especificados por seu cronograma.

A atividade **[!UICONTROL Scheduler]** deve ser considerada como um início agendado. As regras de posicionamento de atividades no gráfico são iguais para a atividade **[!UICONTROL Start]**. Esta atividade não deve ter uma transição de entrada.

## Práticas recomendadas {#best-practices}

* Não agende a execução de um fluxo de trabalho a cada 15 minutos, pois isso pode impedir o desempenho geral do sistema e criar blocos no banco de dados.

* Nunca use mais de uma **[!UICONTROL Scheduler]** atividade por ramificação em um fluxo de trabalho. Consulte [Uso do atividade](../../workflow/using/workflow-best-practices.md#using-activities).

* O uso de uma atividade do programador pode levar a várias execuções ao mesmo tempo de um workflow em andamento. Por exemplo, você pode ter um scheduler acionando a execução do workflow a cada hora, mas, às vezes, a execução do workflow inteiro demora mais de uma hora.

   Talvez você queira ignorar a execução se o workflow já estiver em execução. Para obter mais informações sobre como evitar execuções simultâneas de um workflow, consulte [esta página](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions).

* Observe que a transição pode ser ativada várias horas depois se o fluxo de trabalho estiver executando uma tarefa de longo prazo, como uma importação, ou se o módulo do servidor tiver sido interrompido por um tempo. Nesse caso, pode ser necessário restringir a execução da tarefa ativada pelo agendador para um determinado intervalo de tempo.

## Configuring the Scheduler activity {#configuring-scheduler-activity}

O scheduler define o agendamento de ativação da transição. Para configurá-lo, clique duas vezes no objeto gráfico e clique em **[!UICONTROL Change...]**

![](assets/s_user_segmentation_scheduler.png)

Um assistente permite definir a frequência e o período de validade da atividade. As etapas de configuração são as seguintes:

1. Selecione a frequência de ativação e clique em **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_scheduler2.png)

1. Forneça os dias e horas de ativação. Os parâmetros desta etapa dependem da frequência selecionada na etapa anterior. Se optar iniciar a atividade várias vezes por dia, as opções de configuração serão as seguintes:

   ![](assets/s_user_segmentation_scheduler3.png)

1. Defina o período de validade do agendamento ou especifique quantas vezes será executado.

   ![](assets/s_user_segmentation_scheduler4.png)

1. Verifique a configuração e clique em **[!UICONTROL Finish]** para salvar.

   ![](assets/s_user_segmentation_scheduler5.png)
