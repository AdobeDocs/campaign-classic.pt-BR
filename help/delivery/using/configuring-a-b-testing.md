---
product: campaign
title: Configurar teste A/B
description: Saiba como configurar o teste A/B no Campaign
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: A/B Testing
role: User
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
TQID: https://experienceleague.adobe.com/PHIsuJZ-o5mBRAPggyVYdzS7PBXL9GYCBc6Fr56ur5Q
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 260
ht-degree: 100%

---

# Configurar teste A/B {#configuring-a-b-testing}

Esta seção detalha como criar um fluxo de trabalho para executar um teste A/B.

1. Crie um novo fluxo de trabalho e configure uma atividade de consulta para direcionar a população desejada. Consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html?lang=pt-BR){target="_blank"}.

1. Adicione uma atividade Dividir para dividir a população direcionada em vários subconjuntos. Consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html?lang=pt-BR){target="_blank"}.

1. Abra a atividade e configure cada subconjunto de acordo com suas necessidades. Para obter mais informações sobre como configurar uma atividade **[!UICONTROL Split]**, consulte [esta seção](../../workflow/using/split.md).

   Neste exemplo, queremos testar dois novos assuntos para um informativo, apresentando cada um deles a 10% da população direcionada.

   ![](assets/ab-testing-split.png)

1. Adicione uma transição para enviar ao restante da população o informativo com o assunto atual. Para fazer isso, ative a opção **[!UICONTROL Generate complement]** na guia **[!UICONTROL General]**.

   ![](assets/ab-testing-complement.png)

1. Para cada subconjunto, adicione a versão da entrega a ser testada.

   ![](assets/ab-testing-delivery.png)

Agora, você pode iniciar o fluxo de trabalho. Depois que as entregas forem enviadas, você poderá rastrear o comportamento dos três subconjuntos nos logs da entrega para ver qual assunto foi o mais bem-sucedido.

Os fluxos de trabalho também permitem que você automatize seus processos identificando automaticamente a variante da entrega que teve melhor desempenho e, em seguida, enviando-a à população restante. Para saber mais, consulte este [caso de uso](a-b-testing-use-case.md) dedicado.
