---
product: campaign
title: Problemas de logs de rastreamento
description: Problemas de logs de rastreamento
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
TQID: https://experienceleague.adobe.com/9u8xqAINLPKmeptZOZf94Ms-GiEciCL4nFBaw7SjRss
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 81
ht-degree: 32%

---

# Problemas de logs de rastreamento{#tracking-logs-issues}



Pode haver vários motivos para os logs de rastreamento não serem encaminhados. Recomendamos que você verifique as seguintes informações:

* **O fluxo de trabalho** Rastreamento **contém erros?**

Consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-technical-workflows.html?lang=pt-BR){target="_blank"}.

![](assets/tracking_scheduled_task.png)

* **O módulo** trackinglogd **está em execução no servidor?**

  Consulte [Arquivos de log](../../production/using/log-files.md).

* **Foram feitas alterações?**

  Eles podem acionar uma perda de conexão com os servidores usando o alias de rastreamento.
