---
solution: Campaign Classic
product: campaign
title: Criar um workflow para construção do target
description: Saiba como executar testes A/B por meio de um caso de uso dedicado.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 177b4e74c75e4fcca70dc90b5ff2c0406181e0f7
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 90%

---


# Criação de um workflow para construção do target {#step-1--creating-a-targeting-workflow}

É necessário criar o workflow na guia **[!UICONTROL Targeting and Workflows]** de uma campanha. Ele é composto de uma atividade **[!UICONTROL Query]**, uma atividade **[!UICONTROL Split]** vinculada às duas atividades **[!UICONTROL Email delivery]**, uma atividade **[!UICONTROL Wait]**, uma atividade **[!UICONTROL JavaScript code]** e uma atividade **[!UICONTROL Delivery]**.

1. Se ainda não tiver feito isso, crie uma campanha (para saber mais sobre isso, consulte esta [seção](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Acesse a guia **[!UICONTROL Targeting and Workflows]**.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Altere o rótulo do workflow existente ou clique em **[!UICONTROL Add]** para criar um novo (para mais informações sobre isso, consulte esta [seção](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Use o mouse para arrastar e soltar atividades no diagrama do workflow, incluindo uma **[!UICONTROL Query]** (guia **[!UICONTROL Target]**), uma **[!UICONTROL Split]** (guia **[!UICONTROL Target]**), duas **[!UICONTROL Email deliveries]** (guia **[!UICONTROL Deliveries]**), uma atividade **[!UICONTROL Wait]** (guia **[!UICONTROL Flow Control]**), uma atividade **[!UICONTROL JavaScript code]** (guia **[!UICONTROL Actions]**), e uma atividade **[!UICONTROL Delivery]** (guia **[!UICONTROL Actions]**).

![](assets/use_case_abtesting_targetwkfl_004.png)
