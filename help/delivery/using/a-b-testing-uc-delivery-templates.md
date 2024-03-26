---
product: campaign
title: Criar os templates de entrega
description: Saiba como executar testes A/B por meio de um caso de uso dedicado
role: User
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: A/B Testing
exl-id: 77b3a906-b76e-49e1-b524-b6f1ae537259
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 100%

---

# Teste A/B: criar os modelos de entrega {#step-3--creating-two-delivery-templates}

Agora devemos criar dois modelos de entrega. Cada modelo será referenciado em uma atividade de **[!UICONTROL Email delivery]** vinculada à atividade **[!UICONTROL Split]**. Para obter mais informações, consulte [esta seção](about-templates.md).

1. Navegue até a pasta **[!UICONTROL Resources > Delivery template]**.
1. Duplicar o template de entrega **[!UICONTROL Email]**.

   ![](assets/use_case_abtesting_deliverymodel_001.png)

1. Crie o conteúdo a ser usado para a entrega A.

   ![](assets/use_case_abtesting_deliverymodel_002.png)

1. Repita esse processo para criar um modelo para a entrega B.

   ![](assets/use_case_abtesting_deliverymodel_003.png)

Agora você pode configurar as entregas no fluxo de trabalho. [Saiba mais](a-b-testing-uc-configuring-deliveries.md).
