---
title: Sinal externo
seo-title: Sinal externo
description: Sinal externo
seo-description: null
page-status-flag: never-activated
uuid: dbe6624a-70cf-4ac4-adfd-bc72db9bb3f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 3739593f-056c-4165-87ef-63c812bd3c43
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Sinal externo{#external-signal}

A atividade **External signal** permite acionar a execução de um conjunto de tarefas em um workflow para uma agenda.

Quando uma tarefa &quot;External signal&quot; é ativada, ela é pausada indefinidamente ou até o final do período de tempo especificado. Sua transição é ativada pela chamada SOAP **PostEvent(sessionToken, workflowId, atividade, transição, parâmetros, complete).** O **[!UICONTROL complete]** parâmetro permite que a tarefa seja concluída, de modo que não reagirá às chamadas subsequentes.

Consulte a documentação online sobre chamadas SOAP para obter mais informações sobre a função PostEvent.

É possível configurar essa atividade para definir eventos se nenhum sinal for 
        recebido. To do this, edit the activity and click the **[!UICONTROL Expiration]** tab. Click the **[!UICONTROL Insert]** button to create and configure an event.

![](assets/edit_signal.png)

The configuration of expirations is detailed in [Expirations](../../workflow/using/executing-a-workflow.md#expirations).

O campo **Delay** permite especificar um atraso de expiração nas unidades de sua escolha. Consulte [Aguardar](../../workflow/using/wait.md).

Cada linha representa um tipo de expiração e coincides com uma transição.

![](assets/external_sign_diag.png)

