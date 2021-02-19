---
solution: Campaign Classic
product: campaign
title: Criação de categorias de ofertas
description: Criação de categorias de ofertas
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 100%

---


# Criação de categorias de ofertas{#creating-offer-categories}

A criação de categorias de oferta só pode ocorrer no ambiente **[!UICONTROL Design]**. Eles são implantados automaticamente no ambiente **[!UICONTROL Live]**, ou seja, são disponibilizados quando as ofertas criadas/modificadas que eles contêm são aprovadas. Por padrão, o ambiente **[!UICONTROL Design]** contém uma categoria para receber todas as ofertas. Subcategorias pode ser criado para adicionar hierarquia às ofertas de catálogo.

Para cada categoria, é possível definir datas de qualificação, ou seja, um ponto além do qual as ofertas contidas na categoria podem não ser mais apresentadas ao target. Se desejar que as ofertas de uma categoria específica sejam selecionadas como uma prioridade pelo mecanismo de oferta, para melhor expor um produto, por exemplo, é possível aumentar seus pesos por um determinado período adicionando um peso multiplicando na categoria.

Para criar uma categoria adicional, siga as etapas abaixo:

1. Vá para a pasta de **[!UICONTROL Offer catalog]**.

   ![](assets/offer_cat_create_001.png)

1. Clique com o botão direito e selecione **[!UICONTROL Create a new "Offer category" folder]** na lista suspensa.

   ![](assets/offer_cat_create_002.png)

1. Renomeie a categoria. É possível editar o rótulo posteriormente usando a guia **[!UICONTROL General]**.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Repita essas etapas para criar quantas categorias forem necessárias.

   Logo, conforme necessário:

   * Atribuir datas de qualificação pela guia **[!UICONTROL Eligibility]**.

      ![](assets/offer_cat_create_004.png)

   * Insira as palavras-chave que podem ser usadas para selecionar ofertas dentro desta categoria, usando o campo **[!UICONTROL Themes]**.

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >Ao chamar o mecanismo de oferta, somente a parte do catálogo no qual os temas ou categorias correspondem aos parâmetros é selecionada.

   * “Impulsione” temporariamente o peso da oferta de uma categoria por um determinado período por meio do campo **[!UICONTROL Multiplier weight]**.

      ![](assets/offer_cat_create_006.png)

Um resumo das regras de qualificação está disponível no painel das ofertas incluídas na categoria. Para visualizá-las, clique no link **[!UICONTROL Schedule and eligibility rules of the offer]**.

![](assets/offer_create_006.png)

