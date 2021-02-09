---
solution: Campaign Classic
product: campaign
title: Definição da delivery final
description: Saiba como executar testes A/B por meio de um caso de uso dedicado.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 177b4e74c75e4fcca70dc90b5ff2c0406181e0f7
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 88%

---


# Definição da delivery final {#step-6--defining-the-final-delivery}

Depois que o script for criado para selecionar o vencedor do teste A/B, é possível definir os parâmetros da delivery final.

1. Conecte a atividade **[!UICONTROL JavaScript code]** à atividade restante **[!UICONTROL Delivery]**.
1. Abra a atividade **[!UICONTROL Delivery]**.
1. Desmarque a opção **[!UICONTROL Generate an outbound transition]** para finalizar o workflow com esta atividade.
1. Deixe as outras opções em seus valores padrão.

   ![](assets/ab_test_final_delivery.png)

Ao preparar o delivery especificado na transição (definido por meio da atividade **[!UICONTROL Javascript Code]**), é possível aprovar e iniciar o envio, conforme descrito na próxima etapa.
