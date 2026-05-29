---
product: campaign
title: Ofertas por célula
description: Ofertas por célula
feature: Workflows, Targeting Activity, Interaction
hide: true
exl-id: 72b17b48-093a-4eb9-a848-3c1570e49b61
TQID: https://experienceleague.adobe.com/ddCHWdqnyWjUtP3lcc3yIaUHffGkNCbnVKWiJVfhdjg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 153
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

1. Em seguida, configure uma atividade de entrega que corresponda ao canal escolhido. Consulte [Entregas entre canais](cross-channel-deliveries.md).
