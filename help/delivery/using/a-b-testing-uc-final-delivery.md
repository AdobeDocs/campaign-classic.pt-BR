---
product: campaign
title: Definir a entrega final
description: Saiba como executar testes A/B por meio de um caso de uso dedicado
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: A/B Testing
role: User
exl-id: bc23a444-a872-48fb-8bba-64b301541089
TQID: https://experienceleague.adobe.com/P0oI4PhLZB-iBFDrEJ2Qy7eIOPYWSWYu5s6j3yCN6j0
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
source-wordcount: 119
ht-degree: 100%

---

# Teste A/B: definir a entrega final {#step-6--defining-the-final-delivery}

Depois que o script for criado para selecionar o vencedor do teste A/B, será possível definir os parâmetros da entrega final.

1. Conecte a atividade **[!UICONTROL JavaScript code]** à atividade restante **[!UICONTROL Delivery]**.
1. Abra a atividade **[!UICONTROL Delivery]**.
1. Desmarque a opção **[!UICONTROL Generate an outbound transition]** para finalizar o fluxo de trabalho com esta atividade.
1. Deixe as outras opções em seus valores padrão.

   ![](assets/ab_test_final_delivery.png)

Ao preparar a entrega especificada na transição (definido por meio da atividade **[!UICONTROL Javascript Code]**), é possível aprovar e iniciar o envio, conforme descrito na próxima etapa.

Agora, você pode iniciar o fluxo de trabalho. [Saiba mais](a-b-testing-uc-start-workflow.md).
