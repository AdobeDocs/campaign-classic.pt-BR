---
product: campaign
title: Scheduler
description: Saiba mais sobre a atividade de fluxo de trabalho Agendador
feature: Workflows
hide: true
exl-id: 30a9bd2a-afb1-481c-ab5f-5acebd9cbb5a
TQID: https://experienceleague.adobe.com/SQfzWYlYCgUZXRpV3FDQEeGEBneTZHr-iW55Cy6lBXk
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 335
ht-degree: 100%

---

# Scheduler {#scheduler}



O **Scheduler** é uma tarefa persistente que ativa a transição nos momentos especificados por seu cronograma.

A atividade **[!UICONTROL Scheduler]** deve ser considerada como um início agendado. As regras de posicionamento de atividades no gráfico são iguais para a atividade **[!UICONTROL Start]**. Esta atividade não deve ter uma transição de entrada.

## Práticas recomendadas {#best-practices}

* É recomendável não agendar um fluxo de trabalho para execução por mais de 15 minutos, pois pode atrapalhar o desempenho geral do sistema e criar bloqueios no banco de dados.

* Nunca use mais de uma atividade **[!UICONTROL Scheduler]** por ramificação em um fluxo de trabalho. Consulte [Uso de atividades](workflow-best-practices.md#using-activities).

* O uso de uma atividade do programador pode levar a várias execuções ao mesmo tempo de um fluxo de trabalho em andamento. Por exemplo, você pode ter um scheduler acionando a execução do fluxo de trabalho a cada hora, mas, às vezes, a execução do fluxo de trabalho inteiro demora mais de uma hora.

  Talvez você queira ignorar a execução se o fluxo de trabalho já estiver em execução. Para obter mais informações sobre como evitar execuções simultâneas de um fluxo de trabalho, consulte [esta página](monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions).

* Observe que a transição pode ser ativada várias horas depois caso o fluxo de trabalho esteja executando uma tarefa de longo prazo, como uma importação, ou se o módulo wfserver for interrompido por um momento. Nesse caso, pode ser necessário restringir a execução da tarefa ativada pelo scheduler para um determinado intervalo de tempo.

## Configuração de atividade do Scheduler {#configuring-scheduler-activity}

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
