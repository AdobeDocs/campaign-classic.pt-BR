---
title: Tabelas para manter
seo-title: Tabelas para manter
description: Tabelas para manter
seo-description: null
page-status-flag: never-activated
uuid: 1085e929-65cc-48fa-9c31-0508a14b4704
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: 6ec4e566-7116-4d7f-835d-cb0f3c3a6a7a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Tabelas para manter{#tables-to-maintain}

A lista de tabelas a serem mantidas depende da sua versão do Adobe Campaign, da forma como você o usa e da configuração do modelo de dados.

A lista a seguir contém apenas as tabelas mais sujeitas a fragmentação. Os impactos são os seguintes:

* consumo excessivo de espaço em disco, afetando assim o acesso à base de dados,
* índices que não foram atualizados regularmente, o que reduz o desempenho da consulta.

## Tabelas do Adobe Campaign {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Nome da tabela </strong><br /> </th> 
   <th> <strong>Tamanho</strong><br /> </th> 
   <th> <strong>Principal tipo de atividade</strong><br /> </th> 
   <th> <strong>Comentários</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NmsDelivery<br /> </td> 
   <td> Pequeno<br /> </td> 
   <td> Atualizações<br /> </td> 
   <td> Há um registro por ação de entrega. Um único registro pode ser atualizado várias vezes para refletir o progresso da entrega, de modo que os índices nesta tabela tendem a fragmentar rapidamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> Médio<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Tabela de trabalho na qual os registros são inseridos durante a preparação da entrega. Eles são atualizados durante a entrega e finalmente excluídos assim que a entrega for concluída.<br /> Esta tabela tende a se fragmentar rapidamente, mesmo que seu tamanho médio seja bastante limitado.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Esta tabela contém as informações necessárias para gerar páginas espelhadas personalizadas. Ele contém um campo de memorando (CLOB) e, como tal, tende a ser muito grande. O volume é diretamente proporcional ao histórico de páginas espelhadas mantidas. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> Médio<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Esta tabela contém estatísticas sobre o processo de entrega. Os seus registros são regularmente atualizados. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> Médio<br /> </td> 
   <td> Atualizações, inserções<br /> </td> 
   <td> Esta tabela contém informações sobre endereços de email. Ele é frequentemente atualizado como parte do processo de quarentena (os registros são criados no primeiro erro de entrega, atualizados quando os contadores são alterados e excluídos assim que a entrega é bem-sucedida). <br /> </td> 
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
   <td> Esta tabela é específica do mecanismo de fluxo de trabalho. Ela permite o envio de comandos para fluxos de trabalho (Iniciar, Parar, Pausar, por exemplo). Embora seja pequeno, este quadro é considerado durante a expurgação de tabelas transacionais ligadas a fluxos de trabalho.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> Maior<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Esta é a maior mesa do sistema. Há um registro por mensagem enviada, e esses registros são inseridos, atualizados para rastrear o status de entrega e excluídos quando o histórico é expurgado. <br /> </td> 
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
   <td> Esta tabela contém informações usadas para qualificar erros SMTP. É bastante pequeno, mas será atualizado em grande escala, portanto os índices desta tabela tendem a se fragmentar rapidamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> Médio<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Esta tabela contém os agregados em erros SMTP classificados por domínio. Ele contém inicialmente informações detalhadas que são agregadas pela tarefa de limpeza quando ela fica desatualizada. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid (em uma instância de mid-sourcing)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Somente quando a instância 5.10 (ou posterior) é usada como uma instância de mid-sourcing. Esta é uma das maiores tabelas do banco de dados. Há um registro por mensagem enviada, e esses registros são inseridos, atualizados para rastrear o status de entrega e excluídos quando o histórico é expurgado. Ao usar o mid-sourcing, a recomendação é limitar o histórico (normalmente menos de dois meses), portanto, essa tabela permanece razoável em termos de tamanho (menos de 30 milhões de linhas, data+index), mas é muito importante reconstruí-la periodicamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp (quando a tabela NmsRecipient é usada) <br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Esta é a maior mesa do sistema. Há um registro por mensagem enviada, e esses registros são inseridos, atualizados para rastrear o status de entrega e excluídos quando o histórico é expurgado. Observe que na versão 5.10, essa tabela é menor que o equivalente na versão 4.05 (NmsBroadLog), pois o texto da mensagem SMTP é fatorizado na tabela NmsBroadLogMsg na versão 5.10. No entanto, continua sendo essencial reindexar essa tabela regularmente (a cada duas semanas para começar) e recriá-la completamente de vez em quando (uma vez por mês ou quando o desempenho é afetado). <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx (quando uma tabela de destinatários externos é usada)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Igual a NmsBroadLogRcp, mas com uma tabela de destinatários externos. Adapte Yyy e Xxx aos valores no mapeamento de entrega. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp (quando a tabela NmsRecipient é usada) <br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Os logs de rastreamento são inseridos e excluídos quando o histórico é removido, mas não são atualizados. O volume depende da duração da retenção de dados. <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXxx (quando a tabela de destinatários externos é usada)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Igual a NmsTrackingLogRcp, mas com uma tabela de destinatários externos. Adapte Yyy e Xxx aos valores usados no mapeamento de entrega. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent (instância de execução do Message Center)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Semelhante às outras tabelas de transmissão, mas com NmsRtEvent em vez de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent (instância de execução do Message Center)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Semelhante às outras tabelas trackingLog, mas com a tabela NmsRtEvent em vez de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent (instância de execução do Centro de Mensagens)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Tabela que contém a fila de eventos do Centro de mensagens. O status desses eventos é atualizado pelo Centro de Mensagens à medida que são processados. As exclusões são feitas durante a purga. Recomendamos que você recrie regularmente o índice desta tabela e reconstrua-a.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto (instância de controle do Message Center)<br /> </td> 
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
   <td> Tabela que inclui os identificadores de dispositivos móveis (endereços) usados para enviar a notificação (semelhante a uma tabela de destinatários).<br /> </td> 
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

Além da lista acima, as tabelas que contêm tabelas criadas por clientes (que não existem no modelo de dados do Adobe Campaign) durante a configuração da plataforma também podem estar sujeitas a fragmentação, especialmente se forem atualizadas com frequência durante os procedimentos de carregamento ou sincronização de dados. Essas tabelas podem fazer parte do modelo de dados padrão do Adobe Campaign (por exemplo, **NmsRecipient**). Nesse caso, cabe ao administrador da plataforma Adobe Campaign realizar uma auditoria de seu modelo de banco de dados específico para localizar essas tabelas personalizadas. Essas tabelas não são necessariamente mencionadas explicitamente em nossos procedimentos de manutenção.
