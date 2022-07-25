---
product: campaign
title: Sub-workflow
description: Saiba mais sobre a atividade de sub-workflow
feature: Workflows
exl-id: bc64ca11-2c50-4896-b6c6-ae42c0315924
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: ht
source-wordcount: '417'
ht-degree: 100%

---

# Sub-workflow{#sub-workflow}

![](../../assets/v7-only.svg)

A atividade **[!UICONTROL Sub-workflow]** permite acionar a execução de outro workflow e recuperar o resultado. Essa atividade permite usar workflows complexos ao usar uma interface simplificada.

Você pode chamar vários sub-workflows em um único workflow. Os Sub-workflows são executados de forma síncrona.

No exemplo abaixo, um workflow chama um subworkflow por meio de saltos. Para obter mais informações sobre objetos gráficos do tipo salto, consulte [esta seção](jump--start-point-and-end-point-.md).

1. Crie um workflow que será usado como um subworkflow em outro workflow.
1. Insira uma atividade **[!UICONTROL Jump (end point)]** com prioridade 1 no início do workflow. Se você tiver vários saltos do tipo &quot;ponto final&quot;, o Adobe Campaign usará o salto &quot;ponto final&quot; com o número mais baixo.
1. Insira uma atividade **[!UICONTROL Jump (start point)]** com prioridade 2 no fim do workflow. Se você tiver vários saltos do tipo &quot;ponto inicial&quot;, o Adobe Campaign usará o salto &quot;ponto inicial&quot; com o número mais alto.

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >Se a atividade do subworkflow fizer referência a um workflow com várias atividades **[!UICONTROL Jump]**, o subworkflow será executado entre o salto tipo &quot;ponto final&quot; com o número mais baixo e o salto tipo &quot;ponto inicial&quot; com o número mais alto.
   >
   >Para que o subworkflow seja executado corretamente, você deve ter apenas um salto tipo &quot;ponto final&quot; com o número mais baixo e apenas um salto tipo &quot;ponto inicial&quot; com o número mais alto.

1. Complete e salve este &quot;subworkflow&quot;.
1. Crie um workflow principal.
1. Insira uma atividade **[!UICONTROL Sub-workflow]** e abra-a.
1. Selecione o workflow que deseja usar na lista suspensa **[!UICONTROL Workflow template]**.

   ![](assets/subworkflow_selection.png)

1. Também é possível adicionar um script de configuração para alterar o workflow referenciado.
1. Clique em **[!UICONTROL Ok]**. Uma transição de saída com o rótulo da atividade **[!UICONTROL Jump (start point)]** será criada automaticamente a partir do workflow selecionado.

   ![](assets/subworkflow_outbound.png)

1. Execute o workflow.

Uma vez executado, o workflow chamado como um subworkflow ainda estará com o status **[!UICONTROL Being edited]**, o que significa que:

* Você não pode clicar com o botão direito do mouse nas transições para exibir o target.
* A contagem de públicos intermediários não pode ser exibida.
* Os registros do subworkflow são exibidos no workflow principal.

   ![](assets/subworkflow_logs.png)

>[!NOTE]
>
>Se ocorrer algum erro no subworkflow, o workflow principal será pausado e uma cópia do subworkflow será criada.

## Parâmetros de entrada (opcional) {#input-parameters--optional-}

* tableName
* schema

Cada evento de entrada deve especificar um target definido por esses parâmetros.

## Parâmetros de saída {#output-parameters}

* tableName
* schema
* recCount

Esse conjunto de três valores identifica o público alvo do query. **[!UICONTROL tableName]** é o nome da tabela que registra os identificadores de target, **[!UICONTROL schema]** é o schema do público (normalmente nms:recipient) e **[!UICONTROL recCount]** é o número de elementos na tabela.

* targetSchema: Este valor é o schema da tabela de trabalho. Esse parâmetro é válido para todas as transições com **[!UICONTROL tableName]** e **[!UICONTROL schema]**.
