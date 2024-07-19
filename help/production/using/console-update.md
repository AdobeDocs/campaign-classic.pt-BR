---
product: campaign
title: Atualização do console
description: Atualização do console
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---

# Atualização do console{#console-update}



Se você selecionou a opção **[!UICONTROL Do not request console update]** e deseja reativar a solicitação de atualização, execute o seguinte procedimento:

1. Abra o editor do banco de dados do Registro usando o comando **regedit** no menu **[!UICONTROL Start > Execute]** do Windows.

   ![](assets/ncs_console_update_1.png)

1. Na árvore, exiba as opções do nó **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]**.
1. Exclua a entrada **[!UICONTROL confAdvisedUpgrade]** e feche o editor do Registro.

   ![](assets/ncs_console_update_2.png)
