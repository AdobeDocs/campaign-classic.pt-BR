---
product: campaign
title: Exemplo de extensão
description: Exemplo de extensão
feature: Interaction, Offers
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
TQID: 'https://experienceleague.adobe.com/TQZaYrJop03HAw47XPFqgmoxb073iC-xztTp-f-5dEk'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
    internal-label: Offer Management
  - id: 65702805-0026-5ca1-843a-144fa79f0883
    internal-label: Interaction
  - id: ea08db70-4682-59a2-9408-9aedd9548e07
    internal-label: Offers
subfeature_v2:
  - id: e739ee2b-6228-412e-878f-45de0791417d
    internal-label: Use cases
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 100%
---
# Exemplo de extensão{#extension-example}



No caso de um contato de entrada (call center ou site da Web), as ofertas mais relevantes são sugeridas para um determinado contato usando um conjunto de regras de elegibilidade. Para enriquecer os critérios de elegibilidade de suas ofertas, estenda o esquema **nms:interaction**.

* Para adicionar um novo contexto de interação, estenda o esquema **nms:interaction** e crie quantos elementos de **atributo** forem necessários no esquema.

  No exemplo a seguir, os critérios adicionados são o código do país e a última página visitada.

  ![](assets/s_ncs_configuration_offer_schemas.png)

* Em seguida, é possível usar os atributos criados anteriormente ao definir a definição dos critérios de elegibilidade.

  No exemplo a seguir, podemos criar critérios de elegibilidade para exibir uma oferta com base no país do usuário ou na última página da Web que eles visualizaram.

  ![](assets/s_ncs_configuration_offer_context.png)

* Ao configurar chamadas SOAP, insira o elemento XML do **contexto** para fazer referência às informações de contexto adicionadas no esquema de interação. Para obter mais informações, consulte [Integração via SOAP (lado do servidor)](../../interaction/using/integration-via-soap-server-side.md).
