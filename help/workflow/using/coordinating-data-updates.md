---
solution: Campaign Classic
product: campaign
title: Coordenação das atualizações de dados
description: Coordenação das atualizações de dados
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 100%

---


# Coordenação das atualizações de dados{#coordinating-data-updates}

Esse caso de uso detalha a criação de um workflow que permite gerenciar atualizações relacionadas ao workflow ao usar várias execuções de um workflow.

O objetivo é verificar se o processo de atualização terminou antes de executar outra operação de atualização. Para fazer isso, vamos configurar uma variável de instância e permitir que o workflow teste, se a instância estiver em execução, decidir se continua ou não a execução do workflow e realizar a atualização.

![](assets/uc_dataupdate_wkf.png)

Este workflow é composto por:

* Uma atividade do **Scheduler**, que executa o workflow em uma frequência específica.
* Uma atividade **Test** que verifica se o workflow já está em execução.
* Atividades **Query** e **Udate data** caso o workflow ainda não estiver em execução, seguido por uma atividade **End** que reinicializa a variável de instância do workflow para falso.
* Uma atividade **End** se o workflow já estiver em execução.

Para criar o workflow, siga as etapas abaixo:

1. Adicione uma atividade do **Scheduler** e configure sua frequência de acordo com suas necessidades.
1. Adicione uma atividade **Test** para verificar se o workflow já está em execução, depois a configure como apresentado abaixo.

   >[!NOTE]
   >
   >&quot;isRunning&quot; é o nome da variável de instância que escolhemos para este exemplo. Essa não é uma variável interna.

   ![](assets/uc_dataupdate_test.png)

1. Adicione uma atividade **End** à bifurcação **No.** Dessa forma, nada será executado se o workflow já estiver em execução.
1. Adicione as atividades desejadas à bifurcação **Yes.** Em nosso caso, as atividades **Query** e **Update Data**.
1. Abra a primeira atividade e adicione o comando **instance.vars.isRunning = true** na guia **[!UICONTROL Advanced]**. Dessa forma, a variável de instância é definida como em execução.

   ![](assets/uc_dataupdate_query.png)

1. Adicione uma atividade **End** ao final da bifurcação **[!UICONTROL Yes]** e adicione o comando **instance.vars.isRunning = false** na guia **[!UICONTROL Advanced]**.

   Desta maneira, nenhuma ação será executada enquanto o workflow estiver em execução.

   ![](assets/uc_dataupdate_end.png)

**Tópicos relacionados:**

* [Evitando várias execuções simultâneas](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [Atividade de atualização de dados](../../workflow/using/update-data.md)

