---
solution: Campaign Classic
product: campaign
title: Configuração de amostras de população
description: Saiba como executar testes A/B por meio de um caso de uso dedicado.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: ht
source-git-commit: 50a10e16f320a67cb4ad0e31c1cbe8a9365b7887
workflow-type: ht
source-wordcount: '174'
ht-degree: 100%

---


# Configuração de amostras de população {#step-2--configuring-population-samples}

## Configuração da atividade de Query {#configuring-the-query-activity}

* Clique duas vezes na atividade **[!UICONTROL Query]**.

   ![](assets/use_case_abtesting_createrecipients_001.png)

* Clique no link **[!UICONTROL Edit query]** e selecione o tipo de recipients que deseja direcionar.

   ![](assets/use_case_abtesting_createrecipients_002.png)

* Vincule a atividade **[!UICONTROL Query]** à atividade **[!UICONTROL Split]**.

   ![](assets/use_case_abtesting_createrecipients_003.png)

## Configuração da atividade Split {#configuring-the-split-activity}

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

Agora você pode criar os dois modelos do delivery (consulte [Etapa 3: criar dois modelos do delivery](../../delivery/using/a-b-testing-uc-delivery-templates.md)).
