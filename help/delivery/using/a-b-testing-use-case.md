---
solution: Campaign Classic
product: campaign
title: Sobre este caso de uso
description: Saiba como executar testes A/B por meio de um caso de uso dedicado.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 50a10e16f320a67cb4ad0e31c1cbe8a9365b7887
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 51%

---


# Sobre este caso de uso {#about-use-case}

Nesse caso de uso, vamos comparar dois conteúdos de delivery de e-mail por meio de um workflow para construção do target. A mensagem e o texto são idênticos nas duas remessas: apenas o layout é alterado.

A população direcionada é dividida em três grupos: dois grupos de teste e a população restante. Uma versão diferente da delivery é enviada para cada grupo de teste.

Após a delivery, um período de espera de 5 dias é configurado antes de coletar os resultados das melhores taxas aberturas. O conteúdo do delivery com a pontuação mais alta é recuperado por um script e enviado para a população que não foi usada como grupo de teste.

Observe que os critérios que decide qual delivery é o melhor pode ser alterado para atender às suas necessidades. Pode ser a taxa de abertura, a taxa de cliques, a taxa de subscrição, o reatividade, etc.

Além disso, o teste detalhado neste caso de uso relacionou-se apenas a dois delivery, mas você pode testar quantas versões forem necessárias. Basta adicionar atividades ao workflow.

As principais etapas para executar esse caso de uso são:

* [Etapa 1: Criar um fluxo de trabalho de definição de metas](../../delivery/using/a-b-testing-uc-targeting-workflow.md)
* [Etapa 2: Configurar amostras de população](../../delivery/using/a-b-testing-uc-population-samples.md)
* [Etapa 3: Criar dois templates do delivery](../../delivery/using/a-b-testing-uc-delivery-templates.md)
* [Etapa 4: Configurar os delivery no fluxo de trabalho](../../delivery/using/a-b-testing-uc-configuring-deliveries.md)
* [Etapa 5: Criar o script](../../delivery/using/a-b-testing-uc-script.md)
* [Etapa 6: Definir o delivery final](../../delivery/using/a-b-testing-uc-final-delivery.md)
* [Etapa 7: Start do fluxo de trabalho](../../delivery/using/a-b-testing-uc-start-workflow.md)
* [Etapa 8: Analisar o resultado](../../delivery/using/a-b-testing-uc-analyzing.md)

**Tópicos relacionados:**

* [Introdução ao teste A/B](../../delivery/using/get-started-a-b-testing.md)
* [Configuração do teste A/B](../../delivery/using/configuring-a-b-testing.md)
