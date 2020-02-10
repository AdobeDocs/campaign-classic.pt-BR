---
title: Problemas de registro de rastreamento
seo-title: Problemas de registro de rastreamento
description: Problemas de registro de rastreamento
seo-description: null
page-status-flag: never-activated
uuid: 996869c4-7ffe-4fcc-9555-1d8b65e93e87
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 1b9ff479-4847-408d-a5c2-9a164805081f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e1937c1ddcbde092a22f4fe8c50d3d72b02cfeed

---


# Problemas de registro de rastreamento{#tracking-logs-issues}

Pode haver vários motivos para os logs de rastreamento não serem encaminhados. Recomendamos que você verifique as seguintes informações:

* O fluxo de trabalho de **rastreamento** apresenta erros?

   Consulte [Monitoramento de fluxos de trabalho](../../workflow/using/monitoring-technical-workflows.md)técnicos.

   ![](assets/tracking_scheduled_task.png)

* O módulo **trackinglogd** está sendo executado no servidor?

   Consulte [Registrar arquivos](../../production/using/log-files.md).

* Foram feitas mudanças? Eles podem acionar uma perda de conexão com os servidores usando o alias de rastreamento.

