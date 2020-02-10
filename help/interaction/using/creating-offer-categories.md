---
title: Criação de categorias de ofertas
seo-title: Criação de categorias de ofertas
description: Criação de categorias de ofertas
seo-description: null
page-status-flag: never-activated
uuid: 5ac0ae5e-1731-4699-b4ef-f3867ad0ab58
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: a9fad813-3256-4a00-ba74-7dbaba9e8e23
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Criação de categorias de ofertas{#creating-offer-categories}

The creation of offer categories can only take place in the **[!UICONTROL Design]** environment. They are deployed automatically in the **[!UICONTROL Live]** environment (i.e. made available) when the created/modified offer(s) they contain are approved. By default, the **[!UICONTROL Design]** environment contains a category to receive all offers. Subcategorias pode ser criado para adicionar hierarquia às ofertas de catálogo.

Para cada categoria, é possível definir datas de qualificação, ou seja, um ponto além do qual as ofertas contidas na categoria podem não ser mais apresentadas ao target. Se desejar que as ofertas de uma categoria específica sejam selecionadas como uma prioridade pelo mecanismo de oferta, para melhor expor um produto, por exemplo, é possível aumentar seus pesos por um determinado período adicionando um peso multiplicando na categoria.

Para criar uma categoria adicional, siga as etapas abaixo:

1. Vá para a **[!UICONTROL Offer catalog]** pasta.

   ![](assets/offer_cat_create_001.png)

1. Clique com o botão direito do mouse e selecione **[!UICONTROL Create a new "Offer category" folder]** na lista suspensa.

   ![](assets/offer_cat_create_002.png)

1. Renomeie a categoria. You can edit the label later using the **[!UICONTROL General]** tab.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Repita essas etapas para criar quantas categorias forem necessárias.

   Logo, conforme necessário:

   * assign eligibility dates from the **[!UICONTROL Eligibility]** tab.

      ![](assets/offer_cat_create_004.png)

   * enter key words that may be used to select offers from within this category, using the **[!UICONTROL Themes]** field.

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >Ao chamar o mecanismo de oferta, somente a parte do catálogo no qual os temas ou categorias correspondem aos parâmetros é selecionada.

   * You can temporarily &quot;boost&quot; the offer weight of a category for a given period via the **[!UICONTROL Multiplier weight]** field.

      ![](assets/offer_cat_create_006.png)

Um resumo das regras de qualificação está disponível no painel das ofertas incluídas na categoria. Para exibi-los, clique no **[!UICONTROL Schedule and eligibility rules of the offer]** link.

![](assets/offer_create_006.png)

