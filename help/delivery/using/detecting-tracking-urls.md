---
product: campaign
title: Detectar URLs de rastreamento
description: Saiba mais sobre o padrão recomendado para rastrear URLs
feature: Monitoring
role: User, Developer
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
TQID: 'https://experienceleague.adobe.com/F63e0G1uyp-tXDiBk9cau5P-HBHttCkiFD2yw657RBw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: d7e5f68c0d2e0b94fd5cfdf2981bed29f33d9f62
workflow-type: ht
source-wordcount: '247'
ht-degree: 100%
---
# Detectar URLs de rastreamento

O Adobe Campaign detecta os URLs para rastreamento no seu conteúdo durante a análise de entrega.

Como parte da transição do Campaign v7 para o v8, o conjunto de documentações do Campaign Classic foi simplificado e reorganizado. Os recursos comuns agora estão disponíveis apenas no conjunto de documentações do Campaign v8. Para saber como os URLs são detectados e quais padrões usar, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/analytics/tracking/personalized-links#url-detection){target=_blank}.

[![imagem](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/analytics/tracking/personalized-links#url-detection){target=_blank}

## Padrão não seguro

Ao adicionar links personalizados ao seu conteúdo, sempre evite qualquer personalização na parte do nome do host do URL para evitar possíveis brechas de segurança. Saiba mais [nesta página](../../installation/using/privacy.md#url-personalization).

Por exemplo, a sintaxe `<a href="http://<%=myURL%>">` não é **segura** e deve ser evitada.

* O uso dessa sintaxe poderá causar problemas de segurança se o link gerado pelo Adobe Campaign contiver um ou mais parâmetros.
* O Tidy pode corrigir incorretamente alguns links, o que pode acontecer aleatoriamente. O sintoma típico é um item de HTML que está visível nas provas de email, mas não na pré-visualização.
* Utilizar o recurso de escape no URL é problemático. Alguns caracteres no URL podem causar problemas.
* Não é possível ter um parâmetro com o nome ID em conflito com o parâmetro no URL de redirecionamento.
* O interesse do rastreamento é então limitado às estatísticas na entrega, já que o Adobe Campaign rastreia de forma indiferente todos os valores possíveis de &quot;myURL&quot;.
