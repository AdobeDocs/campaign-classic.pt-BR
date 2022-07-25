---
product: campaign
title: Sinal externo
description: Saiba mais sobre a atividade de workflow de sinal externo
feature: Workflows
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Sinal externo{#external-signal}

![](../../assets/v7-only.svg)

A atividade **External signal** permite acionar a execução de um conjunto de tarefas em um workflow para uma agenda.

Quando uma tarefa &quot;External signal&quot; é ativada, ela é pausada indefinidamente ou até o final do período de tempo especificado. Sua transição é ativada pela chamada SOAP **PostEvent(sessionToken, workflowId, activity, transition, parameters, complete).** O parâmetro **[!UICONTROL complete]** permite que a tarefa seja concluída, de modo que não reagirá às chamadas subsequentes.

Consulte a documentação online sobre chamadas SOAP para obter mais informações sobre a função PostEvent.

É possível configurar essa atividade para definir eventos se nenhum sinal for recebido. Para fazer isso, crie a atividade e clique na guia **[!UICONTROL Expiration]**. Clique no botão **[!UICONTROL Insert]** para criar e configurar um evento.

![](assets/edit_signal.png)

A configuração das expirações é apresentada em [Expirations](defining-approvals.md).

O campo **Delay** permite especificar um atraso de expiração nas unidades de sua escolha. Consulte [Wait](wait.md).

Cada linha representa um tipo de expiração e coincides com uma transição.

![](assets/external_sign_diag.png)
