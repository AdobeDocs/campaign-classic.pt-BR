---
solution: Campaign Classic
product: campaign
title: Atualização do console
description: Atualização do console
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---


# Atualização do console{#console-update}

Se você selecionou a **[!UICONTROL Do not request console update]** opção e deseja reativar a solicitação de atualização, aplique o seguinte procedimento:

1. Abra o editor do banco de dados do Registro usando o comando **regedit** no menu do Windows **[!UICONTROL Start > Execute]** .

   ![](assets/ncs_console_update_1.png)

1. Na árvore, exiba as opções do **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** nó.
1. Exclua a **[!UICONTROL confAdvisedUpgrade]** entrada e feche o editor do Registro.

   ![](assets/ncs_console_update_2.png)

