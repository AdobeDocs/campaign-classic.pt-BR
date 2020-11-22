---
solution: Campaign Classic
product: campaign
title: Sobre o gestor de resposta
description: Sobre o gestor de resposta
audience: campaign
content-type: reference
topic-tags: response-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 100%

---


# Sobre o gestor de resposta{#about-response-manager}

## Objetivos {#objectives}

O Adobe Campaign oferece um aplicativo de gestor de respostas (Gestor de Resposta) que permite medir o sucesso e a lucratividade das campanhas de marketing ou apresentações de ofertas de todos os canais de comunicação (email, celular, telefone, mala direta, fax, agência, etc.).

## Conceito de Hipótese {#hypothesis-concept}

A hipótese pode ser configurada por um determinado período a partir da data de contato para deduzir o comportamento desses destinos após receber um delivery. Essas hipóteses são baseadas em uma tabela de **transaction** que salva as compras e os seus detalhes.

As hipósteses são limitadas no tempo e podem ser aplicadas a um grupo de controle a ser comparado à população do target. Os resultados da hipótese são fornecidos por **indicatores** atualizados automaticamente após a conclusão do cálculo. O ROI vinculado à hipótese é considerado nos relatórios da campanha.

Além disso, os **relatórios** fornecidos com o Gestor de resposta permitem resumir as informações vinculadas ao aumento do faturamento, cálculo de margem, assim como o ROI do delivery ou da oferta.

Além disso, graças às linhas de detalhes da compra, é possível especificar a hipótese para focar somente em um produto específico, por exemplo.

Por exemplo, um delivery promovendo um item, no qual é possível avaliar a receita gerada. Nós aplicamos a hipótese de que qualquer recipient que tenha comprado pelo menos um item no mês seguinte ao acionamento do delivery tenha reagido a ação. O gestor de resposta determina, com base nesta hipótese, quais linhas da solicitação de compra devem ser atribuídas a ele. Em seguida, com base nisso, é possível determinar a receita resultante como a soma dessas linhas.

>[!CAUTION]
>
>O Gestor de Resposta é uma opção do **[!UICONTROL Campaign]**. Verifique o contrato de licença.

Também é possível calcular todas as reações da família do recipient que recebeu o delivery ou a oferta.

Cada hipótese está vinculada a uma única tabela de transação. Um delivery ou oferta pode ser vinculado a várias hipóteses.

## Método {#method}

Antes de começar a usar o Gestor de Resposta, consulte [Configuração](../../campaign/using/configuration.md) e execute as configurações necessárias.

Para iniciar uma hipótese em um delivery ou oferta, defina o contexto em um template que deve ser usado em cada hipótese criada.

Aplique o seguinte processo para definir e criar uma hipótese de medição:

1. Defina um modelo de hipótese. Consulte [Criação de um modelo de hipótese](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model).
1. Crie uma ou mais hipóteses em um delivery existente. Consulte [Referenciar uma hipótese em um delivery de campanha](../../campaign/using/creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery).

   ou

   Crie uma ou mais hipóteses em ofertas. Consulte [Criação de uma hipótese em uma oferta](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-an-offer).

1. Verifique os resultados da hipótese. Consulte [Rastreamento de hipótese](../../campaign/using/hypothesis-tracking.md).
1. Se necessário, reinicie a hipótese. Consulte [Criação de uma hipótese em tempo real em um delivery](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery).

