---
solution: Campaign Classic
product: campaign
title: Reciclagem de eventos
description: Reciclagem de eventos
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 100%

---


# Reciclagem de eventos{#event-recycling}

Se o delivery de uma mensagem em um canal específico falhar, o Adobe Campaign poderá reenviar a mensagem usando um canal diferente. Por exemplo, se um delivery no canal SMS falhar, a mensagem será reenviada usando o canal de email.

Para fazer isso, é necessário configurar um workflow que recrie todos os eventos com o status **Delivery error** e atribuir um canal diferente a eles.

>[!CAUTION]
>
>Essa etapa só poderá ser executada usando um workflow e, portanto, é reservada a usuários experts. Para obter mais informações, entre em contato com o executivo da sua conta Adobe.

