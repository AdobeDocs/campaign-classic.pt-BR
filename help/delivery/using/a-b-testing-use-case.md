---
product: campaign
title: Caso de uso de teste A/B
description: Saiba como executar testes A/B por meio de um caso de uso dedicado
feature: A/B Testing
exl-id: 4eb139a0-5342-4084-9f6d-d736e05bf1c6
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: ht
source-wordcount: '246'
ht-degree: 100%

---

# Teste A/B deste caso de uso {#ab-testing-use-case}

![](../../assets/common.svg)

Nesse caso de uso, vamos comparar dois conteúdos de delivery de e-mail por meio de um workflow para construção do target. A mensagem e o texto são idênticos nas duas remessas: apenas o layout é alterado.

A população direcionada é dividida em três grupos: dois grupos de teste e a população restante. Uma versão diferente do delivery é enviado para cada grupo de teste.

Após o delivery, um período de espera de cinco dias é configurado antes de coletar os resultados das melhores taxas de abertura. O conteúdo do delivery com a pontuação mais alta é então recuperado por um script e enviado à população que não foi usada como um grupo de teste.

Observe que os critérios que decide qual delivery é o melhor pode ser alterado para atender às suas necessidades. Pode ser a taxa de abertura, a taxa de cliques, a taxa de subscrição, o reatividade, etc.

Além disso, o teste detalhado nesse caso de uso aborda apenas dois deliveries, mas é possível testar quantas versões forem necessárias. Basta adicionar atividades ao fluxo de trabalho.

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
