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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 88%

---


# Parâmetros avançados{#advanced-parameters}

A janela das propriedades de uma atividade tem uma guia **[!UICONTROL Advanced]** que permite a definição de um comportamento no caso de erros, o período de execução da atividade e a inserção de um script de inicialização. Há duas versões dessa aba:

* a simplified version (for **[!UICONTROL Start]** and **[!UICONTROL End]** activities for instance)

   ![](assets/wf-advanced-basic.png)

* uma versão mais detalhada (para a atividade de **[!UICONTROL Query]**, por exemplo)

   ![](assets/wf-advanced-full.png)

Os campos a serem inseridos na guia **[!UICONTROL Advanced]** estão detalhados nas seções a seguir.

## Nome {#name}

Este campo contém o nome interno da atividade.

## Imagem {#image}

Este campo permite alterar a imagem vinculada a uma atividade. Para obter mais informações, consulte [Gerenciamento de imagens de atividades](../../workflow/using/managing-activity-images.md).

## Execução {#execution}

Este campo permite que você defina a ação a ser executada quando a tarefa for acionada. Há três opções possíveis:

Geralmente, essas opções são selecionadas no carrinho clicando com o botão direito do mouse na atividade.

* **[!UICONTROL Normal]**: a atividade é executada como de costume.
* **[!UICONTROL Do not activate]**: esta tarefa e todas as tarefas a seguir (na mesma ramificação) não são executadas.
* **[!UICONTROL Activate but do not execute]**: esta tarefa e todas as tarefas a seguir (na mesma ramificação) são automaticamente interrompidas. Isso pode ser útil se você quiser que esteja lá quando a tarefa for iniciada. Para executar a tarefa manualmente, clique com o botão direito do mouse na atividade e selecione **[!UICONTROL Normal execution]**.

## Afinidade {#affinity}

Este campo permite que você force a execução de uma atividade em uma máquina específica. Para obter mais informações, consulte [Gerenciamento de tendências](../../workflow/using/managing-propensity.md).

## Max. período de execução {#max--execution-period}

Este campo permite que você defina um aviso para quando a tarefa demorar muito. Ele não afetará a operação do workflow. If the task isn&#39;t finished by the time the **[!UICONTROL Max. execution period]** is over, the **[!UICONTROL Instance monitoring]** page will show a warning for this workflow. Esta página é acessada pela guia **[!UICONTROL Monitoring]** da página inicial.

## Comportamento {#behavior}

Este campo permite que você defina o comportamento a ser aplicado para usar tarefas assíncronas. Há duas opções possíveis:

* **[!UICONTROL Several tasks authorized]**: várias tarefas podem ser executadas de uma vez, mesmo sem a conclusão da primeira.
* **[!UICONTROL The current task has priority]**: As tarefas em andamento têm prioridade. Enquanto uma tarefa estiver em andamento, nenhuma outra tarefa será executada.

## Fuso horário {#time-zone}

Este campo permite selecionar o fuso horário da atividade. Para obter mais informações: [Gerenciar fusos horários](../../workflow/using/managing-time-zones.md).

## No caso de erros {#in-case-of-errors}

Este campo permite que você defina a ação a ser executada quando a atividade tiver erros. Há duas opções possíveis:

* **[!UICONTROL Stop the process]**: o fluxo de trabalho é interrompido automaticamente. Seu status muda para **[!UICONTROL Failed]**. Depois que o problema for resolvido, reinicie o workflow.
* **[!UICONTROL Ignore]**: esta tarefa e todas as tarefas a seguir (na mesma ramificação) não serão executadas. Pode ser útil para tarefas recorrentes. Se a ramificação tiver um programador a montante, ele será iniciado como de costume na próxima data de execução.

## Script de inicialização {#initialization-script}

Este campo permite inicializar variáveis ou modificar propriedades da atividade. Para obter mais informações, consulte [Modelos e scripts JavaScript](../../workflow/using/javascript-scripts-and-templates.md).

## Comentário {#comment}

O campo **[!UICONTROL Comment]** é um campo livre que permite a adição de uma descrição.
