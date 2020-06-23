---
title: Integração com o Adobe Target
seo-title: Integração com o Adobe Target
description: Integração com o Adobe Target
seo-description: null
page-status-flag: never-activated
uuid: de482b31-0b7b-4669-8a00-28da48c6c5a9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-target
discoiquuid: 44c7acdd-6b7a-4e88-b2a7-3e9bf8a6eab5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0c3737b22c7bf4e614c5a2fbe8e8fd954d3ece8a
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 95%

---


# Integração com o Adobe Target{#integrating-with-adobe-target}

A integração entre o Adobe Campaign e o Adobe Target (Classic e Standard) dentro da Adobe Experience Cloud permite incluir uma oferta do Adobe Target em um delivery de email do Adobe Campaign.

O princípio operacional é o seguinte: quando um recipient abre um email enviado pelo Adobe Campaign, uma chamada para o Adobe Target permite exibir uma versão dinâmica do conteúdo. Essa versão dinâmica é calculada, dependendo das regras especificadas anteriormente ao criar o email.

Saiba mais sobre a integração do Adobe Campaign e do Adobe Target com [estas quatro dicas e truques](https://www.adobe.com/content/dam/www/us/en/marketing/campaign/pdfs/Adobe_Campaign_for_Target_Tips_and_Tricks.pdf).
>[!NOTE]
>
>A integração só oferece suporte a imagens estáticas. O restante do conteúdo não pode ser personalizado.

Vários tipos de dados podem ser utilizados pelo Adobe Target:

* Dados do datamart do Adobe Campaign
* Segmentos vinculados à ID do visitante no Adobe Target, se os dados usados não estiverem sujeitos a limitações legais
* Dados do Adobe Target: agente do usuário, endereço IP, dados de geolocalização

>[!NOTE]
>
>Você também pode encontrar informações sobre a integração entre o Adobe Campaign e o Adobe Target nas [páginas de ajuda do Adobe Target](https://docs.adobe.com/content/help/en/target/using/integrate/campaign-and-target.html).
