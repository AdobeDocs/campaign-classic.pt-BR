---
product: campaign
title: Sinal externo
description: Saiba mais sobre a atividade de workflow de sinal externo
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: ht
source-wordcount: '168'
ht-degree: 100%

---

# Sinal externo{#external-signal}

A atividade **External signal** permite acionar a execução de um conjunto de tarefas em um workflow para uma agenda.

Quando uma tarefa &quot;External signal&quot; é ativada, ela é pausada indefinidamente ou até o final do período de tempo especificado. Sua transição é ativada pela chamada SOAP **PostEvent(sessionToken, workflowId, activity, transition, parameters, complete).** O parâmetro **[!UICONTROL complete]** permite que a tarefa seja concluída, de modo que não reagirá às chamadas subsequentes.

Consulte a documentação online sobre chamadas SOAP para obter mais informações sobre a função PostEvent.

É possível configurar essa atividade para definir eventos se nenhum sinal for recebido. Para fazer isso, crie a atividade e clique na guia **[!UICONTROL Expiration]**. Clique no botão **[!UICONTROL Insert]** para criar e configurar um evento.

![](assets/edit_signal.png)

A configuração das expirações é apresentada em [Expirations](../../workflow/using/defining-approvals.md).

O campo **Delay** permite especificar um atraso de expiração nas unidades de sua escolha. Consulte [Wait](../../workflow/using/wait.md).

Cada linha representa um tipo de expiração e coincides com uma transição.

![](assets/external_sign_diag.png)
