---
product: campaign
title: Mecanismo de oferta
description: Mecanismo de oferta
feature: Workflows, Interaction
hide: true
exl-id: 8db4b04f-7754-4a49-ab72-afc916888ebb
TQID: 'https://experienceleague.adobe.com/oAzSAhtWhfJTWcWowjaewtlVucahY839933SaCQZO10'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 65702805-0026-5ca1-843a-144fa79f0883
    internal-label: Interaction
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 100%
---
# Mecanismo de oferta{#offer-engine}



A atividade **[!UICONTROL Offer engine]** permite definir uma chamada para o mecanismo de oferta antes de uma entrega.

Essa atividade funciona de acordo com o mesmo princípio que a atividade de enriquecimento com uma chamada de mecanismo, enriquecendo os dados da população de entrada com uma oferta calculada pelo mecanismo, antes de uma entrega.

![](assets/int_offerengine_activity2.png)

Após configurar sua consulta (consulte esta [seção](query.md)):

1. Adicione e abra uma atividade de **[!UICONTROL Offer engine]**.
1. Preencha os vários campos disponíveis para especificar a chamada para oferecer parâmetros de mecanismo (espaço de oferta, categoria ou tema(s), data de contato, número de ofertas a serem mantidas). O mecanismo calculará automaticamente as ofertas para adicionar de acordo com esses parâmetros.

   >[!CAUTION]
   >
   >Se usar essa atividade, somente as propostas de oferta usadas na entrega serão armazenadas.

   ![](assets/int_offerengine_activity1.png)

1. Em seguida, configure uma atividade de entrega que corresponda ao canal escolhido. Consulte [Entregas entre canais](cross-channel-deliveries.md).
