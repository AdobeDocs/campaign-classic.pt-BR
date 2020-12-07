---
solution: Campaign Classic
product: campaign
title: Criação de um ambiente de teste
description: Criação de um ambiente de teste
audience: interaction
content-type: reference
topic-tags: advanced-parameters
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '120'
ht-degree: 100%

---


# Criação de um ambiente de teste{#creating-a-test-environment}

Para criar um ambiente de teste (modo sandbox), siga as etapas abaixo:

>[!IMPORTANT]
>
>Use somente esse método de criação de ambiente para ambientes de teste. Em todos os outros casos, use o assistente de target mapping. Para obter mais informações, consulte [Criação de um ambiente de ofertas](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

1. Inicie o explorador do Adobe Campaign e vá para a raiz da instância.
1. Clique com o botão direito do mouse e adicione um **[!UICONTROL Generic folder]** usando os menus suspensos.

   ![](assets/offer_env_creation_001.png)

1. Em seguida, acesse a pasta que acabou de criar e adicione um **[!UICONTROL Offer environment]** usando os menus de atalho.

   ![](assets/offer_env_creation_001bis.png)

1. Aplique o mesmo processo para criar as subpastas e os elementos do ambiente.
1. Depois que os testes forem concluídos e quiser usar o ambiente em produção, duplique as ofertas e espaços no ambiente de design. (Clique com o botão direito do mouse em > **[!UICONTROL Actions]** > **[!UICONTROL Deploy]** ).

   ![](assets/migration_interaction_5.png)

