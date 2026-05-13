---
product: campaign
title: Usar uma tabela externa de destinatário
description: Usar uma tabela externa de destinatário
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
TQID: https://experienceleague.adobe.com/Uq5yqNYkyDrFVtueUlkIOEC9XEUaYtBArNy8-t1rKAw
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 91
ht-degree: 92%

---

# Usar uma tabela externa de destinatário{#using-an-external-recipient-table}



Se a tabela da entrega for uma tabela externa, você precisará fazer configurações adicionais. O esquema **[!UICONTROL nms:seedmember]** deve ser estendido. Uma guia é adicionada aos seed addresses para definir os campos adequados, como mostrado abaixo:

![](assets/s_ncs_user_seedlist_new_tab.png)

Nesse caso, para adicionar seed addresses à entrega, insira os campos adequados diretamente na guia correspondente ou importe os modelos de endereços:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

A extensão de esquema **nms:seedMember** é [esta seção](../../configuration/using/seed-addresses.md).
