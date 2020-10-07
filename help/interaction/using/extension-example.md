---
title: Exemplo de extensão
seo-title: Exemplo de extensão
description: Exemplo de extensão
seo-description: null
page-status-flag: never-activated
uuid: 6703b6e8-4eac-4a94-a80a-a7cd71b25cdf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 990b6cbc-9b7b-4278-a635-653d5abafe87
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 100%

---


# Exemplo de extensão{#extension-example}

No caso de um contato de entrada (call center ou site da Web), as ofertas mais relevantes são sugeridas para um determinado contato usando um conjunto de regras de qualificação. Para enriquecer os critérios de qualificação de suas ofertas, estenda o schema **nms:interação**.

* Para adicionar um novo contexto de interação, estenda o schema **interaction:interação** e crie quantos elementos **attribute** forem necessários no schema.

   No exemplo a seguir, os critérios adicionados são o código do país e a última página visitada.

   ![](assets/s_ncs_configuration_offer_schemas.png)

* Em seguida, é possível usar os atributos criados anteriormente ao definir a definição dos critérios de qualificação.

   No exemplo a seguir, podemos criar critérios de qualificação para exibir uma oferta com base no país do usuário ou na última página da Web que eles visualizaram.

   ![](assets/s_ncs_configuration_offer_context.png)

* Ao configurar chamadas SOAP, insira o elemento XML do **contexto** para fazer referência às informações de contexto adicionadas no schema de interação. Para obter mais informações, consulte [Integração via SOAP (lado do servidor)](../../interaction/using/integration-via-soap--server-side-.md).

