---
solution: Campaign Classic
product: campaign
title: Introdução ao rastreamento de links personalizados
description: Saiba como escrever links em emails que podem ser personalizados e suportar o rastreamento no Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Introdução ao rastreamento de links personalizados {#tracking-personalized-links}

Os links no conteúdo de email que contêm personalização precisam de sintaxe específica para serem rastreados.

Usar o JavaScript no conteúdo de email (HTML ou Texto) permite gerar e enviar conteúdo dinâmico para os recipient, com duas limitações:

* O script não pode acessar o banco de dados diretamente (as funções SQL e API não estão disponíveis),
* A Adobe Campaign deve ser capaz de detectar URLs para que os links possam ser rastreados (finalidade desse documento).

Para detecção de rastreamento, a Adobe Campaign incorpora [Tidy](http://www.html-tidy.org/) para analisar a fonte HTML e detectar o padrão. Ele lista todos os URLs do conteúdo para que possam ser rastreados individualmente. A Adobe Campaign usa o Tidy novamente para substituir o URL (`http://myurl.com`) por um URL apontando para o servidor de redirecionamento da Adobe Campaign.

Por exemplo, no conteúdo inicial: `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` é substituído para um recipient específico por: `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

Em que:

* &quot;h&quot; significa conteúdo HTML (ou &quot;t&quot; para conteúdo de texto).
* 617791 é a ID da mensagem / wideLog ID (hexadecimal).
* 71ffa3 é a NmsDelivery ID (hexadecimal).
* 71ffa8 é a ID NmsTrackingUrl (hexadecimal).
* p1, p2 e assim por diante, são todos os parâmetros a serem substituídos no URL.
