---
product: campaign
title: Coordenar atualizações de dados
description: Coordenar atualizações de dados
feature: Workflows, Data Management
hide: true
exl-id: 9959e22e-9aa0-410f-b22c-9ca1cac46b97
TQID: https://experienceleague.adobe.com/G82StaXeELHRHF4C1qMnRK0IekJoF0n-r6xQi63KPlk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 301
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
