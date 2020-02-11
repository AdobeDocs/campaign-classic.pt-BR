---
title: Rastreamento de Hipótese
seo-title: Rastreamento de Hipótese
description: Rastreamento de Hipótese
seo-description: null
page-status-flag: never-activated
uuid: cb949a9d-8bbe-446b-b5b4-22234a91a68b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: 4452bfc6-9ac4-4d81-a63c-879a163c13ee
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# Rastreamento de Hipótese{#hypothesis-tracking}

O resultado dos cálculos da hipótese está disponível em vários níveis da plataforma Adobe Campaign: indicadores calculados pela hipótese e as reações da amostragem alvo são visíveis por meio da hipótese real, assim como nos relatórios disponíveis por campanhas e envios.

## Resultados da Hipótese {#hypothesis-results}

### Indicadores {#indicators}

Depois que a hipótese é calculada, vários indicadores de mensuração são atualizados automaticamente. These are available in the **[!UICONTROL General]** tab of the hypothesis.

![](assets/response_hypothesis_delivery_example_010.png)

Esses indicadores são:

* **Number of respondent contacts**: número de individuais que correspondem à hipótese.
* **Contacted response rate**: número de contatos de contatos/pessoas contatadas durante o delivery.
* **Number of respondent control group contacts**: número de grupos de controle que correspondem à hipótese.
* **Response rate of the control group**: número de grupos de controle de usuário/número total de grupos de controle de deliveries.
* **Number of reactions**: número de registros na tabela que contém a relação entre individuais, a hipótese e a tabela de transações.

For the full list of indicators, click the **[!UICONTROL Display the list]** link:

![](assets/response_hypothesis_indicators_002.png)

Os indicadores fornecem as seguintes informações:

* **Total revenue of population contacted**: valor total sobre o número de pessoas contatadas.
* **Total revenue of the control group**: valor total sobre o número de grupos de controle.
* **Average revenue per contact**: valor total / contatado.
* **Average revenue of control group**: valor total / grupo de controle.
* **Total margin per contact**: margem total sobre contatados.
* **Total margin of control group**: margem total sobre o grupo de controle.
* **Average margin per contact**: margem total / contatado.
* **Average margin of control groups**: margens totais / grupo de controle.
* **Receitas** adicionais: (Receitas médias do grupo de controlo contactado — Receitas médias)*Número de pessoas contactadas
* **Margem** adicional: (Margem média do grupo de controlo contactado - Margem média) / número de contatos
* **Average cost per contact**: custo de delivery calculado/Número de contatos.
* **ROI**: custo de delivery calculado/margem total por contato
* **Effective ROI**: custo de delivery calculado/margem adicional.
* **Significance**: contém valores 0 a 3 dependendo do significado da campanha.

### Reações {#reactions}

You can view recipients&#39; reactions to the hypotheses via the **[!UICONTROL Reactions]** tab.

1. Once hypothesis calculation is complete, go to the **[!UICONTROL Campaign management > Measurement hypotheses]** node of the Adobe Campaign tree.
1. Select the desired hypothesis and click the **[!UICONTROL Reactions]** tab to view the list of recipients likely to purchase something following the marketing campaign.

   ![](assets/response_hypothesis_reactions_001.png)

## Relatórios {#reports}

The **[!UICONTROL Hypothesis report]** lets you view the results of the hypotheses performed on campaigns and deliveries. This report contains the indicators calculated by the hypothesis (for more on this, refer to [Indicators](#indicators)).

* **No nível** da campanha: clique no **[!UICONTROL Reports]** link da campanha relevante e selecione o **[!UICONTROL Hypothesis report]**. Esse relatório contém a lista de deliveries da campanha e a hipótese calculada para cada um deles.

   ![](assets/response_hypothesis_campaign_report_001.png)

* **No nível** de entrega: para acessar o relatório, abra a entrega em questão, clique **[!UICONTROL Reports]** na guia **[!UICONTROL Summary]** e selecione a **[!UICONTROL Hypothesis report]**. Se várias hipóteses são calculadas para o mesmo delivery, o relatório mostra todas as alternativas.

   ![](assets/response_hypothesis_delivery_report_001.png)
