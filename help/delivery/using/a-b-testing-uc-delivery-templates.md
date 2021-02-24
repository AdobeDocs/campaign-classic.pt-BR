---
solution: Campaign Classic
product: campaign
title: Criação dos templates do delivery
description: Saiba como executar testes A/B por meio de um caso de uso dedicado.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 50a10e16f320a67cb4ad0e31c1cbe8a9365b7887
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 59%

---


# Criação dos templates do delivery {#step-3--creating-two-delivery-templates}

Agora devemos criar dois templates de delivery. Cada modelo será referenciado em uma atividade de **[!UICONTROL Email delivery]** vinculada à atividade **[!UICONTROL Split]**. Para obter mais informações, consulte esta [seção](../../delivery/using/about-templates.md).

1. Vá para a pasta de **[!UICONTROL Resources > Delivery template]**.
1. Duplicar o template de delivery **[!UICONTROL Email]**.

   ![](assets/use_case_abtesting_deliverymodel_001.png)

1. Crie o conteúdo a ser usado para a delivery A.

   ![](assets/use_case_abtesting_deliverymodel_002.png)

1. Repita esse processo para criar um modelo para a delivery B.

   ![](assets/use_case_abtesting_deliverymodel_003.png)

Agora você pode configurar os delivery no fluxo de trabalho (consulte [Etapa 4: Configure os delivery no fluxo de trabalho](../../delivery/using/a-b-testing-uc-configuring-deliveries.md)).
