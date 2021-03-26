---
solution: Campaign Classic
product: campaign
title: Nota técnica
description: Nota técnica
hide: false
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 08c6e84e07da2811c91aa58ddf40c5781de2b163
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Atualização de certificado do servidor do serviço de Notificação por Push da Apple {#apns-certificate-update}

Em 29 de março de 2021, uma atualização de infraestrutura do serviço de notificação por push (APNs) da Apple afetará o canal do Adobe Campaign Classic iOS. Uma alteração na configuração do sistema operacional é **mandatory** para evitar a interrupção do canal de push do iOS.

Saiba mais sobre as alterações de APNs [nesta página](https://developer.apple.com/news/?id=7gx0a2lp).

Como cliente hospedado, nenhuma ação é necessária: O Adobe já incorporou o novo certificado raiz ao seu ambiente.

Como cliente local/híbrido, você precisa atualizar sua configuração para garantir uma transição contínua **antes de 29 de março de 2021**.

Para incorporar o novo certificado, siga as etapas abaixo:

1. Baixe o **AAACertificateServices 5/12/2020** certificado raiz [desta página](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. Verifique se o certificado AAA está presente nas lojas de confiabilidade do SO e JAVA. Caso contrário, adicione-o.

1. Reinicie o Adobe Campaign Web Service:

   ```
   nlserver restart web
   ```

