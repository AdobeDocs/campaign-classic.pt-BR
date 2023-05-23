---
product: campaign
title: Tabelas a serem preservadas
description: Tabelas a serem preservadas
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 194f12de-4671-4a56-8cdc-cd5e3dac147b
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 3%

---

# Tabelas a serem preservadas{#tables-to-maintain}



A lista de tabelas a serem mantidas depende da versão do Adobe Campaign, como você a usa e da configuração do modelo de dados.

A lista a seguir contém apenas as tabelas mais sujeitas à fragmentação. Os impactos são os seguintes:

* consumo excessivo de espaço em disco, afetando assim o acesso ao banco de dados,
* índices que não foram atualizados regularmente, o que atrasa o desempenho da consulta.

## Tabelas do Adobe Campaign {#adobe-campaign-tables}

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
   <td> Há um registro por ação de entrega. Um único registro pode ser atualizado várias vezes para refletir o progresso do delivery, de modo que os índices nessa tabela tendem a se fragmentar rapidamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> Médio<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Tabela de trabalho na qual os registros são inseridos durante a preparação da entrega. Eles são atualizados durante o delivery e finalmente excluídos quando o delivery é concluído.<br /> Essa tabela tende a se fragmentar rapidamente, mesmo que seu tamanho médio seja bastante limitado.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Esta tabela contém as informações necessárias para gerar mirror pages personalizadas. Ele contém um campo de memorando (CLOB) e, como tal, tenderá a ser muito grande. O volume é diretamente proporcional ao histórico de mirror pages mantidas. <br /> </td> 
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
   <td> Esta tabela contém informações sobre endereços de email. Ele é atualizado com frequência como parte do processo de quarentena (os registros são criados no primeiro erro de delivery, atualizados quando os contadores são alterados e excluídos quando o delivery é bem-sucedido). <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> Pequeno<br /> </td> 
   <td> Atualizações<br /> </td> 
   <td> Há um registro por instância de fluxo de trabalho, então pouquíssimos registros. No entanto, a tabela é atualizada regularmente para refletir o status e o progresso.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> Pequeno<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Cada execução de uma atividade de workflow leva à criação de um registro nesta tabela. O mecanismo de limpeza as exclui após a expiração.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> Pequeno<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Cada transição ativada entre tarefas em um workflow leva à criação de um registro nesta tabela. O mecanismo de limpeza as exclui após a expiração. <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> Muito pequeno <br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Essa tabela é específica do mecanismo de workflow. Ela permite o envio de comandos para workflows (Start, Stop, Pause, por exemplo). Embora pequena, essa tabela é levada em conta durante a limpeza de tabelas transacionais vinculadas aos workflows.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> Maior<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Esta é a maior tabela do sistema. Há um registro por mensagem enviada. Esses registros são inseridos, atualizados para rastrear o status do delivery e excluídos quando o histórico é removido. <br /> </td> 
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
   <td> Esta tabela contém informações usadas para qualificar erros SMTP. É relativamente pequeno, mas será amplamente atualizado, portanto, os índices nesta tabela tendem a se fragmentar rapidamente. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> Médio<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Essa tabela contém as agregações de erros SMTP classificados por domínio. Inicialmente, contém informações detalhadas que são agregadas pela tarefa de limpeza depois que ela se torna desatualizada. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid (em uma instância mid-sourcing)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Somente quando a instância 5.10 (ou posterior) é usada como uma instância mid-sourcing. Esta é uma das maiores tabelas do banco de dados. Há um registro por mensagem enviada. Esses registros são inseridos, atualizados para rastrear o status do delivery e excluídos quando o histórico é removido. Ao usar o mid-sourcing, a recomendação é limitar o histórico (geralmente menos de dois meses), de modo que esta tabela permanece razoável em termos de tamanho (menos de 30 Vá para 60 milhões de linhas, dados + índice), mas é muito importante reconstruí-la de tempos em tempos. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp (quando a tabela NmsRecipient é usada) <br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Esta é a maior tabela do sistema. Há um registro por mensagem enviada. Esses registros são inseridos, atualizados para rastrear o status do delivery e excluídos quando o histórico é removido. Observe que na versão 5.10, essa tabela é menor que o equivalente na 4.05 (NmsBroadLog), pois o texto da mensagem SMTP é fatorado na tabela NmsBroadLogMsg na versão 5.10. No entanto, continua sendo essencial reindexar essa tabela regularmente (a cada duas semanas, para começar) e recriá-la completamente de tempos em tempos (uma vez por mês ou quando o desempenho é afetado). <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx (quando uma tabela externa de recipient é usada)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Igual a NmsBroadLogRcp, mas com uma tabela externa de recipient. Adapte Yyy e Xxx com os valores no mapeamento do delivery. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp (quando a tabela NmsRecipient é usada) <br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Os logs de rastreamento são inseridos e excluídos quando o histórico é removido, mas não são atualizados. O volume depende da duração da retenção de dados. <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXxx (quando a tabela de destinatários externos for usada)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Igual a NmsTrackingLogRcp, mas com uma tabela de recipient externa. Adapte Yyy e Xxx com os valores usados no mapeamento do delivery. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent (instância de execução do Centro de Mensagens)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Semelhante às outras tabelas de broadlog, mas com o NmsRtEvent em vez de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent( instância de execução do Centro de Mensagens)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, exclusões<br /> </td> 
   <td> Semelhante às outras tabelas trackingLog, mas com a tabela NmsRtEvent em vez de NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent (instância de execução do Centro de Mensagens)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Tabela contendo a fila de eventos do Centro de mensagens. O status desses eventos é atualizado pelo Centro de mensagens à medida que são processados. As exclusões são realizadas durante a limpeza. Recomendamos que você recrie regularmente o índice desta tabela e recrie-o.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto (instância de controle do Centro de Mensagens)<br /> </td> 
   <td> Grande<br /> </td> 
   <td> Inserções, atualizações, exclusões<br /> </td> 
   <td> Semelhante a NmsRtEvent. Esta tabela arquiva todos os eventos de todas as instâncias de execução. Ela é usada por nenhum processo em tempo real, somente por relatórios.<br /> </td> 
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
   <td> Tabela que inclui sessões de usuário. O número de inserções e exclusões é muito importante.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tabelas do cliente {#customer-tables}

Além da lista acima, as tabelas que contêm dados criados por clientes (que não existem no modelo de dados do Adobe Campaign) durante a configuração da plataforma também podem estar sujeitas a fragmentação, especialmente se forem atualizadas com frequência durante os procedimentos de carregamento ou sincronização de dados. Essas tabelas podem fazer parte do modelo de dados padrão do Adobe Campaign (por exemplo, **NmsRecipient**). Nesse caso, cabe ao administrador da plataforma Adobe Campaign fazer uma auditoria de seu modelo de banco de dados específico para encontrar essas tabelas personalizadas. Essas tabelas não são necessariamente mencionadas explicitamente em nossos procedimentos de manutenção.
