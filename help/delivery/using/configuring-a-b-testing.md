---
product: campaign
title: Configurar teste A/B
description: Saiba como configurar o teste A/B no Campaign
badge-v8: label="Também se aplica à versão v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: A/B Testing
role: User
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 98%

---

# Configurar teste A/B {#configuring-a-b-testing}

Esta seção detalha como criar um fluxo de trabalho para executar um teste A/B.

1. Crie um novo fluxo de trabalho e configure uma atividade [Query](../../workflow/using/query.md) para direcionar a população desejada.

1. Adicione uma atividade [Dividir](../../workflow/using/split.md) para dividir a população direcionada em vários subconjuntos.

1. Abra a atividade e configure cada subconjunto de acordo com suas necessidades. Para obter mais informações sobre como configurar uma atividade **[!UICONTROL Split]**, consulte [esta seção](../../workflow/using/split.md).

   Neste exemplo, queremos testar dois novos assuntos para um informativo, apresentando cada um deles a 10% da população direcionada.

   ![](assets/ab-testing-split.png)

1. Adicione uma transição para enviar ao restante da população o informativo com o assunto atual. Para fazer isso, ative a opção **[!UICONTROL Generate complement]** na guia **[!UICONTROL General]**.

   ![](assets/ab-testing-complement.png)

1. Para cada subconjunto, adicione a versão da entrega a ser testada.

   ![](assets/ab-testing-delivery.png)

Agora, você pode iniciar o fluxo de trabalho. Depois que as entregas forem enviadas, você poderá rastrear o comportamento dos três subconjuntos nos logs da entrega para ver qual assunto foi o mais bem-sucedido.

Os workflows também permitem que você automatize seus processos identificando automaticamente a variante da entrega que teve melhor desempenho e, em seguida, enviando-a à população restante. Para saber mais, consulte este [caso de uso](a-b-testing-use-case.md) dedicado.
