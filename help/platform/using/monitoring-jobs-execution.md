---
solution: Campaign Classic
product: campaign
title: Monitoramento da execução de trabalhos
description: Saiba como monitorar a execução de trabalhos de importação e exportação.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 100%

---


# Monitoramento da execução de trabalhos {#monitoring-job-execution}

É possível rastrear a execução de trabalhos de importação e exportação diretamente na lista de trabalhos de importação/exportação.

![](assets/s_ncs_user_export_list_and_details.png)

* A guia **[!UICONTROL Journal]** permite visualizar mensagens de log relacionadas à execução.
* A guia **[!UICONTROL Rejects]** contém os registros rejeitados. Consulte o [Comportamento no caso de um erro](../../platform/using/executing-import-jobs.md#behavior-in-the-event-of-an-error)

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
