---
product: campaign
title: Definição do delivery final
description: Saiba como executar testes A/B por meio de um caso de uso dedicado.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 100%

---

# Definição do delivery final {#step-6--defining-the-final-delivery}

Depois que o script for criado para selecionar o vencedor do teste A/B, será possível definir os parâmetros do delivery final.

1. Conecte a atividade **[!UICONTROL JavaScript code]** à atividade restante **[!UICONTROL Delivery]**.
1. Abra a atividade **[!UICONTROL Delivery]**.
1. Desmarque a opção **[!UICONTROL Generate an outbound transition]** para finalizar o workflow com esta atividade.
1. Deixe as outras opções em seus valores padrão.

   ![](assets/ab_test_final_delivery.png)

Ao preparar o delivery especificado na transição (definido por meio da atividade **[!UICONTROL Javascript Code]**), é possível aprovar e iniciar o envio, conforme descrito na próxima etapa.

Agora você pode iniciar o fluxo de trabalho (consulte [Etapa 7: iniciar o fluxo de trabalho](../../delivery/using/a-b-testing-uc-start-workflow.md)).
