---
product: campaign
title: Usar uma tabela externa de recipient
description: Usar uma tabela externa de recipient
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 100%

---

# Usar uma tabela externa de recipient{#using-an-external-recipient-table}

![](../../assets/common.svg)

Se a tabela do delivery for uma tabela externa, você precisará fazer configurações adicionais. O schema **[!UICONTROL nms:seedmember]** deve ser estendido. Uma guia é adicionada aos seed addresses para definir os campos adequados, como mostrado abaixo:

![](assets/s_ncs_user_seedlist_new_tab.png)

Nesse caso, para adicionar seed addresses ao delivery, insira os campos adequados diretamente na guia correspondente ou importe os templates de endereços:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

A extensão de schema **nms:seedMember** está [nesta seção](../../configuration/using/seed-addresses.md).
