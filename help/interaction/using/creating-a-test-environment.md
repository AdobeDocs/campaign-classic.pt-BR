---
product: campaign
title: Criação de um ambiente de teste
description: Criação de um ambiente de teste
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 49ac279b-bc67-4311-b0a4-0e23f2a99c52
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 100%

---

# Criação de um ambiente de teste{#creating-a-test-environment}



Para criar um ambiente de teste (modo sandbox), siga as etapas abaixo:

>[!IMPORTANT]
>
>Use somente esse método de criação de ambiente para ambientes de teste. Em todos os outros casos, use o assistente de target mapping. Para obter mais informações, consulte [Criação de um ambiente de ofertas](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

1. Inicie o explorer do Adobe Campaign e vá para a raiz da instância.
1. Clique com o botão direito do mouse e adicione um **[!UICONTROL Generic folder]** usando os menus suspensos.

   ![](assets/offer_env_creation_001.png)

1. Em seguida, acesse a pasta que acabou de criar e adicione um **[!UICONTROL Offer environment]** usando os menus de atalho.

   ![](assets/offer_env_creation_001bis.png)

1. Aplique o mesmo processo para criar as subpastas e os elementos do ambiente.
1. Depois que os testes forem concluídos e quiser usar o ambiente em produção, duplique as ofertas e espaços no ambiente de design. (Clique com o botão direito do mouse em > **[!UICONTROL Actions]** > **[!UICONTROL Deploy]** ).

   ![](assets/migration_interaction_5.png)
