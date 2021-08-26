---
product: campaign
title: Sobre a simulação de ofertas
description: Sobre a simulação de ofertas
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: facaa88e-1fa2-4189-9d8f-348aaef3e235
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 100%

---

# Sobre a simulação de ofertas{#about-offers-simulation}

![](../../assets/v7-only.svg)

O módulo **Simulation** permite testar a distribuição de ofertas pertencentes a uma categoria ou um ambiente antes de enviar sua proposta para os recipients.

A simulação leva em consideração os contextos e as regras de qualificação aplicadas anteriormente às ofertas (consulte [Visão geral do catálogo de ofertas](../../interaction/using/offer-catalog-overview.md)), bem como suas regras de apresentação (consulte [Gestão de apresentação de ofertas](../../interaction/using/managing-offer-presentation.md)). Isso permite testar e refinar várias versões da apresentação de oferta sem realmente usar uma oferta ou sobrecarregar ou não um destino, já que a simulação não tem impacto nos recipients de destino.

Para saber como simular uma oferta, leia as etapas abaixo.

![](assets/do-not-localize/how-to-video.png)[ Você também pode assistir a este vídeo](https://helpx.adobe.com/campaign/classic/how-to/simulate-offer-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/introduction/collection.ccx.js&amp;ref=helpx.adobe.com).

## Etapas principais para a criação de uma simulação {#main-steps-for-creating-a-simulation}

Para criar uma simulação de suas ofertas, aplique as seguintes etapas:

1. Na guia **[!UICONTROL Profiles and Targets]**, clique no link **[!UICONTROL Simulations]** e depois clique no botão **[!UICONTROL Create]**.

   ![](assets/offer_simulation_001.png)

1. Salve e edite a simulação que acabou de criar.
1. Vá para a guia **[!UICONTROL Edit]** e especifique as configurações de execução.

   Para obter mais informações, consulte [Configurações de execução](../../interaction/using/execution-settings.md).

   ![](assets/offer_simulation_003.png)

   >[!NOTE]
   >
   >As configurações de execução só estarão disponíveis se estiver usando o Interaction com o Campaign.

1. Especifique o escopo da simulação.

   Para obter mais informações, consulte [Definição do escopo](../../interaction/using/simulation-scope.md#definition-of-the-scope).

   ![](assets/offer_simulation_004.png)

1. Adicione eixos de relatórios para aprimorar o relatório **[!UICONTROL Offer distribution by rank]** (opcional).

   Para obter mais informações, consulte [Adição de eixos de relatórios](../../interaction/using/simulation-scope.md#adding-reporting-axes).

   ![](assets/offer_simulation_005.png)

1. Clique em **[!UICONTROL Save]** para gravar as configurações da simulação.
1. Inicie a simulação através do painel.

   ![](assets/offer_simulation_006.png)

1. Verifique o resultado da simulação e exiba o relatório de análise.

   Para obter mais informações, consulte [Rastreamento de simulação](../../interaction/using/simulation-tracking.md).

   ![](assets/offer_simulation_007.png)
