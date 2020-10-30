---
title: Uso de uma tabela externa de recipient
seo-title: Uso de uma tabela externa de recipient
description: Uso de uma tabela externa de recipient
seo-description: null
page-status-flag: never-activated
uuid: a6147425-14f0-41e8-a47f-3e7072deafa7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 92c32b2d-d8bf-41ab-9349-ef4a15f10521
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '88'
ht-degree: 100%

---


# Uso de uma tabela externa de recipient{#using-an-external-recipient-table}

Se a tabela do delivery for uma tabela externa, você precisará fazer configurações adicionais. O schema **[!UICONTROL nms:seedmember]** deve ser estendido. Uma guia é adicionada aos seed addresses para definir os campos adequados, como mostrado abaixo:

![](assets/s_ncs_user_seedlist_new_tab.png)

Nesse caso, para adicionar seed addresses ao delivery, insira os campos adequados diretamente na guia correspondente ou importe os templates de endereços:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

A extensão de schema **nms:seedMember** está [nesta seção](../../configuration/using/seed-addresses.md).
