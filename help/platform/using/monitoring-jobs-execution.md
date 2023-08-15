---
product: campaign
title: Monitoramento da execução de processos
description: Saiba como monitorar a execução de processos de importação e exportação
feature: Monitoring
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 415c5137-2eb0-4581-a46e-26e8e3d264fa
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 100%

---

# Monitorar execução de trabalhos {#monitoring-job-execution}



É possível rastrear a execução de trabalhos de importação e exportação diretamente na lista de trabalhos de importação/exportação.

![](assets/s_ncs_user_export_list_and_details.png)

* A guia **[!UICONTROL Journal]** permite visualizar mensagens de log relacionadas à execução.
* A guia **[!UICONTROL Rejects]** contém os registros rejeitados. Consulte [esta seção](../../platform/using/executing-import-jobs.md#behavior-in-the-event-of-an-error).

Na guia **[!UICONTROL General]**, o campo **[!UICONTROL Status]** indica o status atual de um trabalho.

Cada status é representado por um ícone e rótulo especiais. Os status e seus ícones estão listados abaixo:

![](assets/s_ncs_user_export_status.png)

* **Edição em progresso**

  A tarefa está sendo criada.

* **Execução em progresso**

  A tarefa está sendo executada.

* **Cancelar**

  Clique no botão **[!UICONTROL Cancel]**: a tarefa em andamento é cancelada.

* **Cancelamento em progresso**

  O comando de cancelamento foi considerado e a tarefa está sendo cancelada.

* **Pausa em progresso**

  Clique em **[!UICONTROL Pause]**: a tarefa está sendo suspensa.

* **Em pausa**

  Clique em **[!UICONTROL Pause]**: a tarefa é suspensa. Ele pode ser reiniciado clicando em **[!UICONTROL Start]**.

* **Concluído**

  A execução do trabalho foi concluída.

* **Concluído com erro**

  O trabalho não foi executado devido a um erro técnico.

* **Desligamento do servidor em progresso**

  A tarefa em andamento foi interrompida porque o servidor do Adobe Campaign foi desligado.
