---
solution: Campaign Classic
product: campaign
title: Introdução ao rastreamento de links personalizados
description: Saiba como escrever links em emails que podem ser personalizados e dar suporte ao rastreamento no Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 768fe62db4efd1217c22973c7e5dc31097d67bae
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 88%

---


# Introdução ao rastreamento de links personalizados {#tracking-personalized-links}

Os links no conteúdo de email que contêm personalização precisam de sintaxe específica para serem rastreados.

A utilização do JavaScript no conteúdo de email (HTML ou Texto) permite gerar e enviar conteúdo dinâmico para os recipients, com duas limitações:

* O script não pode acessar o banco de dados diretamente (as funções SQL e API não estão disponíveis),
* O Adobe Campaign deve ser capaz de detectar URLs para que os links possam ser rastreados. [Saiba mais](detecting-tracking-urls.md)

Você pode adicionar [instruções específicas de pré-processamento](pre-processing-instructions.md) nesses URLs

instruções de pré-processamento.

Para detecção de rastreamento, o Adobe Campaign incorpora o [Tidy](http://www.html-tidy.org/) para analisar a origem HTML e detectar o padrão. Ele lista todos os URLs do conteúdo para que possam ser rastreados individualmente. O Adobe Campaign usa o Tidy novamente para substituir o URL (`http://myurl.com`) por um URL que aponte para o servidor de redirecionamento do Adobe Campaign.

Por exemplo, no conteúdo inicial: `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` é substituído para um determinado recipient por: `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

Em que:

* &quot;h&quot; significa conteúdo HTML (ou &quot;t&quot; para conteúdo de texto).
* 617791 é a ID da mensagem/broadLog ID (hexadecimal).
* 71ffa3 é a NmsDelivery ID (hexadecimal).
* 71ffa8 é a NmsTrackingUrl ID (hexadecimal).
* p1, p2 e assim por diante são todos os parâmetros que serão substituídos no URL.
