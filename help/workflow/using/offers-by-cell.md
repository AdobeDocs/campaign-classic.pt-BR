---
title: Ofertas por célula
seo-title: Ofertas por célula
description: Ofertas por célula
seo-description: null
page-status-flag: never-activated
uuid: 731bfdde-abd2-400e-9e22-3dbaad37c5b9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: d90594bb-e3ba-4fb1-9e11-83d519c1ca7d
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 100%

---


# Ofertas por célula{#offers-by-cell}

A atividade **[!UICONTROL Offers by cell]** permite distribuir a população de entrada (de uma consulta, por exemplo) em vários segmentos e especificar uma oferta a ser apresentada para cada um desses segmentos.

Essa atividade só pode ser usada com **Interaction**. Para obter mais informações, consulte esta [seção](../../interaction/using/about-outbound-channels.md).

Para fazer isso:

1. Adicione a atividade **[!UICONTROL Offers by cell]** após especificar a população do target e, em seguida, a abra.
1. Na guia **[!UICONTROL General]**, selecione o espaço de ofertas no qual deseja apresentar as ofertas.
1. Na guia **[!UICONTROL Cells]**, especifique os diferentes subconjuntos usando o botão **[!UICONTROL Add]**:

   * Especifique a população de subconjunto usando o filtro disponível e as regras de limitação.
   * Em seguida, selecione a oferta que deseja apresentar ao subconjunto. As ofertas disponíveis são aquelas qualificadas no espaço de oferta que foi selecionado na etapa anterior.

      ![](assets/int_offer_per_cell1.png)

1. Em seguida, configure uma atividade de delivery que corresponda ao canal escolhido. Consulte [Deliveries entre canais](../../workflow/using/cross-channel-deliveries.md).

