---
product: campaign
title: Configuração de amostras de população
description: Saiba como executar testes A/B por meio de um caso de uso dedicado.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 100%

---

# Configurar amostras de população {#step-2--configuring-population-samples}

![](../../assets/common.svg)

## Configurar a atividade de consulta {#configuring-the-query-activity}

* Clique duas vezes na atividade **[!UICONTROL Query]**.

   ![](assets/use_case_abtesting_createrecipients_001.png)

* Clique no link **[!UICONTROL Edit query]** e selecione o tipo de recipients que deseja direcionar.

   ![](assets/use_case_abtesting_createrecipients_002.png)

* Vincule a atividade **[!UICONTROL Query]** à atividade **[!UICONTROL Split]**.

   ![](assets/use_case_abtesting_createrecipients_003.png)

## Configurar a atividade de divisão {#configuring-the-split-activity}

Esta atividade permite criar várias populações: a que recebe a delivery A, aquela que recebe a delivery B e a população restante. A utilização de seleção aleatória permite atingir apenas parte da população de cada delivery.

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
