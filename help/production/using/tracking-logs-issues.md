---
title: Problemas de logs de rastreamento
seo-title: Problemas de logs de rastreamento
description: Problemas de logs de rastreamento
seo-description: null
page-status-flag: never-activated
uuid: 996869c4-7ffe-4fcc-9555-1d8b65e93e87
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 1b9ff479-4847-408d-a5c2-9a164805081f
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 16%

---


# Problemas de logs de rastreamento{#tracking-logs-issues}

Pode haver vários motivos para logs de rastreamento não serem encaminhados. Recomendamos que você verifique as seguintes informações:

* O fluxo de trabalho de **rastreamento** apresenta erros?

   Consulte [Monitorando workflows técnicos](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* O módulo **trackinglogd** está sendo executado no servidor?

   Consulte [Registrar arquivos](../../production/using/log-files.md).

* Foram feitas mudanças? Eles podem acionar uma perda de conexão com os servidores usando o alias de rastreamento.

