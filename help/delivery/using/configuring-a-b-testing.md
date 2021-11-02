---
product: campaign
title: Configuração de teste A/B
description: Saiba como configurar o teste A/B no Campaign Classic.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: ht
source-wordcount: '212'
ht-degree: 100%

---

# Configuração de teste A/B {#configuring-a-b-testing}

![](../../assets/common.svg)

Esta seção detalha como criar um fluxo de trabalho para executar um teste A/B.

1. Crie um novo fluxo de trabalho e configure uma atividade [Query](../../workflow/using/query.md) para direcionar a população desejada.

1. Adicione uma atividade [Dividir](../../workflow/using/split.md) para dividir a população direcionada em vários subconjuntos.

1. Abra a atividade e configure cada subconjunto de acordo com suas necessidades. Para obter mais informações sobre como configurar uma atividade **[!UICONTROL Split]**, consulte [esta seção](../../workflow/using/split.md).

   Neste exemplo, queremos testar dois novos assuntos para um informativo, apresentando cada um deles a 10% da população direcionada.

   ![](assets/ab-testing-split.png)

1. Adicione uma transição para enviar ao restante da população o informativo com o assunto atual. Para fazer isso, ative a opção **[!UICONTROL Generate complement]** na guia **[!UICONTROL General]**.

   ![](assets/ab-testing-complement.png)

1. Para cada subconjunto, adicione a versão do delivery a ser testada.

   ![](assets/ab-testing-delivery.png)

Agora, você pode iniciar o fluxo de trabalho. Depois que os deliveries forem enviados, você poderá rastrear o comportamento dos três subconjuntos nos logs do delivery para ver qual assunto foi o mais bem-sucedido.

Os workflows também permitem que você automatize seus processos identificando automaticamente a variante do delivery que teve melhor desempenho e, em seguida, enviando-a à população restante. Para saber mais, consulte este [caso de uso](a-b-testing-use-case.md) dedicado.
