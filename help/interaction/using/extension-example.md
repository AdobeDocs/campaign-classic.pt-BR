---
product: campaign
title: Exemplo de extensão
description: Exemplo de extensão
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 100%

---

# Exemplo de extensão{#extension-example}

![](../../assets/v7-only.svg)

No caso de um contato de entrada (call center ou site da Web), as ofertas mais relevantes são sugeridas para um determinado contato usando um conjunto de regras de qualificação. Para enriquecer os critérios de qualificação de suas ofertas, estenda o schema **nms:interação**.

* Para adicionar um novo contexto de interação, estenda o schema **interaction:interação** e crie quantos elementos **attribute** forem necessários no schema.

   No exemplo a seguir, os critérios adicionados são o código do país e a última página visitada.

   ![](assets/s_ncs_configuration_offer_schemas.png)

* Em seguida, é possível usar os atributos criados anteriormente ao definir a definição dos critérios de qualificação.

   No exemplo a seguir, podemos criar critérios de qualificação para exibir uma oferta com base no país do usuário ou na última página da Web que eles visualizaram.

   ![](assets/s_ncs_configuration_offer_context.png)

* Ao configurar chamadas SOAP, insira o elemento XML do **contexto** para fazer referência às informações de contexto adicionadas no schema de interação. Para obter mais informações, consulte [Integração via SOAP (lado do servidor)](../../interaction/using/integration-via-soap--server-side-.md).
