---
solution: Campaign Classic
product: campaign
title: Detecção de URLs de rastreamento
description: Saiba mais sobre o padrão recomendado para rastrear URLs.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 2%

---


# Detecção de URLs de rastreamento

## Exemplo de não detecção

`<%= getURL("http://mynewsletter.com") %>` funciona e envia o conteúdo real da página da Web por email para os recipient. Mas nenhum dos links é rastreado. O motivo para isso é que o MTA executa `"<%=getURL(..."` para cada email antes do envio. Pode ser diferente para cada recipient, portanto, a Adobe Campaign não pode saber os URLs para rastreamento e atribuir uma ID de tag a eles.

Quando a página para download é a mesma para todos os recipient, a prática recomendada é fazer o seguinte:

`<%@ include url="http://mynewsletter.com" %>`

Nesse caso, a página é baixada durante a análise, antes da detecção do rastreamento. Ela permite que a Adobe Campaign descubra os links, atribua uma ID de tag e rastreie-os.

## Padrão recomendado

Depois de processar as instruções `<%@`, o URL a ser rastreado tem a seguinte sintaxe: `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>Todos os outros padrões não são suportados pelo Adobe e devem ser evitados para evitar possíveis falhas de segurança.

## Avisos sobre o padrão http://&lt;%=myURL%>

A sintaxe `<a href="http://<%=myURL%>">` não é segura e não é recomendada porque:

* Tidy pode corrigir incorretamente alguns links, o que pode acontecer aleatoriamente. O sintoma típico é um pedaço de HTML que está visível nas provas de e-mail, mas não na pré-visualização.
* Escapar do URL é problemático, alguns caracteres no URL podem causar problemas.
* Não é possível ter um parâmetro com o nome ID em conflito com o parâmetro no URL de redirecionamento.
* O interesse do rastreamento é então limitado às estatísticas no delivery, já que a Adobe Campaign rastreia de forma indiferente todos os valores possíveis de &quot;myURL&quot;.

Consulte [esta página](https://helpx.adobe.com/br/campaign/kb/acc-security.html#privacy) para saber mais.

