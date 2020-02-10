---
title: Sub-workflow
seo-title: Sub-workflow
description: Sub-workflow
seo-description: null
page-status-flag: never-activated
uuid: c952633f-1aca-44cf-bb50-a67e9b086030
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: a4441820-1b3d-4bac-a6e3-1c9c14466d19
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Sub-workflow{#sub-workflow}

The **[!UICONTROL Sub-workflow]** activity lets you trigger the execution of another workflow and recover the result. Essa atividade permite usar workflows complexos ao usar uma interface simplificada.

Você pode chamar vários sub-workflows em um único workflow. Os Sub-workflows são executados de forma síncrona.

>[!NOTE]
>
>Para que o sub-workflow seja executado corretamente, você deve ter apenas um 
          atalho de &quot;chegada&quot; com o número mais baixo e apenas um atalho de &quot;início&quot; com o 
          número mais alto. Por exemplo, se você tiver um atalho de &quot;início&quot; com uma prioridade 1, 2 e 
          3, você deverá ter apenas um atalho de &quot;início&quot; com uma prioridade 3.

1. Crie um workflow a ser usado como um sub-workflow em 
            outro workflow.
1. Insert a **[!UICONTROL Jump (end point)]** activity with a priority of 1 at the beginning of the workflow. Se você tiver vários atalhos de &quot;chegada&quot;, 
            o Adobe Campaign usará o atalho de &quot;chegada&quot; com o número mais baixo.

   Insert a **[!UICONTROL Jump (start point)]** activity with a priority of 2 at the end of the workflow. Se você tiver vários atalhos de &quot;início&quot;, 
            o Adobe Campaign usará o atalho &quot;inicial&quot; com o número mais alto.

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >If the sub-workflow activity references a workflow with several **[!UICONTROL Jump]** activities, the sub-workflow is executed between the &quot;arrival&quot; type jump with the lowest number and the &quot;start&quot; type jump with the highest number.

1. Complete e salve este &quot;sub-workflow&quot;.
1. Crie um workflow principal.
1. Insert a **[!UICONTROL Sub-workflow]** activity and open it.
1. Select the workflow that you want to use from the **[!UICONTROL Workflow template]** drop-down list.

   ![](assets/subworkflow_selection.png)

1. Também é possível adicionar um script de configuração para alterar o workflow referenciado.
1. Clique em **[!UICONTROL Ok]**. It will automatically create an outbound transition with the label of the **[!UICONTROL Jump (start point)]** activity from the selected workflow.

   ![](assets/subworkflow_outbound.png)

1. Execute o workflow.

Once run, the workflow that was called as a sub-workflow is still in **[!UICONTROL Being edited]** status, which means the following:

* Você não pode clicar com o botão direito do mouse nas transições para exibir o 
            target.
* A contagem de públicos intermediários não pode 
            ser exibida.
* Os logs são agregados no workflow principal e são 
            rotulados apenas como &quot;subworkflow&quot;.

De fato, este workflow é apenas um template. Um novo sub-workflow
        baseado nesse template é criado quando chamado pelo workflow principal.

## Parâmetros de entrada (opcional) {#input-parameters--optional-}

* tableName
* schema

Cada evento de entrada deve especificar um target definido por esses parâmetros.

## Parâmetros de output {#output-parameters}

* tableName
* schema
* recCount

Esse conjunto de três valores identifica o público alvo do query. **[!UICONTROL tableName]** é o nome da tabela que registra os identificadores de metas, **[!UICONTROL schema]** é o esquema da população (normalmente nms:customer) e **[!UICONTROL recCount]** é o número de elementos na tabela.

* targetSchema

Este valor é o schema da tabela de trabalho. This parameter is valid for all transitions with **[!UICONTROL tableName]** and **[!UICONTROL schema]**.
