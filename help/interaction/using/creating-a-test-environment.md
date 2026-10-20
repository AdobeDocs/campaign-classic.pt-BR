---
product: campaign
title: Criação de um ambiente de teste
description: Criação de um ambiente de teste
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 49ac279b-bc67-4311-b0a4-0e23f2a99c52
TQID: 'https://experienceleague.adobe.com/-V-tBgJnQ-1-W7MfUEqXQ5Zzd8GN32XT-9dWVsRa6FI'
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
source-git-commit: 323ff901668895588a6e9587fa2a8b7804cf2fb4
workflow-type: ht
source-wordcount: '144'
ht-degree: 100%
---
# Criação de um ambiente de teste{#creating-a-test-environment}



Para criar um ambiente de teste (modo sandbox), siga as etapas abaixo:

>[!IMPORTANT]
>
>Use somente esse método de criação de ambiente para ambientes de teste. Em todos os outros casos, use o assistente de target mapping. Para obter mais informações sobre isso, consulte [Criar um ambiente de ofertas](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/offers/interaction-settings/interaction-env#create-an-offer-environment){target="_blank"} (documentação do Campaign v8).

1. Inicie o explorer do Adobe Campaign e vá para a raiz da instância.
1. Clique com o botão direito do mouse e adicione um **[!UICONTROL Generic folder]** usando os menus suspensos.

   ![](assets/offer_env_creation_001.png)

1. Em seguida, acesse a pasta que acabou de criar e adicione um **[!UICONTROL Offer environment]** usando os menus do botão direito do mouse.

   ![](assets/offer_env_creation_001bis.png)

1. Aplique o mesmo processo para criar as subpastas e os elementos do ambiente.
1. Depois que os testes forem concluídos e quiser usar o ambiente em produção, duplique as ofertas e espaços no ambiente de design. (Clique com o botão direito do mouse em > **[!UICONTROL Actions]** > **[!UICONTROL Deploy]** ).

   ![](assets/migration_interaction_5.png)
