---
title: Criação de um ambiente de teste
seo-title: Criação de um ambiente de teste
description: Criação de um ambiente de teste
seo-description: null
page-status-flag: never-activated
uuid: 60ce42d5-6c0c-4a0d-bfd6-c778b42563a7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 7a92bc51-24cf-4ce6-bd50-a315f8f6e34e
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Criação de um ambiente de teste{#creating-a-test-environment}

Para criar um ambiente de teste (modo sandbox), siga as etapas abaixo:

>[!CAUTION]
>
>Use somente esse método de criação de ambiente para ambientes de teste. Em todos os outros casos, use o assistente de target mapping. Para obter mais informações, consulte [Criação de um ambiente de ofertas](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

1. Inicie o explorador do Adobe Campaign e vá para a raiz da instância.
1. Clique com o botão direito do mouse e adicione uma **[!UICONTROL Pasta genérica]** usando os menus suspensos.

   ![](assets/offer_env_creation_001.png)

1. Em seguida, acesse a pasta que acabou de criar e adicione um **[!UICONTROL Ambiente de oferta]** usando os menus do botão direito do mouse.

   ![](assets/offer_env_creation_001bis.png)

1. Aplique o mesmo processo para criar as subpastas e os elementos do ambiente.
1. Depois que os testes forem concluídos e quiser usar o ambiente em produção, duplique as ofertas e espaços no ambiente de design. (Clique com o botão direito do mouse em > **[!UICONTROL Actions]** > **[!UICONTROL Deploy]** ).

   ![](assets/migration_interaction_5.png)

