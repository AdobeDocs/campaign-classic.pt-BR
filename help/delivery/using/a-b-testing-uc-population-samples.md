---
product: campaign
title: Configurar amostras de população
description: Saiba como executar testes A/B por meio de um caso de uso dedicado
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: A/B Testing
role: User
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
TQID: https://experienceleague.adobe.com/HWbHtS5F-je1GiNdr25dD17W-MpJ-K3xp-T8kKC-c10
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 185
ht-degree: 100%

---

# Teste A/B: configurar amostras de população {#step-2--configuring-population-samples}

## Configurar a atividade de consulta {#configuring-the-query-activity}

* Clique duas vezes na atividade **[!UICONTROL Query]**.

  ![](assets/use_case_abtesting_createrecipients_001.png)

* Clique no link **[!UICONTROL Edit query]** e selecione o tipo de destinatários que deseja direcionar.

  ![](assets/use_case_abtesting_createrecipients_002.png)

* Vincule a atividade **[!UICONTROL Query]** à atividade **[!UICONTROL Split]**.

  ![](assets/use_case_abtesting_createrecipients_003.png)

## Configurar a atividade de divisão {#configuring-the-split-activity}

Esta atividade permite criar várias populações: a que recebe a entrega A, aquela que recebe a entrega B e a população restante. A utilização de seleção aleatória permite atingir apenas parte da população de cada entrega.

1. Criação da população A:

   * Clique duas vezes na atividade **[!UICONTROL Split]**.

     ![](assets/use_case_abtesting_createrecipients_004.png)

   * Na guia existente, altere o rótulo para a população A.

     ![](assets/use_case_abtesting_createrecipients_005.png)

   * Selecione a opção **[!UICONTROL Limit the selected records]**.

     ![](assets/use_case_abtesting_createrecipients_006.png)

   * Clique no link **[!UICONTROL Edit]**, selecione **[!UICONTROL Activate random sampling]** e clique em **[!UICONTROL Next]**.

     ![](assets/use_case_abtesting_createrecipients_007.png)

   * Defina o limite como 10% e clique em **[!UICONTROL Finish]**.

     ![](assets/use_case_abtesting_createrecipients_008.png)

1. Criação da população B:

   * Clique em **[!UICONTROL Add]** para criar uma nova guia para a população B.

     ![](assets/use_case_abtesting_createrecipients_009.png)

   * Limite a população para 10% como anteriormente.

     ![](assets/use_case_abtesting_createrecipients_010.png)

1. Criação da população restante:

   * Acesse a guia **[!UICONTROL General]**.

     ![](assets/use_case_abtesting_createrecipients_011.png)

   * Selecione **[!UICONTROL Generate complement]**.

     ![](assets/use_case_abtesting_createrecipients_012.png)

   * Altere o rótulo para especificar que esta população não inclui A nem B e clique em **[!UICONTROL OK]** para fechar a atividade.

     ![](assets/use_case_abtesting_createrecipients_013.png)

Agora você pode criar os dois modelos de entrega. [Saiba mais](a-b-testing-uc-delivery-templates.md)).
