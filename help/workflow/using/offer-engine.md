---
product: campaign
title: Mecanismo de oferta
description: Mecanismo de oferta
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 8db4b04f-7754-4a49-ab72-afc916888ebb
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: ht
source-wordcount: '136'
ht-degree: 100%

---

# Mecanismo de oferta{#offer-engine}

![](../../assets/common.svg)

A atividade **[!UICONTROL Offer engine]** permite definir uma chamada para o mecanismo de oferta antes de um delivery.

Essa atividade funciona de acordo com o mesmo princípio que a atividade de enriquecimento com uma chamada de mecanismo, enriquecendo os dados da população de entrada com uma oferta calculada pelo mecanismo, antes de um delivery.

![](assets/int_offerengine_activity2.png)

Após configurar sua query (consulte esta [seção](query.md)):

1. Adicione e abra uma atividade de **[!UICONTROL Offer engine]**.
1. Preencha os vários campos disponíveis para especificar a chamada para oferecer parâmetros de mecanismo (espaço de oferta, categoria ou tema(s), data de contato, número de ofertas a serem mantidas). O mecanismo calculará automaticamente as ofertas para adicionar de acordo com esses parâmetros.

   >[!CAUTION]
   >
   >Se usar essa atividade, somente as propostas de oferta usadas no fornecimento serão armazenadas.

   ![](assets/int_offerengine_activity1.png)

1. Em seguida, configure uma atividade de delivery que corresponda ao canal escolhido. Consulte [Deliveries entre canais](cross-channel-deliveries.md).
