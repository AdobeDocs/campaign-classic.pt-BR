---
product: campaign
title: Sobre o gestor de resposta
description: Sobre o gestor de resposta
feature: Campaigns
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
TQID: https://experienceleague.adobe.com/ScwRjZlHoAjXQBxig5Mt3HuNkpPiZ9J-FQTm9FuCY4g
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: a4671286-a59f-47e3-b97b-90627a1977d5
subfeature_v2: id: d72afaa0-c842-48c8-9a3c-51b7911edc1b
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 417
ht-degree: 100%

---

# Introdução ao Gestor de resposta do Campaign{#about-response-manager}



O Adobe Campaign oferece um complemento de Gerenciamento de resposta que permite medir o sucesso e a lucratividade de campanhas de marketing ou propostas de oferta em canais de comunicação: email, celular, correspondência direta etc.

## Hipótese {#hypothesis-concept}

A hipótese pode ser configurada por um determinado período a partir da data de contato para deduzir o comportamento desses destinos após receber uma entrega. Essas hipóteses são baseadas em uma tabela de **transaction** que salva as compras e os seus detalhes.

As hipósteses são limitadas no tempo e podem ser aplicadas a um grupo de controle a ser comparado à população do target. Os resultados da hipótese são fornecidos por **indicatores** atualizados automaticamente após a conclusão do cálculo. O ROI vinculado à hipótese é considerado nos relatórios da campanha.

Além disso, os **relatórios** fornecidos com o Gestor de resposta permitem resumir as informações vinculadas ao aumento do faturamento, cálculo de margem, assim como o ROI da entrega ou da oferta.

Além disso, graças às linhas de detalhes da compra, é possível especificar a hipótese para focar somente em um produto específico, por exemplo.

Por exemplo, numa entrega promovendo um item, queremos avaliar a receita gerada. Nós aplicamos a hipótese de que qualquer destinatário que tenha comprado pelo menos um item no mês seguinte ao acionamento da entrega tenha reagido a ação. O gestor de resposta determina, com base nesta hipótese, quais linhas da solicitação de compra devem ser atribuídas a ele. Em seguida, com base nisso, é possível determinar a receita resultante como a soma dessas linhas.

>[!CAUTION]
>
>O Gestor de Resposta é uma opção do **[!UICONTROL Campaign]**. Verifique o contrato de licença.

Também é possível calcular todas as reações da família do destinatário que recebeu a entrega ou a oferta.

Cada hipótese está vinculada a uma única tabela de transação. Um entrega ou oferta podem ser vinculadas a várias hipóteses.

## Etapas de implementação {#method}

Antes de começar a usar o Gestor de Resposta, consulte [Configuração](configuration.md) e execute as configurações necessárias.

Para iniciar uma hipótese em uma entrega ou oferta, defina o contexto em um modelo que deve ser usado em cada hipótese criada.

Aplique o seguinte processo para definir e criar uma hipótese de medição:

1. Defina um modelo de hipótese. [Saiba mais](hypothesis-templates.md#creating-a-hypothesis-model)
1. Crie uma ou mais hipóteses em uma entrega existente. [Saiba mais](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   ou

   Crie uma ou mais hipóteses em ofertas. [Saiba mais](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. Verifique os resultados da hipótese. [Saiba mais](hypothesis-tracking.md)
1. Se necessário, reinicie a hipótese. [Saiba mais](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
