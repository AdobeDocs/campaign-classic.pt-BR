---
solution: Campaign Classic
product: campaign
title: Introdução ao teste A/B
description: Saiba mais sobre o teste A/B no Campaign Classic.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 346b72d522c947b2a2552176b910ded8d622f3ab
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---


# Introdução ao teste A/B {#get-started-a-b-testing}

O teste A/B permite que você compare várias versões de um delivery entre si, a fim de identificar qual terá o maior impacto na população-alvo.

Para fazer isso, primeiro é necessário definir várias variantes do delivery. Cada variante é então enviada para amostras de população para determinar qual delas tem melhor desempenho, dependendo dos critérios de sua escolha (abre, reclamações de spam, cliques em um link específico, ...).

No exemplo abaixo, o público alvo do delivery foi dividido em dois grupos, cada um representando 50% da população-alvo. Cada grupo recebe duas versões do delivery com duas ofertas promocionais diferentes. Após o envio do delivery, conclui-se que a variante A teve um melhor desempenho, com base no número de cliques nas ofertas promocionais.

![](assets/a-b-testing-schema.png)

Com o Campaign Classic, o teste A/B é implementado por meio de workflows, onde você especifica a população a ser público alvo, bem como os grupos que receberão cada variante (consulte [Configurando um teste/b](../../delivery/using/configuring-a-b-testing.md)).

As principais etapas são:

1. **Direcione** a população desejada.
1. **Divida a** população em subconjuntos nos quais você testará as variantes do seu delivery.

   Por exemplo, você pode enviar uma versão de um delivery para uma pequena porção da população direcionada e outra versão para a população restante. Isso permite testar uma nova versão de um delivery em vez do delivery que geralmente é enviado para seus clientes. Você também pode dividir a população-alvo em 3 grupos para enviar a eles três versões diferentes de um delivery.

1. **Crie várias** versões do delivery correspondentes a cada subconjunto. A variante a ser testada pode ser o assunto, o conteúdo da mensagem, o nome do remetente etc.
1. Start o fluxo de trabalho, em seguida, use **logs do delivery** para analisar o comportamento dos subconjuntos com cada variante.

>[!NOTE]
>
>Os workflows também permitem que você automatize seus processos identificando automaticamente a variante do delivery que teve um melhor desempenho e, em seguida, enviando-a para a população restante. Para obter mais informações, consulte este [caso de uso ](../../delivery/using/a-b-testing-use-case.md) dedicado.
