---
product: campaign
title: Criar os modelos do delivery
description: Saiba como executar testes A/B por meio de um caso de uso dedicado
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: 77b3a906-b76e-49e1-b524-b6f1ae537259
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 100%

---

# Criar os modelos de entrega {#step-3--creating-two-delivery-templates}



Agora devemos criar dois modelos de delivery. Cada modelo será referenciado em uma atividade de **[!UICONTROL Email delivery]** vinculada à atividade **[!UICONTROL Split]**. Para obter mais informações, consulte [esta seção](about-templates.md).

1. Navegue até a pasta **[!UICONTROL Resources > Delivery template]**.
1. Duplicar o template de delivery **[!UICONTROL Email]**.

   ![](assets/use_case_abtesting_deliverymodel_001.png)

1. Crie o conteúdo a ser usado para a delivery A.

   ![](assets/use_case_abtesting_deliverymodel_002.png)

1. Repita esse processo para criar um modelo para a delivery B.

   ![](assets/use_case_abtesting_deliverymodel_003.png)

Agora você pode configurar as entregas no fluxo de trabalho. [Saiba mais](a-b-testing-uc-configuring-deliveries.md).
