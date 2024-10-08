---
product: campaign
title: Caso de uso de teste A/B
description: Saiba como executar testes A/B por meio de um caso de uso dedicado
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: A/B Testing
role: User
exl-id: 4eb139a0-5342-4084-9f6d-d736e05bf1c6
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 100%

---

# Teste A/B: teste deste caso de uso {#ab-testing-use-case}

Nesse caso de uso, vamos comparar dois conteúdos de entrega de e-mail por meio de um workflow para construção do target. A mensagem e o texto são idênticos nas duas entregas: apenas o layout é alterado.

A população direcionada é dividida em três grupos: dois grupos de teste e a população restante. Uma versão diferente da entrega é enviada para cada grupo de teste.

Após a entrega, um período de espera de cinco dias é configurado antes de coletar os resultados das melhores taxas de abertura. O conteúdo da entrega com a pontuação mais alta é então recuperado por um script e enviado à população que não foi usada como um grupo de teste.

Observe que os critérios que decide qual entrega é o melhor pode ser alterado para atender às suas necessidades. Pode ser a taxa de abertura, a taxa de cliques, a taxa de subscrição, o reatividade, etc.

Além disso, o teste detalhado nesse caso de uso aborda apenas duas entregas, mas é possível testar quantas versões forem necessárias. Basta adicionar atividades ao fluxo de trabalho.

As principais etapas para executar esse caso de uso são:

* [Etapa 1: criar um fluxo de trabalho de direcionamento](a-b-testing-uc-targeting-workflow.md)
* [Etapa 2: configurar amostras de população](a-b-testing-uc-population-samples.md)
* [Etapa 3: criar dois modelos de entrega](a-b-testing-uc-delivery-templates.md)
* [Etapa 4: configurar as entregas no fluxo de trabalho](a-b-testing-uc-configuring-deliveries.md)
* [Etapa 5: criar o script](a-b-testing-uc-script.md)
* [Etapa 6: definir a entrega final](a-b-testing-uc-final-delivery.md)
* [Etapa 7: iniciar o fluxo de trabalho](a-b-testing-uc-start-workflow.md)
* [Etapa 8: analisar o resultado](a-b-testing-uc-analyzing.md)

**Tópicos relacionados:**

* [Introdução ao teste A/B](get-started-a-b-testing.md)
* [Configurar teste A/B](configuring-a-b-testing.md)
