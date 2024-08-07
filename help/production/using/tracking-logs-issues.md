---
product: campaign
title: Problemas de logs de rastreamento
description: Problemas de logs de rastreamento
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---

# Problemas de logs de rastreamento{#tracking-logs-issues}



Pode haver vários motivos para os logs de rastreamento não serem encaminhados. Recomendamos que você verifique as seguintes informações:

* **O fluxo de trabalho** Rastreamento **contém erros?**

  Consulte [Monitoramento de workflows técnicos](../../workflow/using/monitoring-technical-workflows.md).

  ![](assets/tracking_scheduled_task.png)

* **O módulo** trackinglogd **está em execução no servidor?**

  Consulte [Arquivos de log](../../production/using/log-files.md).

* **Foram feitas alterações?**

  Eles podem acionar uma perda de conexão com os servidores usando o alias de rastreamento.
