---
product: campaign
title: Problemas de logs de rastreamento
description: Problemas de logs de rastreamento
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '76'
ht-degree: 21%

---

# Problemas de logs de rastreamento{#tracking-logs-issues}



Pode haver vários motivos para os logs de rastreamento não serem encaminhados. Recomendamos que você verifique as seguintes informações:

* **O faz** Rastreamento **o fluxo de trabalho contém erros?**

  Consulte [Monitoramento de workflows técnicos](../../workflow/using/monitoring-technical-workflows.md).

  ![](assets/tracking_scheduled_task.png)

* **É o módulo** trackinglogd **em execução no servidor?**

  Consulte [Arquivos de log](../../production/using/log-files.md).

* **Foram feitas alterações?**

  Eles podem acionar uma perda de conexão com os servidores usando o alias de rastreamento.
