---
product: campaign
title: Criação dos modelos de delivery
description: Saiba como executar testes A/B por meio de um caso de uso dedicado
exl-id: 77b3a906-b76e-49e1-b524-b6f1ae537259
source-git-commit: 90c52ec144a6a3c1b534a80507e38fa3ed64fc83
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 100%

---

# Criar os modelos de entrega {#step-3--creating-two-delivery-templates}

![](../../assets/common.svg)

Agora devemos criar dois modelos de delivery. Cada modelo será referenciado em uma atividade de **[!UICONTROL Email delivery]** vinculada à atividade **[!UICONTROL Split]**. Para obter mais informações, consulte [esta seção](about-templates.md).

1. Navegue até a pasta **[!UICONTROL Resources > Delivery template]**.
1. Duplicar o template de delivery **[!UICONTROL Email]**.

   ![](assets/use_case_abtesting_deliverymodel_001.png)

1. Crie o conteúdo a ser usado para a delivery A.

   ![](assets/use_case_abtesting_deliverymodel_002.png)

1. Repita esse processo para criar um modelo para a delivery B.

   ![](assets/use_case_abtesting_deliverymodel_003.png)

Agora você pode configurar as entregas no fluxo de trabalho. [Saiba mais](a-b-testing-uc-configuring-deliveries.md).
