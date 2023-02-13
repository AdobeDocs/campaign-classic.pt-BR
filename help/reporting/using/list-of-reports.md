---
product: campaign
title: Lista de relatórios
description: Lista de relatórios
feature: Reporting
exl-id: c01f4850-ab17-44ac-a5e0-ff082ec206b3
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 100%

---

# Lista de relatórios{#list-of-reports}

![](../../assets/common.svg)

## Relatórios sobre deliveries {#reports-on-deliveries}

Os relatórios internos fornecidos pelo Adobe Campaign podem ser encontrados na tabela abaixo.

Para obter mais informações sobre o conteúdo desses relatórios, consulte [esta seção](../../reporting/using/delivery-reports.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Rótulo e nome interno</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Atividades do usuário (recipientActivity)<br /> </td> 
   <td> Detalhamento de aberturas, cliques e transações por período de tempo.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Taxa de transferência de delivery (produtividade)<br /> </td> 
   <td> Gráficos de taxa de transferência de delivery, em mensagens/hora e Mbits/s.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Falhas e devoluções (erros)<br /> </td> 
   <td> Devoluções e não entregues por causa e domínio.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Indicadores de rastreamento (deliveryFeedback)<br /> </td> 
   <td> Resumo dos principais indicadores para rastrear o comportamento do recipient.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Indicadores de rastreamento (mobileAppDeliveryFeedback)<br /> </td> 
   <td> Indicadores de rastreamento de um delivery para um aplicativo móvel.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Navegadores (browserStatistics)<br /> </td> 
   <td> Estatísticas em navegadores usados por recipients que clicaram em mensagens.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Compartilhamento para redes sociais (deliveryForward)<br /> </td> 
   <td> Compartilhamento de atividades e estatísticas de aberturas de email.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Hot clicks (hoturls)<br /> </td> 
   <td> Exibe a mensagem e as taxas de clique sobrepostas.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Relatório Hipótese (deliveryHypothesis)<br /> </td> 
   <td> Exibe o resumo das medidas na hipótese de delivery.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Estatísticas de delivery (statisticsPerDelivery)<br /> </td> 
   <td> Estatísticas (mensagens processadas, mensagens enviadas, devoluções permanentes, devoluções temporárias, cliques, unsubscriptions) por domínio de email.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Estatísticas de atividades de compartilhamento (forwardActivities)<br /> </td> 
   <td> Análise de atividades de compartilhamento, aberturas e subscrições por período de tempo.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Estatísticas de rastreamento (trackingStatistics)<br /> </td> 
   <td> Relatório de aberturas, cliques e taxas de transação.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Resumo do delivery (deliverySending)<br /> </td> 
   <td> Resumo dos indicadores de delivery: target, exclusão e mensagens enviadas.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Resumo do delivery (deliveryStatistics)<br /> </td> 
   <td> Tabela de resumo para deliveries selecionados: targets, exclusões e mensagens enviadas.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Sistemas operacionais (osStatistics)<br /> </td> 
   <td> Estatísticas dos sistemas operacionais usados por recipients que clicaram em uma mensagem.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Taxa de reatividade (deliveryFeedbackSocial)<br /> </td> 
   <td> Detalhamento da reação e da taxa de reatividade de delivery.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Taxa de transferência de cliques e URLs (topUrlDelivery)<br /> </td> 
   <td> A maioria das URLs reativas e fluxos de clique associados.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Relatórios sobre campanhas {#reports-on-campaigns}

Os relatórios sobre campanhas se relacionam aos dados na tabela de **nms:operation** .

Os relatórios internos fornecidos pelo Adobe Campaign podem ser encontrados na tabela abaixo.

Para obter mais informações sobre o conteúdo desses relatórios, consulte [esta seção](../../campaign/using/designing-marketing-campaigns.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Rótulo e nome interno</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Atividades do usuário (operationRecipientActivity)<br /> </td> 
   <td> O detalhamento de aberturas, cliques e transações por período de tempo depende do Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Taxa de transferência de delivery (operationThroughput)<br /> </td> 
   <td> Os gráficos de taxa de transferência de delivery, em emails/hora e Mbits/s, dependem do Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Despesas de campanha (budgetOperationExpenses)<br /> </td> 
   <td> Exibe os itens da linha de campanha em detalhes, depende do Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Falhas e devoluções (operationErrors)<br /> </td> 
   <td> Devoluções e não entregues por causa do domínio, depende do Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Exploração de linhas de custo (budgetExplorerOperation)<br /> </td> 
   <td> A análise descritiva das linhas de custo depende da Gestão dos Recursos de Marketing (MRM).<br /> </td> 
  </tr> 
  <tr> 
   <td> Indicadores de rastreamento (operationFeedback)<br /> </td> 
   <td> Visão geral dos indicadores principais de rastreamento: aberturas, cliques e transações que dependem do Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Compartilhamento para redes sociais (operationForward)<br /> </td> 
   <td> O compartilhamento de atividades e estatísticas de email aberto depende do Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Relatório Hipótese (operationHypothesis)<br /> </td> 
   <td> Exibe o resumo das medidas da hipótese para as deliveries da campanha, depende do Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Estatísticas de atividades de compartilhamento (forwardActivityOpt)<br /> </td> 
   <td> A análise de atividades de compartilhamento, abertura e subscrições por período de tempo depende do Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Resumo do delivery (operationStatistics)<br /> </td> 
   <td> Gráfico de resumo dos deliveries da campanha: targets, exclusões e mensagens enviadas.<br /> </td> 
  </tr> 
  <tr> 
   <td> Taxa de transferência de clique e URLs (operationTopUrlDelivery)<br /> </td> 
   <td> A maioria das URLs reativas e fluxos de cliques associados dependem do Campaign.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Relatórios sobre serviços {#reports-on-services}

Os relatórios sobre serviços diz respeito aos dados na tabela de **nms:service** .

Os relatórios internos fornecidos pelo Adobe Campaign podem ser encontrados na tabela abaixo.

Para obter mais informações sobre o conteúdo desses relatórios, consulte os guias relacionados.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Rótulo e nome interno</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Aquisições de fã (socialAcquisitionsByWebapp)<br /> </td> 
   <td> Quais aplicativos Web permitiram aquisições de prospecto? Depende de add-on de marketing social.<br /> </td> 
  </tr> 
  <tr> 
   <td> Detalhamento de subscrições (mobileAppDistribution)<br /> </td> 
   <td> O detalhamento de subscrições ativas por aplicativo móvel depende do add-on do canal de aplicativo móvel.<br /> </td> 
  </tr> 
  <tr> 
   <td> Rastreamento de subscrição (subscriptionsProgress)<br /> </td> 
   <td> Evolução das subscrições para serviços de informação<br /> </td> 
  </tr> 
  <tr> 
   <td> Taxa de Reatividade (socialReactionRate)<br /> </td> 
   <td> Quais são as taxas de reatividade para os deliveries mais recentes? Depende de add-on de marketing social.<br /> </td> 
  </tr> 
  <tr> 
   <td> Taxa de Reatividade (mobileAppReactivityRate)<br /> </td> 
   <td> A taxa de reatividade para os deliveries mais recentes depende do add-on de canal de aplicativo móvel.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Relatórios de orçamento {#budget-reports}

Os relatórios internos fornecidos pelo Adobe Campaign podem ser encontrados na tabela abaixo.

Para obter mais informações sobre o conteúdo desses relatórios, consulte [esta seção](../../campaign/using/designing-marketing-campaigns.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Rótulo e nome interno</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Custos vinculados ao(s) programa(s) (budgetProgramCost)<br /> </td> 
   <td> Detalhamento dos custos de programa.<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> Evolução do orçamento (budgetEvolution)<br /> </td> 
   <td> Evolução dos custos orçamentários por nível de comprometimento.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Evolução cumulativa do orçamento (budgetCumulativeEvolution)<br /> </td> 
   <td> Evolução dos custos do orçamento acumulado divididos por nível de<br /> compromisso. </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Exploração de linhas de custo (budgetExplorerBudget)<br /> </td> 
   <td> Análise descritiva de linhas de custo.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Exploração de linhas de custo (budgetExplorer)<br /> </td> 
   <td> Análise descritiva de linhas de custo.<br /> </td> 
   <td> nms:costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> Exploração de linhas de custo (budgetExplorerPlan)<br /> </td> 
   <td> Análise descritiva de linhas de custo.<br /> </td> 
   <td> nms:plan<br /> </td> 
  </tr> 
  <tr> 
   <td> Exploração de linhas de custo (budgetExplorerProgram)<br /> </td> 
   <td> Análise descritiva de linhas de custo.<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> Resumo do(s) orçamento(s) (orçamento)<br /> </td> 
   <td> Instantâneo dos custos principais, categorias de despesas e orçamentos.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Relatórios sobre simulações {#reports-on-simulations}

Os relatórios sobre simulações dizem respeito aos dados na tabela de **nms:simulation**.

Os relatórios internos fornecidos pelo Adobe Campaign podem ser encontrados na tabela abaixo.

Para obter mais informações sobre o conteúdo desses relatórios, consulte os guias relacionados.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Rótulo e nome interno</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Detalhe das exclusões de simulação (dlvSimuLossesDetail)<br /> </td> 
   <td> Tabela detalhada de todas as causas da exclusão.<br /> </td> 
  </tr> 
  <tr> 
   <td> Detalhamento de ofertas por classificação (offerSimulationRanking)<br /> </td> 
   <td> Detalhamento de ofertas na simulação, por classificação.<br /> </td> 
  </tr> 
  <tr> 
   <td> Resumo de simulação (dlvSimuLossesSummary)<br /> </td> 
   <td> Resumo de volumes e exclusões de simulação.<br /> </td> 
  </tr> 
  <tr> 
   <td> Estatística de sobreposição (dlvSimuOverlapping)<br /> </td> 
   <td> Volumes de sobreposição de target de delivery.<br /> </td> 
  </tr> 
  <tr> 
   <td> Resumo das exclusões devido à simulação (dlvSimuLossesSimu)<br /> </td> 
   <td> Tabela de exclusões devido à simulação.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Relatórios sobre aplicativos web {#reports-on-web-applications}

Os relatórios em aplicativos Web dizem respeito aos dados na tabela de **nms:WebApp** .

Os relatórios internos fornecidos pelo Adobe Campaign podem ser encontrados na tabela abaixo.

Para obter mais informações sobre o conteúdo desses relatórios, consulte [esta seção](../../web/using/about-web-applications.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Rótulo e nome interno</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Documentação (surveyDictionary)<br /> </td> 
   <td> A descrição da estrutura de pesquisa depende do add-on do Gerenciador de Pesquisa.<br /> </td> 
  </tr> 
  <tr> 
   <td> Principal (surveyProperties)<br /> </td> 
   <td> Propriedades da pesquisa<br /> </td> 
  </tr> 
  <tr> 
   <td> Detalhamento de respostas (surveyDistribution)<br /> </td> 
   <td> Detalhamento de respostas às perguntas.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Outros relatórios OOTB {#other-ootb-reports}

Os relatórios a seguir também são fornecidos internamente. Para obter mais informações, consulte o documento na funcionalidade relacionada a eles.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Rótulo e nome interno</strong><br /> </td> 
   <td> <strong>Descrição</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Análise de oferta (offerAnalysis)<br /> </td> 
   <td> A análise de oferta por data e canal depende do add-on Interaction.<br /> </td> 
   <td> nms:ofer<br /> </td> 
  </tr> 
  <tr> 
   <td> Eficiência de re-marketing (remarketingEffect)<br /> </td> 
   <td> Medição da eficiência do re-marketing<br /> </td> 
   <td> nms:webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> Histórico de aquisições de prospecto social (socialVisitorStatistics)<br /> </td> 
   <td> O histórico de aquisições de prospecto do Twitter e do Facebook depende do add-on de marketing social.<br /> </td> 
   <td> nms:visitor<br /> </td> 
  </tr> 
  <tr> 
   <td> Rastreamento de apresentação recente (recentPropositions)<br /> </td> 
   <td> Rastreamento de apresentação em tempo real<br /> </td> 
   <td> nms:propositionRcp<br /> </td> 
  </tr> 
 </tbody> 
</table>
