---
title: Atualização do console
seo-title: Atualização do console
description: Atualização do console
seo-description: null
page-status-flag: never-activated
uuid: d2193d4f-b98c-47b1-88f1-7e5ccf4c453c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 9281808b-1c2f-4095-9051-f181f089f205
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Atualização do console{#console-update}

Se você selecionou a **[!UICONTROL Do not request console update]** opção e deseja reativar a solicitação de atualização, aplique o seguinte procedimento:

1. Abra o editor do banco de dados do Registro usando o comando **regedit** no menu do Windows **[!UICONTROL Start > Execute]** .

   ![](assets/ncs_console_update_1.png)

1. Na árvore, exiba as opções do **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** nó.
1. Exclua a **[!UICONTROL confAdvisedUpgrade]** entrada e feche o editor do Registro.

   ![](assets/ncs_console_update_2.png)

