---
product: campaign
title: Definir o delivery final
description: Saiba como executar testes A/B por meio de um caso de uso dedicado
feature: A/B Testing
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: ht
source-wordcount: '108'
ht-degree: 100%

---

# Definir a entrega final {#step-6--defining-the-final-delivery}

![](../../assets/common.svg)

Depois que o script for criado para selecionar o vencedor do teste A/B, será possível definir os parâmetros do delivery final.

1. Conecte a atividade **[!UICONTROL JavaScript code]** à atividade restante **[!UICONTROL Delivery]**.
1. Abra a atividade **[!UICONTROL Delivery]**.
1. Desmarque a opção **[!UICONTROL Generate an outbound transition]** para finalizar o workflow com esta atividade.
1. Deixe as outras opções em seus valores padrão.

   ![](assets/ab_test_final_delivery.png)

Ao preparar o delivery especificado na transição (definido por meio da atividade **[!UICONTROL Javascript Code]**), é possível aprovar e iniciar o envio, conforme descrito na próxima etapa.

Agora, você pode iniciar o fluxo de trabalho. [Saiba mais](a-b-testing-uc-start-workflow.md).
