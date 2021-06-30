---
product: campaign
title: Detectar URLs de rastreamento
description: Saiba mais sobre o padrão recomendado para rastrear URLs
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: ht
source-wordcount: '297'
ht-degree: 100%

---

# Detecção de URLs de rastreamento

## Exemplo de não detecção

`<%= getURL("http://mynewsletter.com") %>` funciona e envia o conteúdo real da página da Web por email para os recipients. Mas nenhum dos links é rastreado. O motivo para isso é que o MTA executa `"<%=getURL(..."` para cada email antes do envio. Pode ser diferente para cada recipient. Portanto, o Adobe Campaign não pode saber os URLs para rastreamento e atribuir uma ID de tag a eles.

Quando a página para download é a mesma para todos os recipients, a prática recomendada é fazer o seguinte:

`<%@ include url="http://mynewsletter.com" %>`

Nesse caso, a página é baixada durante a análise, antes da detecção do rastreamento. Ela permite que o Adobe Campaign descubra os links, atribua uma ID de tag e rastreie-os.

## Padrão recomendado

Após o processamento das instruções `<%@`, o URL a ser rastreado tem a seguinte sintaxe: `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>Todos os outros padrões não são suportados pelo Adobe e devem ser evitados para impedir possíveis falhas de segurança.

## Padrão não seguro

Ao adicionar links personalizados ao seu conteúdo, sempre evite qualquer personalização na parte do nome do host do URL para evitar possíveis brechas de segurança. Saiba mais [nesta página](../../installation/using/privacy.md#url-personalization).

Por exemplo, a sintaxe `<a href="http://<%=myURL%>">` não é **segura** e deve ser evitada.

* O uso dessa sintaxe poderá causar problemas de segurança se o link gerado pelo Adobe Campaign contiver um ou mais parâmetros.
* O Tidy pode corrigir incorretamente alguns links, o que pode acontecer aleatoriamente. O sintoma típico é um item de HTML que está visível nas provas de email, mas não na pré-visualização.
* Utilizar o recurso de escape no URL é problemático. Alguns caracteres no URL podem causar problemas.
* Não é possível ter um parâmetro com o nome ID em conflito com o parâmetro no URL de redirecionamento.
* O interesse do rastreamento é então limitado às estatísticas no delivery, já que o Adobe Campaign rastreia de forma indiferente todos os valores possíveis de &quot;myURL&quot;.
