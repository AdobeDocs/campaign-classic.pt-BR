---
product: campaign
title: Atualização do console
description: Atualização do console
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---

# Atualização do console{#console-update}



Se você selecionou a variável **[!UICONTROL Do not request console update]** e você deseja reativar a solicitação de atualização, aplique o seguinte procedimento:

1. Abra o editor do banco de dados do Registro usando o **regedit** no Windows **[!UICONTROL Start > Execute]** menu.

   ![](assets/ncs_console_update_1.png)

1. Na árvore, exiba as opções da variável **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** nó .
1. Exclua o **[!UICONTROL confAdvisedUpgrade]** entre e feche o editor do Registro.

   ![](assets/ncs_console_update_2.png)
