---
product: campaign
title: Exemplo de extensão
description: Exemplo de extensão
feature: Interaction, Offers
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: ht
source-wordcount: '165'
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

* Ao configurar chamadas SOAP, insira o elemento XML do **contexto** para fazer referência às informações de contexto adicionadas no schema de interação. Para obter mais informações, consulte [Integração via SOAP (lado do servidor)](../../interaction/using/integration-via-soap-server-side.md).
