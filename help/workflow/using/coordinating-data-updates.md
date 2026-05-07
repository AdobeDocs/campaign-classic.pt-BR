---
product: campaign
title: Coordenar atualizações de dados
description: Coordenar atualizações de dados
feature: Workflows, Data Management
hide: true
exl-id: 9959e22e-9aa0-410f-b22c-9ca1cac46b97
source-git-commit: 720a5f4edf534788f7fd143a476c25e58a6f1586
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 100%

---

# Coordenar atualizações de dados{#coordinating-data-updates}



Esse caso de uso detalha a criação de um fluxo de trabalho que permite gerenciar atualizações relacionadas ao usar várias execuções de um fluxo de trabalho.

O objetivo é verificar se o processo de atualização terminou antes de executar outra operação de atualização. Para fazer isso, vamos configurar uma variável de instância e permitir que o fluxo de trabalho teste, se a instância estiver em execução, decidir se continua ou não a execução do fluxo de trabalho e realizar a atualização.

![](assets/uc_dataupdate_wkf.png)

Este fluxo de trabalho é composto por:

* Uma atividade do **Scheduler**, que executa o fluxo de trabalho em uma frequência específica.
* Uma atividade **Test** que verifica se o fluxo de trabalho já está em execução.
* Atividades **Query** e **Update data** caso o fluxo de trabalho ainda não estiver em execução, seguido por uma atividade **End** que reinicializa a variável de instância do fluxo de trabalho para falso.
* Uma atividade **End** se o fluxo de trabalho já estiver em execução.

Para criar o fluxo de trabalho, siga as etapas abaixo:

1. Adicione uma atividade do **Scheduler** e configure sua frequência de acordo com suas necessidades.
1. Adicione uma atividade **Test** para verificar se o fluxo de trabalho já está em execução, depois a configure como apresentado abaixo.

   >[!NOTE]
   >
   >&quot;isRunning&quot; é o nome da variável de instância que escolhemos para este exemplo. Essa não é uma variável interna.

   ![](assets/uc_dataupdate_test.png)

1. Adicione uma atividade **End** à bifurcação **No.** Dessa forma, nada será executado se o fluxo de trabalho já estiver em execução.
1. Adicione as atividades desejadas à bifurcação **Yes.** Em nosso caso, as atividades **Query** e **Update Data**.
1. Abra a primeira atividade e adicione o comando **instance.vars.isRunning = true** na guia **[!UICONTROL Advanced]**. Dessa forma, a variável de instância é definida como em execução.

   ![](assets/uc_dataupdate_query.png)

1. Adicione uma atividade **End** ao final da bifurcação **[!UICONTROL Yes]** e adicione o comando **instance.vars.isRunning = false** na guia **[!UICONTROL Advanced]**.

   Desta maneira, nenhuma ação será executada enquanto o fluxo de trabalho estiver em execução.

   ![](assets/uc_dataupdate_end.png)

**Tópicos relacionados:**

* [Evitar várias execuções simultâneas](monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [Atividade Atualizar dados](update-data.md)
