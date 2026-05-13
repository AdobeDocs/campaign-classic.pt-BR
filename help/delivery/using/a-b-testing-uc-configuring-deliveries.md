---
product: campaign
title: Configurar entregas
description: Saiba como executar testes A/B por meio de um caso de uso dedicado
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: A/B Testing
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
TQID: https://experienceleague.adobe.com/7fr4R6dly8-CJh9XYRpAwus1-AUJaz496LOPrWebt0k
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 250
ht-degree: 100%

---

# Teste A/B: configurar as entregas no fluxo de trabalho {#step-4--configuring-the-deliveries-in-the-workflow}

Depois que [populações forem criadas](a-b-testing-uc-population-samples.md), você poderá configurar as entregas. Nesse caso de uso, as duas primeiras entregas permitem enviar conteúdo diferente às populações A e B. A terceira entrega é a de fallback: ela será enviada aos destinatários que não pertencerem a A nem B. O conteúdo será calculado por um script e será idêntico a A ou B, dependendo de qual deles obteve a maior taxa de abertura. Precisamos configurar um período de espera para a terceira entrega, para descobrir o resultado das entregas A e B. É por isso que a terceira entrega inclui uma atividade **[!UICONTROL Wait]**.

1. Vá para a atividade **[!UICONTROL Split]** e vincule a transição destinada à população A para uma das entregas do e-mail já no fluxo de trabalho.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. Clique duas vezes na entrega para abri-la.
1. Usando a lista suspensa, selecione o modelo para a entrega A.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. Clique em **[!UICONTROL Continue]** para visualizar a entrega e, em seguida, salve.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. Vincule a transição da atividade **[!UICONTROL Split]** destinada à população B para a segunda entrega de e-mail.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. Abra a entrega e selecione o modelo na entrega B e, em seguida, salve a entrega.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. Vincule a transição destinada à população restante para a atividade **[!UICONTROL Wait]**.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. Abra a atividade **[!UICONTROL Wait]** e configure um período de espera de 5 dias.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. Vincule a atividade **[!UICONTROL Wait]** à atividade **[!UICONTROL JavaScript code]**.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

Agora você pode criar o script. [Saiba mais](a-b-testing-uc-script.md).
