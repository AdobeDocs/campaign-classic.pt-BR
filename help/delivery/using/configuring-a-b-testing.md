---
solution: Campaign Classic
product: campaign
title: Configuração do teste A/B
description: Saiba como configurar o teste A/B no Campaign Classic.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: a341980e9d940857388bb2755e5eaa74824cf6ea
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Configurando testes A/B {#configuring-a-b-testing}

Esta seção detalha como criar um fluxo de trabalho para executar um teste A/B.

1. Crie um novo fluxo de trabalho e configure uma atividade [Query](../../workflow/using/query.md) para público alvo da população desejada.

1. Adicione uma atividade [Dividir](../../workflow/using/split.md) para dividir a população direcionada em vários subconjuntos.

1. Abra a atividade e configure cada subconjunto de acordo com suas necessidades. Para obter mais informações sobre como configurar uma atividade **[!UICONTROL Split]**, consulte [esta seção](../../workflow/using/split.md).

   Neste exemplo, queremos testar 2 novos assuntos para um boletim informativo apresentando cada um deles a 10% da população-alvo.

   ![](assets/ab-testing-split.png)

1. Adicione uma transição para enviar ao restante da população o boletim informativo com o assunto atual. Para fazer isso, ative a opção **[!UICONTROL Generate complement]** na guia **[!UICONTROL General]**.

   ![](assets/ab-testing-complement.png)

1. Para cada subconjunto, adicione a versão do delivery a ser testada.

   ![](assets/ab-testing-delivery.png)

Agora você pode start o fluxo de trabalho. Depois que os delivery forem enviados, você poderá rastrear o comportamento dos três subconjuntos nos logs do delivery, para ver qual assunto foi o mais bem-sucedido.

Os workflows também permitem que você automatize seus processos identificando automaticamente a variante do delivery que teve um melhor desempenho e, em seguida, enviando-a para a população restante. Para obter mais informações, consulte este [caso de uso ](../../delivery/using/a-b-testing-use-case.md) dedicado.
