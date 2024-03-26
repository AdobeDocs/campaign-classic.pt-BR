---
product: campaign
title: Introdução ao teste A/B
description: Saiba mais sobre o teste A/B no Campaign
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: A/B Testing
role: User
exl-id: ae046ef6-d850-4222-b82c-8ef5b3da7037
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 100%

---

# Introdução ao teste A/B {#get-started-a-b-testing}


O teste A/B permite que você compare várias versões de uma entrega entre si, a fim de identificar qual terá o maior impacto na população direcionada.

Para fazer isso, primeiro é necessário definir diversas variantes da entrega. Cada variante é então enviada para amostras de população a fim de determinar qual delas tem melhor desempenho, dependendo dos critérios de sua escolha (aberturas, reclamações de spam, cliques em um link específico etc.).

No exemplo abaixo, o target da entrega foi dividido em dois grupos, cada um representando 50% da população direcionada. Cada grupo recebe duas versões da entrega com duas ofertas promocionais diferentes. Após o envio da entrega, conclui-se que a variante A teve melhor desempenho, com base no número de cliques nas ofertas promocionais.

![](assets/a-b-testing-schema.png)

Com o Campaign Classic, o teste A/B é implementado por meio de workflows, em que você especifica a população a ser direcionada, bem como os grupos que receberão cada variante (consulte [Configurar um teste A/B](configuring-a-b-testing.md)).

As principais etapas são:

1. **Direcionar** a população desejada.
1. **Dividir a população** em subconjuntos nos quais você testará as variantes da entrega.

   Por exemplo, você pode enviar uma versão de uma entrega a uma pequena parte da população direcionada e outra versão à a população restante. Isso permite testar uma nova versão de uma entrega em vez da entrega que geralmente é enviado a seus clientes. Você também pode dividir a população direcionada em três grupos para enviar a eles três versões diferentes de uma entrega.

1. **Crie várias versões** da entrega correspondentes a cada subconjunto. A variante a ser testada pode ser o assunto, o conteúdo da mensagem, o nome do remetente etc.
1. Inicie o fluxo de trabalho e, em seguida, use os **logs da entrega** para analisar o comportamento dos subconjuntos com cada variante.

>[!NOTE]
>
>Os workflows também permitem que você automatize seus processos identificando automaticamente a variante da entrega que teve melhor desempenho e, em seguida, enviando-a à população restante. Para saber mais, consulte este [caso de uso](a-b-testing-use-case.md) dedicado.
