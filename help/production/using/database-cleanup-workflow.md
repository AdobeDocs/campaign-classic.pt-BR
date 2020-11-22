---
solution: Campaign Classic
product: campaign
title: Workflow de limpeza do banco de dados
description: Saiba como os dados obsoletos são automaticamente limpos
audience: production
content-type: reference
topic-tags: data-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2910'
ht-degree: 1%

---


# Workflow de limpeza do banco de dados{#database-cleanup-workflow}

## Introdução {#introduction}

O **[!UICONTROL Database cleanup]** fluxo de trabalho acessível pelo **[!UICONTROL Administration > Production > Technical workflows]** nó permite que você exclua dados obsoletos para evitar o crescimento exponencial do banco de dados. O workflow é acionado automaticamente sem a intervenção do usuário.

![](assets/ncs_cleanup_workflow.png)

## Configuração {#configuration}

A limpeza do banco de dados está configurada em dois níveis: no scheduler de fluxo de trabalho e no assistente de implantação.

### Scheduler de fluxo de trabalho {#the-scheduler}

>[!NOTE]
>
>Para saber mais sobre o scheduler, consulte [esta seção](../../workflow/using/scheduler.md).

Por padrão, o fluxo de trabalho **[!UICONTROL Database cleanup]** é configurado para start diariamente às 4h00. O scheduler permite alterar a frequência de acionamento do fluxo de trabalho. As seguintes frequências estão disponíveis:

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>Para que o fluxo de trabalho seja **[!UICONTROL Database cleanup]** start na data e hora definidas no scheduler, o motor de workflow (wfserver) deve ser iniciado. Se esse não for o caso, a limpeza do banco de dados não ocorrerá até a próxima vez que o motor de workflow for iniciado.

### Assistente de implantação {#deployment-wizard}

O **[!UICONTROL Deployment wizard]**, acessado pelo **[!UICONTROL Tools > Advanced]** menu, permite configurar por quanto tempo os dados são salvos. Os valores são expressos em dias. Se esses valores não forem alterados, o fluxo de trabalho usará os valores padrão.

![](assets/ncs_cleanup_deployment-wizard.png)

Os campos da **[!UICONTROL Purge of data]** janela coincidem com as seguintes opções. Eles são usados por algumas tarefas executadas pelo **[!UICONTROL Database cleanup]** fluxo de trabalho:

* Rastreamento consolidado: **NmsCleanup_TrackingStatPurgeDelay** (consulte [Limpeza de logs de rastreamento](#cleanup-of-tracking-logs))
* Logs do delivery: **NmsCleanup_BroadLogPurgeDelay** (consulte [Limpeza de logs do delivery](#cleanup-of-delivery-logs))
* Logs de rastreamento: **NmsCleanup_TrackingLogPurgeDelay** (consulte [Limpeza de logs de rastreamento](#cleanup-of-tracking-logs))
* Delivery excluídos: **NmsCleanup_RecycledDeliveryPurgeDelay** (consulte [Limpeza de delivery a serem excluídos ou reciclados](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* Importar rejeitos: **NmsCleanup_RejectsPurgeDelay** (consulte [Limpeza de rejeitos gerados por importações](#cleanup-of-rejects-generated-by-imports-))
* Perfis do visitante: **NmsCleanup_VisitorPurgeDelay** (consulte [Limpeza de visitantes](#cleanup-of-visitors))
* Apresentações da oferta: **NmsCleanup_PropositionPurgeDelay** (consulte [Limpeza de proposições](#cleanup-of-propositions))

   >[!NOTE]
   >
   >O **[!UICONTROL Offer propositions]** campo só estará disponível quando o módulo **Interação** estiver instalado.

* Eventos: **NmsCleanup_EventPurgeDelay** (consulte a [Limpeza de eventos](#cleansing-expired-events)expirados)
* Eventos arquivados: **NmsCleanup_EventHistoPurgeDelay** (consulte os eventos [vencidos da](#cleansing-expired-events)Limpeza)

   >[!NOTE]
   >
   >Os campos **[!UICONTROL Events]** e **[!UICONTROL Archived events]** só estarão disponíveis se o módulo Central **de** mensagens estiver instalado.

* Trilha de auditoria: **XtkCleanup_AuditTrailPurgeDelay** (consulte a [Limpeza da trilha](#cleanup-of-audit-trail)de auditoria)

Todas as tarefas executadas pelo **[!UICONTROL Database cleanup]** fluxo de trabalho são descritas na seção a seguir.

## Tarefas executadas pelo fluxo de trabalho de limpeza do Banco de Dados {#tasks-carried-out-by-the-database-cleanup-workflow}

Na data e hora definidas no scheduler do fluxo de trabalho (consulte [O scheduler](#the-scheduler)), o motor de workflow start o processo de limpeza do banco de dados. A limpeza do Banco de Dados se conecta ao banco de dados e executa as tarefas na sequência mostrada abaixo.

>[!IMPORTANT]
>
>Se uma dessas tarefas falhar, as seguintes não serão executadas.\
>Os query SQL com um atributo **LIMIT** serão executados repetidamente até que todas as informações sejam processadas.

>[!NOTE]
>
>As seções abaixo que descrevem as tarefas executadas pelo fluxo de trabalho de limpeza do Banco de Dados são reservadas para administradores de banco de dados ou usuários familiarizados com o idioma SQL.

### Listas para excluir a limpeza {#lists-to-delete-cleanup}

A primeira tarefa executada pelo **[!UICONTROL Database cleanup]** fluxo de trabalho exclui todos os grupos com o **deleteStatus != 0** atributo do **NmsGroup**. Os registros ligados a esses grupos e que existem em outras tabelas também são excluídos.

1. As listas a serem excluídas são recuperadas usando o seguinte query SQL:

   ```
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. Cada lista tem vários links para outras tabelas. Todos esses links são excluídos em massa usando o seguinte query:

   ```
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   em que **$(relatedTable)** é uma tabela relacionada ao **NmsGroup** e **$(l)** é o identificador da lista.

1. Quando a lista é do tipo &quot;Lista&quot;, a tabela associada é excluída usando o seguinte query:

   ```
   DROP TABLE grp$(l)
   ```

1. Cada lista **Select** type recuperada pela operação é excluída usando o seguinte query:

   ```
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   em que **$(l)** é o identificador da lista

### Limpeza dos delivery a eliminar ou a reciclar {#cleanup-of-deliveries-to-be-deleted-or-recycled}

Esta tarefa limpa todos os delivery a serem excluídos ou reciclados.

1. O **[!UICONTROL Database cleanup]** fluxo de trabalho seleciona todos os delivery para os quais o campo **deleteStatus** tem o valor **[!UICONTROL Yes]** ou **[!UICONTROL Recycled]** e cuja data de exclusão é anterior ao período definido no campo **[!UICONTROL Deleted deliveries]** (**NmsCleanup_RecycledDeliveryPurgeDelay**) do assistente de implantação. For more on this, refer to [Deployment wizard](#deployment-wizard). Esse período é calculado em relação à data atual do servidor.
1. Para cada servidor mid-sourcing, a tarefa seleciona a lista de delivery a serem excluídos.
1. O **[!UICONTROL Database cleanup]** fluxo de trabalho exclui logs do delivery, anexos, informações do mirror page e todos os outros dados relacionados.
1. Antes de excluir o delivery para boas, o fluxo de trabalho remove as informações vinculadas das seguintes tabelas:

   * Na tabela de exclusão de delivery (**NmsDlvExclusion**), é usado o seguinte query:

      ```
      DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
      ```

      onde **$(l)** é o identificador do delivery.

   * Na tabela de cupom (**NmsCouponValue**), o seguinte query é usado (com exclusões em massa):

      ```
      DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
      ```

      onde **$(l)** é o identificador do delivery.

   * Nas tabelas de log de delivery (**NmsBroadlogXxx**), as exclusões em massa são executadas em lotes de 20.000 registros.
   * Nas tabelas de apresentação da oferta (**NmsPropositionXxx**), as exclusões em massa são executadas em lotes de 20.000 registros.
   * Nas tabelas de log de rastreamento (**NmsTrackinglogXxx**), as exclusões em massa são executadas em lotes de 20.000 registros.
   * Na tabela de fragmentos do delivery (**NmsDeliveryPart**), as exclusões em massa são executadas em lotes de 500.000 registros. Esta tabela contém informações de personalização sobre as mensagens restantes a serem entregues.
   * Na tabela de fragmentos de dados do mirror page (**NmsMirrorPageInfo**), as exclusões em massa são executadas em lotes de 20.000 registros para partes do delivery expiradas e para partes concluídas ou canceladas. Esta tabela contém informações de personalização sobre todas as mensagens usadas para gerar mirrores page.
   * Na tabela de pesquisa de mirrores page (**NmsMirrorPageSearch**), as exclusões em massa são executadas em lotes de 20.000 registros. Esta tabela é um índice de pesquisa que fornece acesso às informações de personalização armazenadas na tabela **NmsMirrorPageInfo** .
   * Na tabela de log do processo em lote (**XtkJobLog**), as exclusões em massa são executadas em lotes de 20.000 registros. Esta tabela contém o log de delivery a serem excluídos.
   * Na tabela de rastreamento de URL do delivery (**NmsTrackingUrl**), o seguinte query é usado:

      ```
      DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
      ```

      onde **$(l)** é o identificador do delivery.

      Esta tabela contém os URLs encontrados nos delivery a serem excluídos para permitir seu rastreamento.

1. O delivery é excluído da tabela delivery (**NmsDelivery**):

   ```
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   onde **$(l)** é o identificador do delivery.

#### Delivery usando mid-sourcing {#deliveries-using-mid-sourcing}

O **[!UICONTROL Database cleanup]** fluxo de trabalho também exclui delivery nos servidores mid-sourcing.

1. Para fazer isso, o fluxo de trabalho verifica se cada delivery está inativo (com base em seu status). Se um delivery estiver ativo, ele será interrompido antes de ser excluído. A verificação é realizada executando o seguinte query:

   ```
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   onde **$(l)** é o identificador do delivery.

1. Se o valor do status for **[!UICONTROL Start pending]** , **[!UICONTROL In progress]** , **[!UICONTROL Recovery pending]** , **[!UICONTROL Recovery in progress]** , **[!UICONTROL Pause requested]** , **[!UICONTROL Pause in progress]** ou **[!UICONTROL Paused]** (valores 51, 55, 61, 62, 71, 72, 75), o delivery será parado e a tarefa limpará as informações vinculadas.

### Limpeza de delivery expirados {#cleanup-of-expired-deliveries}

Esta tarefa interrompe delivery cujo período de validade expirou.

1. O **[!UICONTROL Database cleanup]** fluxo de trabalho cria a lista de delivery que expiraram. Esta lista inclui todos os delivery expirados com um status diferente de **[!UICONTROL Finished]** , bem como delivery recém-parados com mais de 10.000 mensagens não processadas. O query a seguir é usado:

   ```
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   onde o modo **delivery 1** corresponde ao **[!UICONTROL Mass delivery]** modo, o **estado 51** corresponde ao **[!UICONTROL Start pending]** estado, o **estado 85** **[!UICONTROL Stopped]** corresponde ao estado e o maior número de logs do delivery atualizados em massa no servidor delivery é igual a 10.000.

1. O fluxo de trabalho então inclui a lista de delivery expirados recentemente que usam mid-sourcing. Os delivery para os quais nenhum logs do delivery foi recuperado por meio do servidor mid-sourcing são excluídos.

   O query a seguir é usado:

   ```
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. O query a seguir é usado para detectar se a conta externa ainda está ativa ou não, para filtrar delivery por data:

   ```
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. Na lista de delivery expirados, logs do delivery cujo status é **[!UICONTROL Pending]** , alterne para **[!UICONTROL Delivery cancelled]** e todos os delivery desta lista mudam para **[!UICONTROL Finished]** .

   Os seguintes query são usados:

   ```
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   onde **$(curdate)** é a data atual do servidor de banco de dados, **$(bl)** é o identificador da mensagem de logs do delivery, **$(dl)** é o identificador do delivery, o status do **delivery 6** corresponde ao **[!UICONTROL Pending]** status e o status do **** **[!UICONTROL Delivery cancelled]** delivery 7 corresponde ao status do .

   ```
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   em que o estado do **delivery 95** corresponde ao **[!UICONTROL Finished]** status e **$(dl)** é o identificador do delivery.

1. Todos os fragmentos (**deliveryParts**) de delivery obsoletos são excluídos e todos os fragmentos obsoletos de delivery de notificação em andamento são excluídos. A exclusão em massa é usada para ambas as tarefas.

   Os seguintes query são usados:

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   onde o estado do **delivery 95** corresponde ao **[!UICONTROL Finished]** status, o estado do **delivery 85** corresponde ao **[!UICONTROL Stopped]** status e **$(curDate)** é a data atual do servidor.

### Limpeza de mirrores page {#cleanup-of-mirror-pages}

Essa tarefa exclui os recursos da Web (mirrores page) usados pelos delivery.

1. Em primeiro lugar, a lista de delivery a serem expurgados é recuperada usando o seguinte query:

   ```
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)"
   ```

   em que **$(curDate)** é a data atual do servidor.

1. A tabela **NmsMirrorPageInfo** é então removida, se necessário usando o identificador do delivery recuperado anteriormente. A exclusão em massa é usada para gerar os seguintes query:

   ```
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   onde **$(dl)** é o identificador do delivery.

1. Uma entrada é então adicionada ao log de delivery.
1. Os delivery expurgados são então identificados, para evitar a necessidade de reprocessá-los mais tarde. O seguinte query é executado:

   ```
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   where **$(strIn)** é a lista de identificadores de delivery.

### Limpeza das tabelas de trabalho {#cleanup-of-work-tables}

Esta tarefa exclui do banco de dados, todas as tabelas de trabalho que correspondem a delivery cujo status é **[!UICONTROL Being edited]** , **[!UICONTROL Stopped]** ou **[!UICONTROL Deleted]** .

1. A lista de tabelas com nomes que começam com **wkDlv_** é recuperada primeiro com o seguinte query (postgresql):

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. As tabelas usadas por workflows em andamento são excluídas. Para fazer isso, a lista de delivery em andamento é recuperada usando o seguinte query:

   ```
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   onde 0 é o valor que corresponde ao status do **[!UICONTROL Being edited]** delivery, 85 corresponde ao **[!UICONTROL Stopped]** status e 100 corresponde ao **[!UICONTROL Deleted]** status.

1. As tabelas que não forem mais usadas serão excluídas usando o seguinte query:

   ```
   DROP TABLE wkDlv_15487_1;
   ```

### Limpeza de rejeitos gerados pelas importações {#cleanup-of-rejects-generated-by-imports-}

Esta etapa permite excluir registros para os quais todos os dados não foram processados durante a importação.

1. A exclusão em massa é realizada na tabela **XtkReject** com o seguinte query:

   ```
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l))
   ```

   em que **$(curDate)** é a data atual do servidor a partir da qual subtraímos o período definido para a opção **NmsCleanup_RejectsPurgeDelay** (consulte o assistente [de](#deployment-wizard)implantação) e **$(l)** é o número máximo de registros a serem excluídos em massa.

1. Todos os rejeitos órfãos são depois excluídos usando o seguinte query:

   ```
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### Limpeza de instâncias de fluxo de trabalho {#cleanup-of-workflow-instances}

Essa tarefa limpa cada instância do fluxo de trabalho usando seu identificador (**lWorkflowId**) e histórico (**lHistory**). Ele exclui tabelas inativas executando a tarefa de limpeza da mesa de trabalho novamente. A limpeza também exclui todas as tabelas de trabalho órfãs (wkf% e wkfhisto%) de workflows excluídos.

>[!NOTE]
>
>A frequência de expurgação do histórico é especificada para cada fluxo de trabalho no campo **Histórico em dias** (valor padrão 30 dias). Esse campo pode ser encontrado na guia **Execução** das propriedades do fluxo de trabalho. Para obter mais informações, consulte [esta seção](../../workflow/using/workflow-properties.md#execution).

1. Para recuperar a lista de workflows a serem excluídos, é usado o seguinte query:

   ```
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. Este query gera a lista de workflows que serão usados para excluir todos os registros vinculados, tarefas concluídas e eventos concluídos, usando os seguintes query:

   ```
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   onde **$(fluxo de trabalho)** é o identificador do fluxo de trabalho e **$(histórico)** é o identificador do histórico.

1. Todas as tabelas não usadas são excluídas. Para essa finalidade, todas as tabelas são coletadas graças a uma máscara de tipo **wkf%** usando o seguinte query (postgresql):

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Em seguida, todas as tabelas usadas por uma instância de fluxo de trabalho pendente são excluídas. A lista de workflows ativos é recuperada usando o seguinte query:

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. Cada identificador de fluxo de trabalho é recuperado para localizar o nome das tabelas usadas pelos workflows em andamento. Esses nomes são excluídos da lista de tabelas recuperadas anteriormente.
1. As tabelas de histórico de atividades do tipo &quot;query incremental&quot; são excluídas usando os seguintes query:

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   onde **$(strcondition)** é a lista de tabelas que correspondem à máscara **wkfhisto%** .

1. As tabelas restantes são excluídas usando o seguinte query:

   ```
   DROP TABLE wkf15487_12;
   ```

### Limpeza de logons de fluxo de trabalho {#cleanup-of-workflow-logins}

Esta tarefa exclui os logons do fluxo de trabalho usando o seguinte query:

```
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### Limpeza de tabelas de trabalho órfãs {#cleanup-of-orphan-work-tables}

Esta tarefa exclui tabelas de trabalho órfãs vinculadas a grupos. A tabela **NmsGroup** armazena os grupos a serem limpos (com um tipo diferente de 0). O prefixo dos nomes das tabelas é **grp**. Para identificar os grupos a serem limpos, é usado o seguinte query:

```
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### Limpeza de visitantes {#cleanup-of-visitors}

Esta tarefa exclui registros obsoletos da tabela de visitantes usando a exclusão em massa. Os registros obsoletos são aqueles para os quais a última modificação é anterior ao período de conservação definido no assistente de implantação (consulte o assistente [de](#deployment-wizard)implantação). O query a seguir é usado:

```
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

em que **$(tsDate)** é a data atual do servidor, a partir da qual subtraímos o período definido para a opção **NmsCleanup_VisitorPurgeDelay** .

### Limpeza da NAPI {#cleanup-of-npai}

Esta tarefa permite que você exclua registros que correspondem a endereços válidos da tabela **NmsAddress** . O query a seguir é usado para executar a exclusão em massa:

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

onde **o status 2** corresponde ao **[!UICONTROL Valid]** status, **$(tsDate1)** é a data atual do servidor e **$(tsDate2)** corresponde à opção **NmsCleanup_LastCleanup** .

### Limpeza de subscrições {#cleanup-of-subscriptions-}

Esta tarefa limpa todas as subscrições excluídas pelo usuário da tabela **NmsSubscription** , usando exclusão em massa. O query a seguir é usado:

```
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### Limpeza de logs de rastreamento {#cleanup-of-tracking-logs}

Esta tarefa exclui registros obsoletos das tabelas de log de rastreamento e de rastreamento da Web. Os registros obsoletos são os anteriores ao período de conservação definido no assistente de implantação (consulte o assistente [de](#deployment-wizard)implantação).

1. Primeiro, a lista das tabelas de log de rastreamento é recuperada usando o seguinte query:

   ```
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. A exclusão em massa é usada para expurgar todas as tabelas na lista de tabelas recuperadas anteriormente. O query a seguir é usado:

   ```
   DELETE FROM XtkTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM XtkTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   em que **$(tsDate)** é a data atual do servidor a partir da qual subtraímos o período definido para a opção **NmsCleanup_TrackingLogPurgeDelay** .

1. A tabela de estatísticas de rastreamento é limpa usando a exclusão em massa. O query a seguir é usado:

   ```
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   em que **$(tsDate)** é a data atual do servidor a partir da qual subtraímos o período definido para a opção **NmsCleanup_TrackingStatPurgeDelay** .

### Limpeza de logs do delivery {#cleanup-of-delivery-logs}

Essa tarefa permite que você expurgue os logs do delivery armazenados em várias tabelas.

1. Para essa finalidade, a lista dos schemas de log de delivery é recuperada usando o seguinte query:

   ```
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. Ao usar mid-sourcing, a tabela **NmsBroadLogMid** não é referenciada nos mapeamentos de delivery. O schema **nms:wideLogMid** é adicionado à lista recuperada pelo query anterior.
1. O fluxo de trabalho de limpeza **do** banco de dados remove dados obsoletos de tabelas recuperadas anteriormente. O query a seguir é usado:

   ```
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   em que **$(tableName)** é o nome de cada tabela na lista de schemas e **$(option)** é a data definida para a opção **NmsCleanup_BroadLogPurgeDelay** (consulte o assistente [de](#deployment-wizard)implantação).

1. Finalmente, o fluxo de trabalho verifica se a tabela **NmsProviderMsgId** existe. Em caso afirmativo, todos os dados obsoletos serão excluídos usando o seguinte query:

   ```
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   onde **$(opção)** corresponde à data definida para a opção **NmsCleanup_BroadLogPurgeDelay** (consulte o assistente [de](#deployment-wizard)implantação).

### Limpeza da tabela NmsEmailErrorStat {#cleanup-of-the-nmsemailerrorstat-table-}

Esta tarefa limpa a tabela **NmsEmailErrorStat** . O programa principal (**coalesceErrors**) define duas datas:

* **Data** do start: data do próximo processo que corresponde à opção **NmsLastErrorStateCoalesce** ou a data mais recente na tabela.
* **Data** de término: data atual do servidor.

Se a data de start for maior ou igual à data de término, nenhum processo ocorrerá. Nesse caso, a mensagem **coalesceUpToDate** é exibida.

Se a data do start for anterior à data de término, a tabela **NmsEmailErrorStat** será limpa.

O número total de erros na tabela **NmsEmailErrorStat** , entre as datas de start e término, é recuperado usando o seguinte query:

```
"SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)"
```

onde **$end** e **$start** são as datas de start e término definidas anteriormente.

Se o total for maior que 0:

1. O query a seguir é executado para manter somente erros além de um determinado limite (que é igual a 20):

   ```
   "SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20"
   ```

1. A mensagem **coalescingErrors** é exibida.
1. Uma nova conexão é criada para excluir todos os erros que ocorreram entre as datas de start e término. O query a seguir é usado:

   ```
   "DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)"
   ```

1. Cada erro é salvo na tabela **NmsEmailErrorStat** usando o seguinte query:

   ```
   "INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))"
   ```

   em que cada variável corresponde a um valor recuperado pelo query anterior.

1. A variável **start** é atualizada com os valores do processo anterior para concluir o loop.

O ciclo e a tarefa param.

As limpas são executadas nas tabelas **NmsEmailError** e **cleanupNmsMxDomain** .

### Limpeza da tabela NmsEmailError {#cleanup-of-the-nmsemailerror-table-}

O query a seguir é usado:

```
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Este query exclui todas as linhas sem registros vinculados no **NmsEmailErrorStat** da tabela **NmsEmailError** .

### Limpeza da tabela NmsMxDomain {#cleanup-of-the-nmsmxdomain-table-}

O query a seguir é usado:

```
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Este query exclui todas as linhas sem um registro vinculado na tabela **NmsEmailErrorStat** da tabela **NmsMxDomain** .

### Limpeza das proposições {#cleanup-of-propositions}

Se o módulo **Interaction** estiver instalado, essa tarefa será executada para expurgar as tabelas **NmsPropositionXxx** .

A lista das tabelas de proposições é recuperada e a exclusão em massa é realizada em cada uma delas, usando o seguinte query:

```
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

onde **$(opção)** é a data definida para a opção **NmsCleanup_PropositionPurgeDelay** (consulte o assistente [de](#deployment-wizard)implantação).

### Limpeza das tabelas de simulação {#cleanup-of-simulation-tables}

Esta tarefa limpa tabelas de simulação órfãs (que não estão mais vinculadas a uma simulação de oferta ou a uma simulação de delivery).

1. Para recuperar a lista das simulações que exigem limpeza, é usado o seguinte query:

   ```
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. O nome das tabelas a serem excluídas é composto pelo prefixo **wkSimu_** seguido pelo identificador da simulação (por exemplo: **wkSimu_456831_aggr**):

   ```
   DROP TABLE wkSimu_456831_aggr
   ```

### Limpeza da trilha de auditoria {#cleanup-of-audit-trail}

O query a seguir é usado:

```
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

em que **$(tsDate)** é a data atual do servidor a partir da qual o período definido para a opção **XtkCleanup_AuditTrailPurgeDelay** está substracto.

### Limpeza de Nmsaddress {#cleanup-of-nmsaddress}

O query a seguir é usado:

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

Este query exclui todas as entradas relacionadas ao iOS e Android.

### Atualização de estatísticas e otimização de armazenamentos {#statistics-update}

A opção **XtkCleanup_NoStats** permite controlar o comportamento da etapa de otimização do armazenamento do fluxo de trabalho de limpeza.

Se a opção **XtkCleanup_NoStats** não existir ou se seu valor for 0, isso executará a otimização do armazenamento no modo detalhado (VACUUM VERBOSE ANALYZE) no PostgreSQL e atualizará as estatísticas em todos os outros bancos de dados. Para verificar se esse comando é executado, verifique os logs do PostgreSQL. O VACUUM emitirá linhas no formato: `INFO: vacuuming "public.nmsactivecontact"` e o ANALYZE emitirá linhas no formato: `INFO: analyzing "public.nmsactivecontact"`.

Se o valor da opção for 1, a atualização de estatísticas não será executada em nenhum banco de dados. A seguinte linha de log será exibida nos logs do fluxo de trabalho: `Option 'XtkCleanup_NoStats' is set to '1'`.

Se o valor da opção for 2, isso executará a análise do armazenamento no modo detalhado (ANALYZE VERBOSE) no PostgreSQL e atualizará as estatísticas em todos os outros bancos de dados. Para verificar se esse comando é executado, verifique os logs do PostgreSQL. O ANALYZE emitirá linhas no formato: `INFO: analyzing "public.nmsactivecontact"`.

### Limpeza de subscrições (NMAC) {#subscription-cleanup--nmac-}

Esta tarefa exclui quaisquer subscrições relacionadas a serviços ou aplicativos móveis excluídos.

Para recuperar a lista de schemas de catálogo, é usado o seguinte query:

```
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

Em seguida, a tarefa recupera os nomes das tabelas vinculadas ao link **appSubscription** e exclui essas tabelas.

Esse fluxo de trabalho de limpeza também exclui todas as entradas em que idisabled = 1 que não foram atualizadas desde o tempo definido na opção **NmsCleanup_AppSubscriptionRcpPurgeDelay** .

### Informações da sessão de limpeza {#cleansing-session-information}

Esta tarefa limpa as informações da tabela **sessionInfo** , sendo usado o seguinte query:

```
 DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### Limpeza de eventos expirados {#cleansing-expired-events}

Essa tarefa limpa os eventos recebidos e armazenados nas instâncias de execução e os eventos arquivados em uma instância de controle.

### Reações limpezas {#cleansing-reactions}

Esta tarefa limpa as reações (tabela **NmsRemaMatchRcp**) nas quais as hipóteses foram eliminadas.
