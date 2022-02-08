---
product: campaign
title: Uso de uma tabela externa de recipient
description: Uso de uma tabela externa de recipient
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 100%

---

# Uso de uma tabela externa de recipient{#using-an-external-recipient-table}

![](../../assets/common.svg)

Se a tabela do delivery for uma tabela externa, você precisará fazer configurações adicionais. O schema **[!UICONTROL nms:seedmember]** deve ser estendido. Uma guia é adicionada aos seed addresses para definir os campos adequados, como mostrado abaixo:

![](assets/s_ncs_user_seedlist_new_tab.png)

Nesse caso, para adicionar seed addresses ao delivery, insira os campos adequados diretamente na guia correspondente ou importe os templates de endereços:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

A extensão de schema **nms:seedMember** está [nesta seção](../../configuration/using/seed-addresses.md).
