---
title: Envio de uma prova
seo-title: Envio de uma prova
description: Envio de uma prova
seo-description: null
page-status-flag: never-activated
uuid: 6446cc5c-8378-48d1-9486-bffbae83e28d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 81090be2-3ed4-4f35-948b-e21af6e19999
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0ce6e5277c32bc18c20dca62e5b276f654d1ace5

---


# Envio de uma prova{#sending-a-proof}

Você pode testar o delivery de mensagens enviando uma prova para um seed address criado anteriormente.

O envio de uma prova envolve o mesmo processo de delivery regular (para obter mais informações, consulte [esta seção](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)). No entanto, para enviar uma prova no Centro de Mensagens, você precisa realizar as seguintes operações antecipadamente:

* criar um ou mais endereços semente (consulte [Gerenciar endereços semente em mensagens](../../message-center/using/managing-seed-addresses-in-transactional-messages.md)transacionais) com dados de teste (consulte Dados [de](../../message-center/using/personalization-data.md)personalização),
* crie o conteúdo da mensagem (consulte [Criação de conteúdo](../../message-center/using/creating-message-content.md)da mensagem).

Para enviar a prova:

1. Clique no **[!UICONTROL Send a proof]** botão na janela de entrega.
1. Analise o delivery.
1. Corrija qualquer erro e confirme o delivery.

   ![](assets/messagecenter_send_proof_001.png)

1. Verifique se a mensagem foi entregue ao seed address e se seu conteúdo está em conformidade com sua configuração.

   ![](assets/messagecenter_send_proof_002.png)

Proofs can be accessed in each template via the **[!UICONTROL Audit]** tab.

![](assets/messagecenter_send_proof_003.png)

