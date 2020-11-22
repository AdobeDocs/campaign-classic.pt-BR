---
solution: Campaign Classic
product: campaign
title: Problemas de logs de rastreamento
description: Problemas de logs de rastreamento
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---


# Problemas de logs de rastreamento{#tracking-logs-issues}

Pode haver vários motivos para logs de rastreamento não serem encaminhados. Recomendamos que você verifique as seguintes informações:

* O fluxo de trabalho de **rastreamento** apresenta erros?

   Consulte [Monitorando workflows técnicos](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* O módulo **trackinglogd** está sendo executado no servidor?

   Consulte [Registrar arquivos](../../production/using/log-files.md).

* Foram feitas mudanças? Eles podem acionar uma perda de conexão com os servidores usando o alias de rastreamento.

