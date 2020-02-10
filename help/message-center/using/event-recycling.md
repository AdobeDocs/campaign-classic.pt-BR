---
title: Reciclagem de eventos
seo-title: Reciclagem de eventos
description: Reciclagem de eventos
seo-description: null
page-status-flag: never-activated
uuid: 55624a41-65a1-4759-8087-6e5d2c5c5b62
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 568a9dec-5818-4666-b858-aa41fe827b92
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Reciclagem de eventos{#event-recycling}

Se o delivery de uma mensagem em um canal específico falhar, o Adobe Campaign poderá reenviar a mensagem usando um canal diferente. Por exemplo, se um delivery no canal SMS falhar, a mensagem será reenviada usando o canal de email.

To do this, you need to configure a workflow which recreates all events with the **Delivery error** status, and assigns a different channel to them.

>[!CAUTION]
>
>Essa etapa só poderá ser executada usando um workflow e, portanto, é reservada a usuários experts. Para obter mais informações, entre em contato com o executivo da sua conta Adobe.

