---
product: campaign
title: Exemplo de extensão
description: Exemplo de extensão
feature: Interaction, Offers
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
TQID: https://experienceleague.adobe.com/TQZaYrJop03HAw47XPFqgmoxb073iC-xztTp-f-5dEk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 160
ht-degree: 79%

---

# Exemplo de extensão{#extension-example}



No caso de um contato de entrada (call center ou site da Web), as ofertas mais relevantes são sugeridas para um determinado contato usando um conjunto de regras de elegibilidade. Para enriquecer os critérios de qualificação de suas ofertas, estenda o esquema **nms:interaction**.

* Para adicionar um novo contexto de interação, estenda o esquema **nms:interaction** e crie quantos elementos **attribute** forem necessários no esquema.

  No exemplo a seguir, os critérios adicionados são o código do país e a última página visitada.

  ![](assets/s_ncs_configuration_offer_schemas.png)

* Em seguida, é possível usar os atributos criados anteriormente ao definir a definição dos critérios de elegibilidade.

  No exemplo a seguir, podemos criar critérios de elegibilidade para exibir uma oferta com base no país do usuário ou na última página da Web que eles visualizaram.

  ![](assets/s_ncs_configuration_offer_context.png)

* Ao configurar chamadas SOAP, insira o elemento XML do **contexto** para fazer referência às informações de contexto adicionadas no esquema de interação. Para obter mais informações, consulte [Integração via SOAP (lado do servidor)](../../interaction/using/integration-via-soap-server-side.md).
