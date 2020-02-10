---
title: Solução de problemas
seo-title: Solução de problemas
description: Solução de problemas
seo-description: null
page-status-flag: never-activated
uuid: 02bd48cf-3928-4817-97b0-1e64cc8ad8ef
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: b64c9729-cfe2-4d02-8c59-9e53efd34a96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Solução de problemas{#troubleshooting}

Se o dispositivo móvel estiver conectado ao Wi-Fi e você não estiver recebendo notificações, verifique se as portas FCM/APNS não estão bloqueadas pelo firewall.

**Android**: O dispositivo móvel se conecta aos servidores FCM nas portas 5228 a 5230. Portanto, você deve configurar o firewall para que ele autorize a conexão com o FCM. As portas a serem abertas são: 5228 (o mais usado), 5229 e 5230.

**iOS**:

Conector binário: para enviar notificações, é necessário autorizar o tráfego TCP de entrada e saída na porta 2195. Os dispositivos conectados ao serviço de envio devem autorizar o tráfego TCP de entrada e saída na porta 5223.

Conector HTTP/2: é necessário permitir a comunicação de e para os seguintes servidores:

* api.push.apple.com: porta 443
* api.development.push.apple.com: porta 443

>[!NOTE]
>
>For more information on the two connectors, refer to [Connectors](../../delivery/using/setting-up-mobile-app-channel.md#connectors).
