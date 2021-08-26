---
product: campaign
title: Integração com o Adobe Target
description: Integração com o Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 100%

---

# Integração com o Adobe Target{#integrating-with-adobe-target}

![](../../assets/common.svg)

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
>Você também pode encontrar informações sobre a integração entre o Adobe Campaign e o Adobe Target nas [páginas de ajuda do Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html?lang=pt-BR).
