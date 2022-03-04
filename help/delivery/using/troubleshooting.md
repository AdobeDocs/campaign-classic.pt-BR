---
product: campaign
title: Solução de problemas
description: Solução de problemas de push
feature: Push
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 100%

---

# Solução de problemas{#troubleshooting}

![](../../assets/common.svg)

Se o dispositivo móvel estiver conectado ao wi-fi e você não estiver recebendo notificações, verifique se as portas FCM/APNS não estão bloqueadas pelo firewall.

**Android**: o dispositivo móvel conecta-se aos servidores FCM nas portas 5228 a 5230. Portanto, você deve configurar o firewall para que ele autorize a conexão com o FCM. As portas que devem ser abertas são: 5228 (a mais usada), 5229 e 5230.

**iOS**:

Conector HTTP/2: é necessário permitir a comunicação de e para os seguintes servidores:

* api.push.apple.com: porta 443
* api.development.push.apple.com: porta 443

>[!NOTE]
>
>Para obter mais informações sobre os dois conectores, consulte [Configuração do aplicativo móvel no Adobe Campaign](configuring-the-mobile-application.md).
