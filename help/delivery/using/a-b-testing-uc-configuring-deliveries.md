---
solution: Campaign Classic
product: campaign
title: Configuração dos deliveries
description: Saiba como executar testes A/B por meio de um caso de uso dedicado.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: ht
source-git-commit: 50a10e16f320a67cb4ad0e31c1cbe8a9365b7887
workflow-type: ht
source-wordcount: '242'
ht-degree: 100%

---


# Configuração dos deliveries no fluxo de trabalho {#step-4--configuring-the-deliveries-in-the-workflow}

A próxima etapa é configurar as deliveries. Estão destinados às três populações criadas na fase anterior: [Etapa 2: configuração de amostras de população](#step-2--configuring-population-samples). As duas primeiras deliverys permitem enviar conteúdo diferente para a população A e B. A terceiro delivery é destinada à população que não recebeu A nem B. O conteúdo será calculado por um script e será idêntico a A ou ao B, dependendo de qual deles obteve a maior taxa de abertura. Precisamos configurar um período de espera para o terceiro delivery, para descobrir o resultado dos deliveries A e B. É por isso que o terceiro delivery inclui uma atividade **[!UICONTROL Wait]**.

1. Vá para a atividade **[!UICONTROL Split]** e vincule a transição destinada à população A para uma das deliveries do e-mail já no workflow.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. Clique duas vezes na delivery para abri-la.
1. Usando a lista suspensa, selecione o template para a delivery A.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. Clique em **[!UICONTROL Continue]** para visualizar o delivery e, em seguida, a salve.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. Vincule a transição da atividade **[!UICONTROL Split]** destinada à população B para o segundo delivery de e-mail.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. Abra delivery e selecione o template na delivery B e, em seguida, salve a delivery.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. Vincule a transição destinada à população restante para a atividade **[!UICONTROL Wait]**.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. Abra a atividade **[!UICONTROL Wait]** e configure um período de espera de 5 dias.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. Vincule a atividade **[!UICONTROL Wait]** à atividade **[!UICONTROL JavaScript code]**.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

Agora você pode criar o script (consulte [Etapa 5: criar o script](../../delivery/using/a-b-testing-uc-script.md)).
