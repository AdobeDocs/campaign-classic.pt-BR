---
product: campaign
title: Problemas de logs de rastreamento
description: Problemas de logs de rastreamento
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 14%

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
