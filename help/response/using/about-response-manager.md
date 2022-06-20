---
product: campaign
title: Sobre o gestor de resposta
description: Sobre o gestor de resposta
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: d36e1881726af6238c4e0caecb7b299b594691f2
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Introdução ao Gestor de resposta do Campaign{#about-response-manager}

![](../../assets/common.svg)

O Adobe Campaign oferece um complemento de Gerenciamento de resposta que permite medir o sucesso e a lucratividade de campanhas de marketing ou propostas de oferta em canais de comunicação: email, celular, correspondência direta etc.

## Hipótese {#hypothesis-concept}

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

## Etapas de implementação {#method}

Antes de começar a usar o Gestor de Resposta, consulte [Configuração](configuration.md) e execute as configurações necessárias.

Para iniciar uma hipótese em um delivery ou oferta, defina o contexto em um template que deve ser usado em cada hipótese criada.

Aplique o seguinte processo para definir e criar uma hipótese de medição:

1. Defina um modelo de hipótese. [Saiba mais](hypothesis-templates.md#creating-a-hypothesis-model)
1. Crie uma ou mais hipóteses em uma entrega existente. [Saiba mais](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   ou

   Crie uma ou mais hipóteses em ofertas. [Saiba mais](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. Verifique os resultados da hipótese. [Saiba mais](hypothesis-tracking.md)
1. Se necessário, reinicie a hipótese. [Saiba mais](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
