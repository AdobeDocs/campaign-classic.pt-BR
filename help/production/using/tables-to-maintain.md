---
solution: Campaign Classic
product: campaign
title: 'Tabelas a serem preservadas '
description: 'Tabelas a serem preservadas '
audience: production
content-type: reference
topic-tags: database-maintenance
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 1%

---


# Tabelas a serem preservadas {#tables-to-maintain}

A lista de tabelas a serem mantidas depende da sua versão do Adobe Campaign, do modo como você o usa e da configuração do modelo de dados.

A lista a seguir contém apenas as tabelas mais sujeitas a fragmentação. Os impactos são os seguintes:

* consumo excessivo de espaço em disco, afetando assim o acesso à base de dados,
* índices que não foram atualizados regularmente, o que reduz o desempenho do query.

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
   <td> Há um registro por ação do delivery. Um único registro pode ser atualizado várias vezes para refletir o progresso do delivery, de modo que os índices nesta tabela tendem a fragmentar rapidamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> Médio<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Tabela de trabalho na qual os registros são inseridos durante a preparação do delivery. Eles são atualizados durante o delivery e finalmente excluídos assim que o delivery for concluído.<br /> Esta tabela tende a se fragmentar rapidamente, mesmo que seu tamanho médio seja bastante limitado.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Esta tabela contém as informações necessárias para gerar mirrores page personalizados. Ele contém um campo de memorando (CLOB) e, como tal, tende a ser muito grande. O volume é diretamente proporcional ao histórico de mirrores page mantidos. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> Médio<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Esta tabela contém estatísticas sobre o processo de delivery. Os seus registros são regularmente atualizados. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> Médio<br /> </td> 
   <td> Atualizações, inserções<br /> </td> 
   <td> Esta tabela contém informações sobre endereços de email. Ele é atualizado com frequência como parte do processo de quarentena (os registros são criados no primeiro erro de delivery, atualizados quando os contadores são alterados e excluídos depois que o delivery é bem-sucedido). <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> Pequeno<br /> </td> 
   <td> Atualizações<br /> </td> 
   <td> Há um registro por instância de fluxo de trabalho, portanto, poucos registros. No entanto, o quadro é atualizado regularmente para refletir o estado e o progresso.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> Pequeno<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Cada execução de uma atividade de fluxo de trabalho leva à criação de um registro nesta tabela. O mecanismo de expurgação os exclui depois que expiram.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> Pequeno<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Cada transição ativada entre tarefas em um fluxo de trabalho leva à criação de um registro nesta tabela. O mecanismo de expurgação os exclui depois que expiram. <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> Muito pequeno <br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Esta tabela é específica do motor de workflow. Ela permite o envio de comandos para workflows (Start, Parar, Pausar, por exemplo). Embora seja pequeno, este quadro é tomado em consideração durante a purga de tabelas transacionais ligadas a workflows.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> Maior<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Esta é a maior mesa do sistema. Há um registro por mensagem enviada e esses registros são inseridos, atualizados para rastrear o status do delivery e excluídos quando o histórico é expurgado. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Logs de rastreamento são inseridos e excluídos quando o histórico é limpo, mas não são atualizados. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> Pequeno<br /> </td> 
   <td> Atualizações<br /> </td> 
   <td> Esta tabela contém informações usadas para qualificar erros SMTP. É bastante pequeno, mas será atualizado em grande escala, portanto os índices desta tabela tendem a se fragmentar rapidamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> Médio<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Esta tabela contém as agregações sobre erros SMTP classificados por domínio. Ele contém inicialmente informações detalhadas que são agregadas pela tarefa de limpeza quando ela fica desatualizada. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid (em uma instância de mid-sourcing)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Somente quando a instância 5.10 (ou posterior) é usada como uma instância mid-sourcing. Esta é uma das maiores tabelas do banco de dados. Há um registro por mensagem enviada e esses registros são inseridos, atualizados para rastrear o status do delivery e excluídos quando o histórico é expurgado. Ao usar o mid-sourcing, a recomendação é limitar o histórico (normalmente menos de dois meses), portanto, essa tabela permanece razoável em termos de tamanho (menos de 30 milhões de linhas, data+index), mas é muito importante reconstruí-la periodicamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp (quando a tabela NmsRecipient é usada) <br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Esta é a maior mesa do sistema. Há um registro por mensagem enviada e esses registros são inseridos, atualizados para rastrear o status do delivery e excluídos quando o histórico é expurgado. Observe que na versão 5.10, essa tabela é menor que o equivalente na versão 4.05 (NmsBroadLog), pois o texto da mensagem SMTP é fatorizado na tabela NmsBroadLogMsg na versão 5.10. No entanto, continua sendo essencial reindexar essa tabela regularmente (de duas em duas semanas para start) e recriá-la completamente de vez em quando (uma vez por mês ou quando o desempenho é afetado). <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx (quando uma tabela de recipient externa é usada)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Igual a NmsBroadLogRcp, mas com uma tabela de recipient externa. Adapte Yyy e Xxx aos valores no mapeamento do delivery. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp (quando a tabela NmsRecipient é usada) <br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Logs de rastreamento são inseridos e excluídos quando o histórico é limpo, mas não são atualizados. O volume depende da duração da retenção de dados. <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXxx (quando a tabela de recipient externos é usada)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Igual a NmsTrackingLogRcp, mas com uma tabela de recipient externa. Adapte Yyy e Xxx aos valores usados no mapeamento do delivery. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent (instância de execução do centro de mensagens)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Semelhante às outras tabelas de transmissão, mas com NmsRtEvent em vez de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent (instância de execução do Centro de mensagens)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Semelhante às outras tabelas trackingLog, mas com a tabela NmsRtEvent em vez de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent (instância de execução do centro de mensagens)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Tabela que contém a fila de evento do Centro de mensagens. O status desses eventos é atualizado pelo Centro de mensagens à medida que são processados. As exclusões são feitas durante a purga. Aconselhamos você a recriar regularmente o índice desta tabela e reconstruí-lo.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto (instância de controle do centro de mensagens)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Semelhante a NmsRtEvent. Esta tabela arquiva cada evento de todas as instâncias de execução. É usado por nenhum processo em tempo real, apenas por relatórios.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> Muito pequeno<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Tabelas que incluem aplicativos móveis e suas configurações.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações<br /> </td> 
   <td> Tabela que inclui os identificadores de dispositivos móveis (endereços) usados para enviar a notificação (semelhante a uma tabela de recipient).<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Semelhante às outras tabelas de transmissão, mas com NmsappSubscriptionRcp em vez de NmsRecipient.<br /> </td> 
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
   <td> Tabela que inclui sessões de usuário. O número de inserções e exclusões é muito importante.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tabelas do cliente {#customer-tables}

Além da lista acima, as tabelas que contêm tabelas criadas por clientes (que não existem no modelo de dados da Adobe Campaign) durante a configuração da plataforma também podem estar sujeitas a fragmentação, especialmente se forem atualizadas com frequência durante os procedimentos de carregamento ou sincronização de dados. Essas tabelas podem fazer parte do modelo de dados padrão da Adobe Campaign (por exemplo, **NmsRecipient**). Nesse caso, cabe ao administrador da plataforma Adobe Campaign realizar uma auditoria de seu modelo de banco de dados específico para localizar essas tabelas personalizadas. Essas tabelas não são necessariamente mencionadas explicitamente em nossos procedimentos de manutenção.
