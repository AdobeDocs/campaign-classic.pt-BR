---
solution: Campaign Classic
product: campaign
title: Problemas de logs de rastreamento
description: Problemas de logs de rastreamento
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: f24642223a2ec9f3d8e78e2f7e71a55bf14b80c7
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---


# Problemas de logs de rastreamento{#tracking-logs-issues}

Pode haver vários motivos para logs de rastreamento não serem encaminhados. Recomendamos que você verifique as seguintes informações:

* **O fluxo de trabalho do****rastreamento apresenta erros?**

   Consulte [workflows técnicos de monitoramento](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* **O módulo****trackinglogdroning está no servidor?**

   Consulte [Arquivos de registro](../../production/using/log-files.md).

* **Foram feitas mudanças?**

   Eles podem acionar uma perda de conexão com os servidores usando o alias de rastreamento.
