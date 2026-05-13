---
product: campaign
title: Atualização do console
description: Atualização do console
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
TQID: https://experienceleague.adobe.com/oNVXa9DaMu-b-GpfxT-Z0jFbWEd-MnsSzu8Jdb0S0Fw
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 55
ht-degree: 10%

---

# Atualização do console{#console-update}



Se você selecionou a opção **[!UICONTROL Do not request console update]** e deseja reativar a solicitação de atualização, execute o seguinte procedimento:

1. Abra o editor do banco de dados do Registro usando o comando **regedit** no menu **[!UICONTROL Start > Execute]** do Windows.

   ![](assets/ncs_console_update_1.png)

1. Na árvore, exiba as opções do nó **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]**.
1. Exclua a entrada **[!UICONTROL confAdvisedUpgrade]** e feche o editor do Registro.

   ![](assets/ncs_console_update_2.png)
