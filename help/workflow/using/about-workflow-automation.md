---
product: campaign
title: Sobre workflows
description: Automatize processos com workflows, gerencie dados e públicos, envie mensagens e muito mais
feature: Workflows, Data Management
exl-id: 024a7344-9376-4ff3-926a-003148229f9f
source-git-commit: b353b562bd2f0b0bd2dfde22c6477ab66d499483
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 9%

---

# Automatizar com fluxos de trabalho {#gs-workflows}

Os fluxos de trabalho da Adobe Campaign permitem que sua equipe simplifique e automatize processos de negócios completos na plataforma. Com uma interface gráfica intuitiva, você pode projetar e gerenciar fluxos de trabalho que coordenam tarefas como segmentação de dados, execução de campanha, manuseio de arquivos e até mesmo aprovações de usuários — tudo em um só lugar.

Por exemplo, você pode automatizar um processo para recuperar um arquivo de um servidor remoto, extrair seu conteúdo e carregar facilmente os dados no servidor Adobe Campaign - reduzindo o esforço manual e aumentando a eficiência operacional. O motor de workflow garante que cada etapa seja executada de forma confiável e rastreada para visibilidade e controle.

>[!BEGINTABS]

>[!TAB Documentação do fluxo de trabalho]

Para saber mais sobre o gerenciamento de fluxos de trabalho, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html?lang=pt-BR){target=_blank}.


[![imagem](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html?lang=pt-BR){target=_blank}


>[!TAB Links úteis]

Saiba mais sobre as principais etapas relacionadas ao gerenciamento de fluxo de trabalho na documentação do Campaign v8:

* [Atividades do fluxo de trabalho](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/activities.html?lang=pt-BR){target=_blank}: uma atividade é um modelo de tarefa. Os fluxos de trabalho incluem atividades de direcionamento, controle de fluxo, ação e evento.

* [Criar um fluxo de trabalho](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html?lang=pt-BR){target=_blank}: saiba como criar e executar fluxos de trabalho de direcionamento, de campanha e técnicos.

* [Práticas recomendadas](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html?lang=pt-BR){target=_blank}: saiba mais sobre as diretrizes para otimizar o desempenho dos fluxos de trabalho do Campaign, melhorar o design dos fluxos de trabalho e definir as configurações corretas.

* [Monitorar fluxos de trabalho](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=pt-BR){target=_blank}: saiba como monitorar a execução do fluxo de trabalho para garantir que tudo esteja funcionando corretamente.

* [Casos de uso do fluxo de trabalho](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/workflow-use-cases.html?lang=pt-BR){target=_blank}: saiba mais sobre os contextos nos quais os fluxos de trabalho podem ser usados e como implementá-los em casos de uso completos.


>[!ENDTABS]





<!--

Adobe Campaign uses workflows to:

* Carry out targeting campaigns. [Learn more](building-a-workflow.md#implementation-steps-)
* Build campaigns: for each campaign, the **[!UICONTROL Workflow]** tab lets you build the target and create the deliveries. [Learn more](building-a-workflow.md#campaign-workflows)
* Perform technical processes: cleanup, collecting tracking information or provisional calculations. [Learn more](building-a-workflow.md#technical-workflows)

A workflow can mean both a process definition (the workflow model, which is a representation of what is supposed to happen) and an instance of this process (a workflow instance, which is a representation of what is actually happening).

The workflow template describes the various tasks to be performed and how they are linked together. The task templates are called activities and are represented by icons. They are linked together by transitions.

![](assets/example1.png)

Each workflow contains:

* **[!UICONTROL Activities]**

  An activity describes a task template. The various activities available are represented on the diagram by icons. Each type has common properties and specific properties. For example, while all activities have a name and label, only the **[!UICONTROL Approval]** activity has an assignment.

  In a workflow diagram, a given activity can produce multiple tasks, in particular when there is a loop or recurrent (periodic) actions.

  All workflow activities are listed in [this section](about-activities.md), including use cases and samples.

* **[!UICONTROL Transitions]**

  Transitions enable you to link activities and to define their sequence. A transition links a source activity to a destination activity. There are several sorts of transitions, which depend on the source activity. Some transitions have additional parameters such as a duration, a condition or a filter.

  A transition which is not linked to a destination activity is colored orange and the arrow head is shown as a diamond.

  >[!NOTE]
  >
  >A workflow containing unterminated transitions can still be executed: a warning message will be generated and the workflow will pause once it reaches the transition but it will not generate an error. It is thus possible to start a workflow without it being finished and to add to it as you go along.

  For more information about how to build a workflow, refer to [this section](building-a-workflow.md).

* **[!UICONTROL Worktables]**

  The worktable contains all the information carried by the transition. Each workflow uses several worktables. The data conveyed in these tables can be accelerated and used throughout the workflow's life cycle, as long as it is not purged. Indeed, unneeded tables are purged each time the workflow is passivated, and possibly during the execution of the largest workflows to avoid overloading the server.

  Learn more on workflow data and tables in [this section](how-to-use-workflow-data.md).

## Key principles and best practices{#principles-workflows}

Refer to these sections to find guidance and best practices to automate processes with workflows:

* Learn more about workflow activities in [this page](how-to-use-workflow-data.md).
* Learn how to build a workflow in [this section](building-a-workflow.md).
* Discover how to use workflows to import data in Campaign in [this section](../../platform/using/import-export-workflows.md).
* Workflow best practices are detailed in [this page](workflow-best-practices.md).
* Find guidance about workflow execution in [this section](starting-a-workflow.md).
* Learn how to monitor workflows in [this page](monitoring-workflow-execution.md).
* Learn how to grant access to users to use workflows in [this page](managing-rights.md).

-->