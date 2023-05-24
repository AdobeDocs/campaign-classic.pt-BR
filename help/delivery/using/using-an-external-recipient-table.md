---
product: campaign
title: Usar uma tabela externa de recipient
description: Usar uma tabela externa de recipient
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 100%

---

# Usar uma tabela externa de recipient{#using-an-external-recipient-table}



Se a tabela do delivery for uma tabela externa, você precisará fazer configurações adicionais. O schema **[!UICONTROL nms:seedmember]** deve ser estendido. Uma guia é adicionada aos seed addresses para definir os campos adequados, como mostrado abaixo:

![](assets/s_ncs_user_seedlist_new_tab.png)

Nesse caso, para adicionar seed addresses ao delivery, insira os campos adequados diretamente na guia correspondente ou importe os templates de endereços:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

A extensão de schema **nms:seedMember** está [nesta seção](../../configuration/using/seed-addresses.md).
