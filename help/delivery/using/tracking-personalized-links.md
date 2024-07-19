---
product: campaign
title: Introdução ao rastreamento de links personalizados
description: Saiba como incluir links em emails que podem ser personalizados e dar suporte ao rastreamento no Campaign
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Personalization
role: User
exl-id: d0e00b40-e7dd-4484-b37c-fd3f3ac70fda
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 100%

---

# Introdução ao rastreamento de links personalizados {#tracking-personalized-links}

Os links no conteúdo de email que contêm personalização precisam de sintaxe específica para serem rastreados.

A utilização do JavaScript no conteúdo de email (HTML ou Texto) permite gerar e enviar conteúdo dinâmico para os destinatários, com duas limitações:

* O script não pode acessar o banco de dados diretamente (as funções SQL e API não estão disponíveis),
* O Adobe Campaign deve ser capaz de detectar URLs para que os links possam ser rastreados. [Saiba mais](detecting-tracking-urls.md)

Você pode adicionar instruções específicas de pré-processamento para fazer o script do URL e rastreá-lo. [Saiba mais](pre-processing-instructions.md)

Para detecção de rastreamento, o Adobe Campaign incorpora o [Tidy](https://www.html-tidy.org/) para analisar a origem HTML e detectar o padrão. Ele lista todos os URLs do conteúdo para que possam ser rastreados individualmente. O Adobe Campaign usa o Tidy novamente para substituir o URL (`http://myurl.com`) por um URL que aponte para o servidor de redirecionamento do Adobe Campaign.

Por exemplo, no conteúdo inicial: `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` é substituído para um determinado destinatário por: `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

Em que:

* &quot;h&quot; significa conteúdo HTML (ou &quot;t&quot; para conteúdo de texto).
* 617791 é a ID da mensagem/broadLog ID (hexadecimal).
* 71ffa3 é a NmsDelivery ID (hexadecimal).
* 71ffa8 é a NmsTrackingUrl ID (hexadecimal).
* p1, p2 e assim por diante são todos os parâmetros que serão substituídos no URL.
