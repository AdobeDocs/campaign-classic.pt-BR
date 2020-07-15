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
source-git-commit: 9f55a2014546ce08972f51e4930ce04d4ce0c188
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 84%

---


# Sub-workflow{#sub-workflow}

A atividade **[!UICONTROL Sub-workflow]** permite acionar a execução de outro fluxo de trabalho e recuperar o resultado. Essa atividade permite usar workflows complexos ao usar uma interface simplificada.

Você pode chamar vários sub-workflows em um único workflow. Os Sub-workflows são executados de forma síncrona.

No exemplo abaixo, um fluxo de trabalho principal está chamando um subfluxo de trabalho usando saltos. Para obter mais informações sobre objetos gráficos do tipo salto, consulte [esta seção](../../workflow/using/jump--start-point-and-end-point-.md).

1. Crie um fluxo de trabalho que será usado como um subfluxo de trabalho em outro fluxo de trabalho.
1. Insira uma atividade **[!UICONTROL Jump (end point)]** com prioridade 1 no início do fluxo de trabalho. Se você tiver vários saltos do tipo &quot;ponto final&quot;, o Adobe Campaign usará o salto &quot;ponto final&quot; com o número mais baixo.
1. Insira uma atividade **[!UICONTROL Jump (start point)]** com prioridade 2 no fim do fluxo de trabalho. Se você tiver vários saltos do tipo &quot;ponto inicial&quot;, o Adobe Campaign usará o salto &quot;ponto inicial&quot; com o número mais alto.

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >Se a atividade do subfluxo de trabalho referenciar um fluxo de trabalho com várias atividades, **[!UICONTROL Jump]** o subfluxo de trabalho será executado entre o salto do tipo &quot;ponto final&quot; com o número mais baixo e o tipo do &quot;ponto inicial&quot; com o número mais alto.
   >
   >Para que o subfluxo de trabalho seja executado corretamente, você deve ter apenas um salto do tipo &quot;ponto final&quot; com o número mais baixo e apenas um salto do tipo &quot;ponto inicial&quot; com o número mais alto.

1. Complete e salve este &quot;sub-workflow&quot;.
1. Crie um fluxo de trabalho principal.
1. Insira uma atividade **[!UICONTROL Sub-workflow]** e abra-a.
1. Selecione o fluxo de trabalho que deseja usar na lista suspensa **[!UICONTROL Workflow template]**.

   ![](assets/subworkflow_selection.png)

1. Também é possível adicionar um script de configuração para alterar o fluxo de trabalho referenciado.
1. Clique em **[!UICONTROL Ok]**. Automaticamente, ele cria uma transição de saída com o rótulo da atividade **[!UICONTROL Jump (start point)]** do fluxo de trabalho selecionado.

   ![](assets/subworkflow_outbound.png)

1. Execute o fluxo de trabalho.

Once run, the workflow that was called as a sub-workflow remains in **[!UICONTROL Being edited]** status, which means the following:

* Você não pode clicar com o botão direito do mouse nas transições para exibir o target.
* A contagem de públicos intermediários não pode ser exibida.
* Os registros do subfluxo de trabalho são exibidos no fluxo de trabalho principal.

   ![](assets/subworkflow_logs.png)

>[!NOTE]
>
>Se ocorrer algum erro no subfluxo de trabalho, o fluxo de trabalho principal será pausado e uma cópia do subfluxo de trabalho será criada.

## Parâmetros de entrada (opcional) {#input-parameters--optional-}

* tableName
* schema

Cada evento de entrada deve especificar um target definido por esses parâmetros.

## Parâmetros de output {#output-parameters}

* tableName
* schema
* recCount

Esse conjunto de três valores identifica o público alvo do query. **[!UICONTROL tableName]** é o nome da tabela que registra os identificadores de target, **[!UICONTROL schema]** é o schema do público (normalmente nms:recipient) e **[!UICONTROL recCount]** é o número de elementos na tabela.

* targetSchema: Este valor é o schema da tabela de trabalho. Esse parâmetro é válido para todas as transições com **[!UICONTROL tableName]** e **[!UICONTROL schema]**.
