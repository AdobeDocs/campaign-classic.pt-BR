---
solution: Campaign Classic
product: campaign
title: Sobre este caso de uso
description: Saiba como executar testes A/B por meio de um caso de uso dedicado.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 346b72d522c947b2a2552176b910ded8d622f3ab
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 52%

---


# Sobre este caso de uso {#about-use-case}

Nesse caso de uso, vamos comparar dois conteúdos de delivery de e-mail por meio de um workflow para construção do target. A mensagem e o texto são idênticos nas duas remessas: apenas o layout é alterado.

A população direcionada é dividida em três grupos: dois grupos de teste e a população restante. Uma versão diferente da delivery é enviada para cada grupo de teste.

Após a delivery, um período de espera de 5 dias é configurado antes de coletar os resultados das melhores taxas aberturas. O conteúdo do delivery com a pontuação mais alta é recuperado por um script e enviado para a população que não foi usada como grupo de teste.

Observe que os critérios que decide qual delivery é o melhor pode ser alterado para atender às suas necessidades. Pode ser a taxa de abertura, a taxa de cliques, a taxa de subscrição, o reatividade, etc.

Além disso, o teste detalhado neste caso de uso relacionou-se apenas a dois delivery, mas você pode testar quantas versões forem necessárias. Basta adicionar atividades ao workflow.

As principais etapas para executar esse caso de uso são:

* [Etapa 1: Criar um fluxo de trabalho de definição de metas](#step-1--creating-a-targeting-workflow)
* [Etapa 2: Configurar amostras de população](#step-2--configuring-population-samples)
* [Etapa 3: Criar dois templates do delivery](#step-3--creating-two-delivery-templates)
* [Etapa 4: Configurar os delivery no fluxo de trabalho](#step-4--configuring-the-deliveries-in-the-workflow)
* [Etapa 5: Criar o script](#step-5--creating-the-script)
* [Etapa 7: Start do fluxo de trabalho](#step-7--starting-the-workflow)
* [Etapa 8: Analise o resultado](#step-8--analyzing-the-result).

**Tópicos relacionados:**

* [Introdução ao teste A/B](../../delivery/using/get-started-a-b-testing.md)
* [Configuração do teste A/B](../../delivery/using/configuring-a-b-testing.md)
