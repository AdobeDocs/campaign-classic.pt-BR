---
title: Implementação
seo-title: Implementação
description: Implementação
seo-description: null
page-status-flag: never-activated
uuid: 12b5fbbf-fe0d-4598-8845-f7b8ee7672c3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: ac1c0a00-41ef-4cc2-bb51-2808ef400bb1
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Implementação{#implementation}

Este é um diagrama com as diferentes etapas envolvidas nesse cenário.

![](assets/message-center-uc1.png)

Primeiro, comece criando seu anexo. Consulte este [artigo](../../delivery/using/attaching-files.md#attach-a-personalized-file). Isso permite anexar os arquivos a um email, mesmo se eles não estiverem hospedados na instância de execução.

Você pode enviar emails por meio de um gatilho de mensagem SOAP Para saber mais sobre solicitações SOAP, consulte [Descrição do evento](../../message-center/using/event-description.md). Na chamada SOAP, há um parâmetro de URL (attachmentURL).

Ao criar seu email, clique em **[!UICONTROL Attachment]**. Na tela **[!UICONTROL Attachment definition]**, digite o parâmetro de anexo SOAP:

```
<%= rtEvent.ctx.attachementUrl %>
```

Quando a mensagem está processando/implantando, o sistema obtém o arquivo do local remoto (servidor de terceiros) e o anexa à mensagem individual.

Como esse parâmetro pode ser uma variável, ele deve aceitar a variável de URL remota totalmente formada do seu arquivo, enviado pela chamada SOAP.

![](assets/message-center-uc2.png)

