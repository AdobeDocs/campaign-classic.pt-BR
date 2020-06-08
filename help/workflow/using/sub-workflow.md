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
source-git-commit: b1a961822224ab0a9551f51942a5f94cf201c8ee
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 57%

---


# Sub-workflow{#sub-workflow}

A atividade **[!UICONTROL Sub-workflow]** permite acionar a execução de outro workflow e recuperar o resultado. Essa atividade permite usar workflows complexos ao usar uma interface simplificada.

Você pode chamar vários sub-workflows em um único workflow. Os Sub-workflows são executados de forma síncrona.

No exemplo abaixo, um fluxo de trabalho &quot;mestre&quot; está chamando um subfluxo de trabalho usando saltos. Para obter mais informações sobre objetos gráficos do tipo salto, consulte [esta seção](../../workflow/using/jump--start-point-and-end-point-.md).

1. Crie um workflow a ser usado como um sub-workflow em outro workflow.
1. Insert a **[!UICONTROL Jump (end point)]** activity with a priority of 1 at the beginning of the workflow. Se você tiver vários saltos do tipo &quot;ponto final&quot;, o Adobe Campaign usará o salto &quot;ponto final&quot; com o número mais baixo.
1. Insert a **[!UICONTROL Jump (start point)]** activity with a priority of 2 at the end of the workflow. Se você tiver vários saltos do tipo &quot;ponto de start&quot;, o Adobe Campaign usará o salto &quot;ponto de start&quot; com o número mais alto.

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >If the sub-workflow activity references a workflow with several **[!UICONTROL Jump]** activities, the sub-workflow is executed between the &quot;end point&quot; type jump with the lowest number and the &quot;start point&quot; type jump with the highest number.
   >
   >Para que o subfluxo de trabalho seja executado corretamente, você deve ter apenas um salto do tipo &quot;ponto final&quot; com o número mais baixo e apenas um salto do tipo &quot;ponto de start&quot; com o número mais alto.

1. Complete e salve este &quot;sub-workflow&quot;.
1. Crie um workflow principal.
1. Insira uma atividade **[!UICONTROL Sub-workflow]** e abra-a.
1. Selecione o workflow que deseja usar na lista suspensa **[!UICONTROL Workflow template]**.

   ![](assets/subworkflow_selection.png)

1. Também é possível adicionar um script de configuração para alterar o workflow referenciado.
1. Clique em **[!UICONTROL Ok]**. It will automatically create an outbound transition with the label of the **[!UICONTROL Jump (start point)]** activity from the selected workflow.

   ![](assets/subworkflow_outbound.png)

1. Execute o workflow.

Uma vez executado, o workflow chamado como sub-workflow ainda estará com o status **[!UICONTROL Being edited]**, o que significa:

* Você não pode clicar com o botão direito do mouse nas transições para exibir o target.
* A contagem de públicos intermediários não pode ser exibida.
* Os logs são agregados no workflow principal e são rotulados apenas como &quot;subworkflow&quot;.

De fato, este workflow é apenas um template. Um novo sub-workflow baseado nesse template é criado quando chamado pelo workflow principal.

## Parâmetros de entrada (opcional) {#input-parameters--optional-}

* tableName
* schema

Cada evento de entrada deve especificar um target definido por esses parâmetros.

## Parâmetros de output {#output-parameters}

* tableName
* schema
* recCount

Esse conjunto de três valores identifica o público alvo do query. **[!UICONTROL tableName]** é o nome da tabela que registra os identificadores de target, **[!UICONTROL schema]** é o schema do público (normalmente nms:recipient) e **[!UICONTROL recCount]** é o número de elementos na tabela.

* targetSchema: Esse valor é o schema da tabela de trabalho. Esse parâmetro é válido para todas as transições com **[!UICONTROL tableName]** e **[!UICONTROL schema]**.
