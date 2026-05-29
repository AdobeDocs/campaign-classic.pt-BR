---
product: campaign
title: Monitoramento da execução de processos
description: Saiba como monitorar a execução de processos de importação e exportação
feature: Monitoring
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 415c5137-2eb0-4581-a46e-26e8e3d264fa
TQID: https://experienceleague.adobe.com/g25R2WVJ2ULkITvhyNbvq87lxMdUNaHDJdm9rZNg-PA
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: afa4204e-6d08-4e29-bc35-26aafb656d48
subfeature_v2: id: f529d0bd-1401-4c88-9833-43228cc1d40fid: d6330382-c886-4f7a-a4f7-74e3f36c0d9cid: f5293531-9312-4099-bfa3-9e67df6a8750id: efa38731-2723-4334-8d8b-a778af834835
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 193
ht-degree: 100%

---

# Monitorar execução de processos {#monitoring-job-execution}



É possível rastrear a execução de processos de importação e exportação diretamente na lista de processos de importação/exportação.

![](assets/s_ncs_user_export_list_and_details.png)

* A guia **[!UICONTROL Journal]** permite visualizar mensagens de log relacionadas à execução.
* A guia **[!UICONTROL Rejects]** contém os registros rejeitados. Consulte [esta seção](../../platform/using/executing-import-jobs.md#behavior-in-the-event-of-an-error).

Na guia **[!UICONTROL General]**, o campo **[!UICONTROL Status]** indica o status atual de um processo.

Cada status é representado por um ícone e rótulo especiais. Os status e seus ícones estão listados abaixo:

![](assets/s_ncs_user_export_status.png)

* **Edição em progresso**

  O processo está sendo criado.

* **Execução em progresso**

  O processo está sendo executado.

* **Cancelar**

  Clique no botão **[!UICONTROL Cancel]**: o processo em andamento é cancelado.

* **Cancelamento em progresso**

  O comando de cancelamento foi considerado e o processo está sendo cancelado.

* **Pausa em progresso**

  Clique em **[!UICONTROL Pause]**: o processo está sendo suspenso.

* **Em pausa**

  Clique em **[!UICONTROL Pause]**: o processo é suspenso. Ele pode ser reiniciado clicando em **[!UICONTROL Start]**.

* **Concluído**

  A execução do processo foi concluída.

* **Concluído com erro**

  O processo não foi executado devido a um erro técnico.

* **Desligamento do servidor em progresso**

  O processo em andamento foi interrompido porque o servidor do Adobe Campaign foi desligado.
