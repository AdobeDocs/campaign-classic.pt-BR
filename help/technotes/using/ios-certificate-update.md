---
product: campaign
title: Nota técnica - Atualização do certificado do servidor do serviço de Notificação por push do Apple
description: Atualização do certificado do servidor do serviço de notificação por push do Apple
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Atualização do certificado do servidor do serviço de notificação por push do Apple {#apns-certificate-update}



Em 29 de março de 2021, uma atualização de infraestrutura do serviço de notificação por push (APNs) da Apple afetou o canal do Adobe Campaign Classic iOS. Uma alteração na configuração do SO é **obrigatório** para evitar a interrupção do canal de push do iOS.

Saiba mais sobre alterações de APNs [nesta página](https://developer.apple.com/news/?id=7gx0a2lp).

Como cliente hospedado, nenhuma ação é necessária: o Adobe já incorporou o novo certificado raiz ao seu ambiente.

Como cliente local/híbrido, você precisa atualizar sua configuração para garantir uma transição contínua **antes de 29 de março de 2021**.

Para incorporar o novo certificado, siga as etapas abaixo:

1. Baixe o **AAACertificateServices 12/05/2020** certificado raiz [nesta página](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. Verifique se o certificado AAA está presente nos trustores do SO e do JAVA. Caso contrário, adicione-o.

1. Reinicie o Adobe Campaign Web Service:

   ```
   nlserver restart web
   ```
