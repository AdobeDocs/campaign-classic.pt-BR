---
product: campaign
title: Tabelas a serem preservadas
description: Tabelas a serem preservadas
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 194f12de-4671-4a56-8cdc-cd5e3dac147b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 3%

---

# Tabelas a serem preservadas{#tables-to-maintain}

![](../../assets/v7-only.svg)

A lista de tabelas a serem mantidas depende da versão do Adobe Campaign, da forma como você a usa e da configuração do modelo de dados.

A lista a seguir contém apenas as tabelas mais sujeitas a fragmentação. Os impactos são os seguintes:

* consumo excessivo de espaço em disco, afetando assim o acesso ao banco de dados,
* índices que não foram atualizados regularmente, o que reduz o desempenho da consulta.

## Tabelas Adobe Campaign {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Nome da tabela </strong><br /> </th> 
   <th> <strong>Tamanho</strong><br /> </th> 
   <th> <strong>Tipo principal de atividade</strong><br /> </th> 
   <th> <strong>Comentários</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NmsDelivery<br /> </td> 
   <td> Pequeno<br /> </td> 
   <td> Atualizações<br /> </td> 
   <td> Há um registro por ação de delivery. Um único registro pode ser atualizado várias vezes para refletir o progresso do delivery, de modo que os índices nesta tabela tendem a fragmentar rapidamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> Médio<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Tabela de trabalho na qual os registros são inseridos durante a preparação do delivery. Eles são atualizados durante o delivery e finalmente excluídos após a conclusão do delivery.<br /> Essa tabela tende a fragmentar rapidamente, mesmo que seu tamanho médio seja bastante limitado.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Essa tabela contém as informações necessárias para gerar mirror pages personalizadas. Ele contém um campo de memorando (CLOB) e, como tal, tenderá a ser muito grande. O volume é diretamente proporcional ao histórico de mirror pages mantidas. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> Médio<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Esta tabela contém estatísticas sobre o processo de delivery. Seus registros são atualizados regularmente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> Médio<br /> </td> 
   <td> Atualizações, inserções<br /> </td> 
   <td> Esta tabela contém informações sobre endereços de email. Ele é frequentemente atualizado como parte do processo de quarentena (os registros são criados no primeiro erro de delivery, atualizados quando os contadores são alterados e excluídos assim que o delivery é bem-sucedido). <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> Pequeno<br /> </td> 
   <td> Atualizações<br /> </td> 
   <td> Há um registro por instância de workflow, portanto, poucos registros. No entanto, o quadro é atualizado regularmente para refletir o status e o progresso.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> Pequeno<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Cada execução de uma atividade de workflow leva à criação de um registro nesta tabela. O mecanismo de limpeza os exclui depois que expiram.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> Pequeno<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Cada transição ativada entre tarefas em um workflow leva à criação de um registro nesta tabela. O mecanismo de limpeza os exclui depois que expiram. <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> Muito pequeno <br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Essa tabela é específica do mecanismo de workflow. Ele permite o envio de comandos para workflows (Start, Stop, Pause, por exemplo). Embora seja pequena, essa tabela é considerada durante a limpeza de tabelas transacionais vinculadas a workflows.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> Maior<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Esta é a maior mesa do sistema. Há um registro por mensagem enviada, e esses registros são inseridos, atualizados para rastrear o status do delivery e excluídos quando o histórico é removido. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Os logs de rastreamento são inseridos e excluídos quando o histórico é removido, mas não são atualizados. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> Pequeno<br /> </td> 
   <td> Atualizações<br /> </td> 
   <td> Esta tabela contém informações usadas para qualificar erros SMTP. Ele é relativamente pequeno, mas será atualizado em grande escala, portanto, os índices nesta tabela tendem a fragmentar rapidamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> Médio<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Esta tabela contém os agregados em erros SMTP classificados por domínio. Ele contém inicialmente informações detalhadas que são agregadas pela tarefa de limpeza quando ela se torna desatualizada. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid (em uma instância mid-sourcing)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Somente quando a instância 5.10 (ou posterior) é usada como uma instância de mid-sourcing. Esta é uma das maiores tabelas no banco de dados. Há um registro por mensagem enviada, e esses registros são inseridos, atualizados para rastrear o status do delivery e excluídos quando o histórico é removido. Ao usar o mid-sourcing, a recomendação é limitar o histórico (geralmente menos de dois meses), de modo que essa tabela permanece razoável em termos de tamanho (menos de 30 milhões de linhas, data+index), mas é muito importante recriá-la ocasionalmente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp (quando a tabela NmsRecipient é usada) <br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Esta é a maior mesa do sistema. Há um registro por mensagem enviada, e esses registros são inseridos, atualizados para rastrear o status do delivery e excluídos quando o histórico é removido. Observe que na versão 5.10, essa tabela é menor que o equivalente na 4.05 (NmsBroadLog), pois o texto da mensagem SMTP é fatorado na tabela NmsBroadLogMsg na versão 5.10. No entanto, continua sendo essencial reindexar essa tabela regularmente (a cada duas semanas para começar) e recriá-la completamente de tempos em tempos (uma vez por mês ou quando o desempenho é afetado). <br /> </td> 
  </tr> 
  <tr> 
   <td> YyBroadLogXxx (quando uma tabela de recipient externo é usada)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Igual a NmsBroadLogRcp, mas com uma tabela de recipient externa. Adapte Yy e Xxx com os valores no mapeamento do delivery. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp (quando a tabela NmsRecipient é usada) <br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Os logs de rastreamento são inseridos e excluídos quando o histórico é removido, mas não são atualizados. O volume depende da duração da retenção de dados. <br /> </td> 
  </tr> 
  <tr> 
   <td> YyTrackingLogXxx (quando a tabela de recipient externo é usada)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Igual a NmsTrackingLogRcp, mas com uma tabela de recipient externa. Adapte Yy e Xxx com os valores usados no mapeamento do delivery. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent (instância de execução do Centro de Mensagens)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Semelhante às outras tabelas de broadlog, mas com o NmsRtEvent em vez de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent( Instância de execução do Centro de Mensagens)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Semelhante às outras tabelas trackingLog, mas com a tabela NmsRtEvent em vez de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent (instância de execução do Centro de Mensagens)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Tabela que contém a fila de eventos do Centro de mensagens. O status desses eventos é atualizado pelo Centro de Mensagens à medida que são processados. As exclusões são realizadas durante a limpeza. Recomendamos que você recrie regularmente o índice desta tabela e recrie-o.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto (instância de controle do Centro de Mensagens)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Semelhante a NmsRtEvent. Esta tabela arquiva cada evento de todas as instâncias de execução. Ele é usado por um processo em tempo real, apenas por relatórios.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> Muito pequeno<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Tabelas que incluem aplicativos móveis e sua configuração.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações<br /> </td> 
   <td> Tabela que inclui os identificadores de dispositivos móveis (endereços) usados para enviar a notificação (semelhante a uma tabela de recipients).<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Semelhante às outras tabelas de broadlog, mas com o NmsappSubscriptionRcp em vez de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogAppSubRcp<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Semelhante às outras tabelas trackingLog, mas com a tabela NmsappSubscriptionRcp em vez de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkSessionInfo<br /> </td> 
   <td> Pequeno<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Tabela que inclui sessões do usuário. O número de inserções e exclusões é muito importante.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tabelas do cliente {#customer-tables}

Além da lista acima, as tabelas que contêm os criados pelos clientes (que não existem no modelo de dados do Adobe Campaign) durante a configuração da plataforma também podem estar sujeitas a fragmentação, especialmente se forem atualizadas com frequência durante os procedimentos de carregamento ou sincronização de dados. Essas tabelas podem fazer parte do modelo de dados padrão do Adobe Campaign (por exemplo, **NmsRecipient**). Nesse caso, cabe ao administrador da plataforma Adobe Campaign realizar uma auditoria do modelo específico de banco de dados para localizar essas tabelas personalizadas. Essas tabelas não são necessariamente mencionadas explicitamente em nossos procedimentos de manutenção.
