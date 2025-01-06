---
product: campaign
title: Nota técnica - Atualização do certificado do servidor do serviço de Notificação por push do Apple
description: Atualização do certificado do servidor do serviço de notificação por push do Apple
feature: Technote, Push
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 0143e0d6ebcdbd96d183ddd0c7f07beb149a9670
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Atualização do certificado do servidor do serviço de notificação por push do Apple {#apns-certificate-update}



Em 17 de outubro de 2024, uma atualização de infraestrutura do serviço de notificação por push (APNs) da Apple afetou o canal do Adobe Campaign Classic iOS. Uma alteração na configuração do sistema operacional é **obrigatória** para evitar a interrupção do canal de push do iOS.

Saiba mais sobre alterações de APNs [nesta página](https://developer.apple.com/news/?id=09za8wzy).

Como cliente hospedado, nenhuma ação é necessária: o Adobe já incorporou o novo certificado raiz ao seu ambiente.

Como cliente local/híbrido, você precisa atualizar sua configuração para garantir uma transição contínua **antes de 24 de fevereiro de 2025**.

Para incorporar o novo certificado, siga as etapas abaixo:

1. Baixe o **SHA-2 Raiz: Certificado de Autoridade de Certificação RSA USERTrust** certificado raiz [desta página](https://www.sectigo.com/knowledge-base/detail/Sectigo-Intermediate-Certificates/kA01N000000rfBO).

1. Verifique se o certificado AAA está presente nos trustores do SO e do JAVA. Caso contrário, adicione-o.

1. Reinicie o Adobe Campaign Web Service:

   ```
   nlserver restart web
   ```
