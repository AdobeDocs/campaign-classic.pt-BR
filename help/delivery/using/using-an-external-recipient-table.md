---
product: campaign
title: Usar uma tabela externa de destinatário
description: Usar uma tabela externa de destinatário
badge-v8: label="Também se aplica à versão v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 95%

---

# Usar uma tabela externa de destinatário{#using-an-external-recipient-table}



Se a tabela da entrega for uma tabela externa, você precisará fazer configurações adicionais. O schema **[!UICONTROL nms:seedmember]** deve ser estendido. Uma guia é adicionada aos seed addresses para definir os campos adequados, como mostrado abaixo:

![](assets/s_ncs_user_seedlist_new_tab.png)

Nesse caso, para adicionar seed addresses à entrega, insira os campos adequados diretamente na guia correspondente ou importe os templates de endereços:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

A extensão de schema **nms:seedMember** está [nesta seção](../../configuration/using/seed-addresses.md).
