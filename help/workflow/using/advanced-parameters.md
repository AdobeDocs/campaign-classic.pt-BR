---
title: Parâmetros avançados
seo-title: Parâmetros avançados
description: Parâmetros avançados
seo-description: null
page-status-flag: never-activated
uuid: 9453d291-921b-4a03-80d1-2c8295f9a986
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: f66f1ff5-3601-4eb8-b05d-6f99164890ae
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Parâmetros avançados{#advanced-parameters}

The properties screen of an activity has an **[!UICONTROL Advanced]** tab that lets you define a behavior in case of errors, the execution period for the activity; and lets you enter an initialization script. Há duas versões dessa aba:

* uma versão simplificada (para **[!UICONTROL Start]** **[!UICONTROL End]** atividades e atividades, por exemplo)

   ![](assets/wf-advanced-basic.png)

* a more detailed version (for the **[!UICONTROL Query]** activity, for instance)

   ![](assets/wf-advanced-full.png)

The fields to be entered in the **[!UICONTROL Advanced]** tab are detailed in the following sections.

## Nome {#name}

Este campo contém o nome interno da atividade.

## Imagem {#image}

Este campo permite alterar a imagem vinculada a uma atividade. For more on this, refer to: [Managing activity images](../../workflow/using/managing-activity-images.md).

## Execução {#execution}

Este campo permite que você defina a ação a ser executada quando a tarefa for acionada. Há três opções possíveis:

Geralmente, essas opções são selecionadas no carrinho clicando com o botão direito do mouse na atividade.

* **[!UICONTROL Normal]**: a atividade é executada como de costume.
* **[!UICONTROL Do not activate]**: esta tarefa e todas as tarefas a seguir (no mesmo ramo) não são executadas.
* **[!UICONTROL Activate but do not execute]**: esta tarefa e todas as tarefas a seguir (na mesma ramificação) são automaticamente interrompidas. Isso pode ser útil se você quiser que esteja lá quando a tarefa for iniciada. To execute the task manually, right-click the activity and select **[!UICONTROL Normal execution]**.

## Afinidade {#affinity}

Este campo permite que você force a execução de uma atividade em uma máquina específica. For more on this, refer to: [Managing propensity](../../workflow/using/managing-propensity.md).

## Max. período de execução {#max--execution-period}

Este campo permite que você defina um aviso para quando a tarefa demorar muito. Ele não afetará a operação do workflow. If the task isn&#39;t finished by the time the **[!UICONTROL Max. execution period]** is over, the **[!UICONTROL Instance monitoring]** page will show a warning for this workflow. This page is accessed via the **[!UICONTROL Monitoring]** tab of the home page.

## Comportamento {#behavior}

Este campo permite que você defina o comportamento a ser aplicado para usar tarefas assíncronas. Há duas opções possíveis:

* **[!UICONTROL Several tasks authorized]**: várias tarefas podem ser executadas de uma vez, mesmo se a primeira não estiver concluída.
* **[!UICONTROL The current task has priority]**: as tarefas em andamento têm prioridade. Enquanto uma tarefa estiver em andamento, nenhuma outra tarefa será executada.

## Fuso horário {#time-zone}

Este campo permite selecionar o fuso horário da atividade. Para obter mais informações: [Gerenciando fusos horários](../../workflow/using/managing-time-zones.md).

## No caso de erros {#in-case-of-errors}

Este campo permite que você defina a ação a ser executada quando a atividade tiver erros. Há duas opções possíveis:

* **[!UICONTROL Stop the process]**: o fluxo de trabalho é interrompido automaticamente. Seu status muda para **[!UICONTROL Failed]**. Depois que o problema for resolvido, reinicie o workflow.
* **[!UICONTROL Ignore]**: esta tarefa e todas as tarefas a seguir (na mesma ramificação) não são executadas. Pode ser útil para tarefas recorrentes. Se a ramificação tiver um programador a montante, ele será iniciado como de costume na próxima data de execução.

## Script de inicialização {#initialization-script}

Este campo permite inicializar variáveis ou modificar propriedades da atividade. Para obter mais informações, consulte: scripts e modelos [JavaScript](../../workflow/using/javascript-scripts-and-templates.md).

## Comentário {#comment}

The **[!UICONTROL Comment]** field is a free field that lets you add a description.
