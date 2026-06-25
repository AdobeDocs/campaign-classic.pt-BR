---
product: campaign
title: Criar os modelos de entrega
description: Saiba como executar testes A/B por meio de um caso de uso dedicado
role: User
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: A/B Testing
exl-id: 77b3a906-b76e-49e1-b524-b6f1ae537259
TQID: https://experienceleague.adobe.com/eble-fTf8Rk7fFGnKNh5pLUhMaLdZlJrG-vjrhbHx1I
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 104
ht-degree: 100%

---

# Teste A/B: criar os modelos de entrega {#step-3--creating-two-delivery-templates}

Agora devemos criar dois modelos de entrega. Cada modelo será referenciado em uma atividade de **[!UICONTROL Email delivery]** vinculada à atividade **[!UICONTROL Split]**. Consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-templates.html?lang=pt-BR){target="_blank"}.

1. Navegue até a pasta **[!UICONTROL Resources > Delivery template]**.
1. Duplicar o modelo de entrega **[!UICONTROL Email]**.

   ![](assets/use_case_abtesting_deliverymodel_001.png)

1. Crie o conteúdo a ser usado para a entrega A.

   ![](assets/use_case_abtesting_deliverymodel_002.png)

1. Repita esse processo para criar um modelo para a entrega B.

   ![](assets/use_case_abtesting_deliverymodel_003.png)

Agora você pode configurar as entregas no fluxo de trabalho. [Saiba mais](a-b-testing-uc-configuring-deliveries.md).
