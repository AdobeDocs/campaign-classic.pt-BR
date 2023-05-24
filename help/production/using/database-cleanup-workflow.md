---
product: campaign
title: Fluxo de trabalho de limpeza do banco de dados
description: Saiba como os dados obsoletos são limpos automaticamente
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 75d3a0af-9a14-4083-b1da-2c1b22f57cbe
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '2823'
ht-degree: 1%

---

# Fluxo de trabalho de limpeza do banco de dados{#database-cleanup-workflow}



## Introdução {#introduction}

A variável **[!UICONTROL Database cleanup]** fluxo de trabalho acessível por meio da **[!UICONTROL Administration > Production > Technical workflows]** permite excluir dados obsoletos para evitar o crescimento exponencial do banco de dados. O fluxo de trabalho é acionado automaticamente sem a intervenção do usuário.

![cleanup](assets/ncs_cleanup_workflow.png)

## Configuração {#configuration}

A limpeza do banco de dados é configurada em dois níveis: no agendador de workflow e no assistente de implantação.

### Programador de workflow {#the-scheduler}

>[!NOTE]
>
>Para saber mais sobre o scheduler, consulte [esta seção](../../workflow/using/scheduler.md).

Por padrão, a variável **[!UICONTROL Database cleanup]** O fluxo de trabalho do está configurado para iniciar diariamente às 4h. O scheduler permite alterar a frequência de acionamento do workflow. As seguintes frequências estão disponíveis:

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![scheduler](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>A fim de assegurar a **[!UICONTROL Database cleanup]** para que o workflow inicie na data e hora definidas no scheduler, o mecanismo de workflow (wfserver) deve ser iniciado.

### Assistente de implantação {#deployment-wizard}

A variável **[!UICONTROL Deployment wizard]**, acessado pelo **[!UICONTROL Tools > Advanced]** permite configurar por quanto tempo os dados serão salvos. Os valores são expressos em dias. Se esses valores não forem alterados, o workflow usará os valores padrão.

![](assets/ncs_cleanup_deployment-wizard.png)

Os campos do **[!UICONTROL Purge of data]** coincidem com as opções a seguir. Eles são usados por algumas das tarefas executadas pelo **[!UICONTROL Database cleanup]** workflow:

* Rastreamento consolidado: **NmsCleanup_TrackingStatPurgeDelay** (consulte [Limpeza de logs de rastreamento](#cleanup-of-tracking-logs))
* Logs de entrega: **NmsCleanup_BroadLogPurgeDelay** (consulte [Limpeza de logs de entrega](#cleanup-of-delivery-logs))
* Logs de rastreamento: **NmsCleanup_TrackingLogPurgeDelay** (consulte [Limpeza de logs de rastreamento](#cleanup-of-tracking-logs))
* Entregas excluídas: **NmsCleanup_RecycledDeliveryPurgeDelay** (consulte [Limpeza de entregas a serem excluídas ou recicladas](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* Importação de rejeitos: **NmsCleanup_RejectsPurgeDelay** (consulte [Limpeza de rejeições geradas por importações](#cleanup-of-rejects-generated-by-imports-))
* Perfis do visitante: **NmsCleanup_VisitorPurgeDelay** (consulte [Limpeza de visitantes](#cleanup-of-visitors))
* Apresentações da oferta: **NmsCleanup_PropositionPurgeDelay** (consulte [Limpeza de apresentações](#cleanup-of-propositions))

   >[!NOTE]
   >
   >A variável **[!UICONTROL Offer propositions]** o campo só está disponível quando a variável **Interação** O módulo do está instalado.

* Eventos: **NmsCleanup_EventPurgeDelay** (consulte [Limpeza de eventos expirados](#cleansing-expired-events))
* Eventos arquivados: **NmsCleanup_EventHistoPurgeDelay** (consulte [Limpeza de eventos expirados](#cleansing-expired-events))

   >[!NOTE]
   >
   >A variável **[!UICONTROL Events]** e **[!UICONTROL Archived events]** os campos só estarão disponíveis se a variável **Centro de mensagens** O módulo do está instalado.

* Trilha de auditoria: **XtkCleanup_AuditTrailPurgeDelay** (consulte [Limpeza da Trilha de auditoria](#cleanup-of-audit-trail))

Todas as tarefas executadas pelo **[!UICONTROL Database cleanup]** fluxo de trabalho são descritos na seção a seguir.

## Tarefas realizadas pelo workflow de limpeza do banco de dados {#tasks-carried-out-by-the-database-cleanup-workflow}

Na data e hora definidas no scheduler do workflow (consulte [O programador](#the-scheduler)), o mecanismo de workflow inicia o processo de limpeza do banco de dados. A Limpeza do banco de dados se conecta ao banco de dados e executa as tarefas na sequência mostrada abaixo.

>[!IMPORTANT]
>
>Se uma dessas tarefas falhar, as próximas não serão executadas.
>
>Consultas SQL com um **LIMITE** atributo são executados repetidamente até que todas as informações sejam processadas.


### Listas para excluir a limpeza {#lists-to-delete-cleanup}

A primeira tarefa executada pelo **[!UICONTROL Database cleanup]** o fluxo de trabalho exclui todos os grupos com **deleteStatus!= 0** atributo do **NmsGroup**. Os registros vinculados a esses grupos e que existem em outras tabelas também são excluídos.

1. As listas a serem excluídas são recuperadas usando a seguinte consulta SQL:

   ```sql
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. Cada lista tem vários links para outras tabelas. Todos esses links são excluídos em massa usando a seguinte query:

   ```sql
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   onde `$(relatedTable)` é uma tabela relacionada a **NmsGroup** e `$(l)` é o identificador da lista.

1. Quando a lista é do tipo &quot;Lista&quot;, a tabela associada é excluída usando a seguinte query:

   ```sql
   DROP TABLE grp$(l)
   ```

1. A cada **Selecionar** A lista de tipos recuperada pela operação é excluída usando a seguinte query:

   ```sql
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   onde `$(l)` é o identificador da lista

### Limpeza de entregas a serem excluídas ou recicladas {#cleanup-of-deliveries-to-be-deleted-or-recycled}

Esta tarefa limpa todos os deliveries a serem excluídos ou reciclados.

1. A variável **[!UICONTROL Database cleanup]** O fluxo de trabalho seleciona todos os deliveries para os quais **deleteStatus** o campo tem o valor **[!UICONTROL Yes]** ou **[!UICONTROL Recycled]** e cuja data de exclusão seja anterior ao período definido na variável **[!UICONTROL Deleted deliveries]** (**NmsCleanup_RecycledDeliveryPurgeDelay**) do assistente de implantação. Para obter mais informações, consulte [Assistente de implantação](#deployment-wizard). Este período é calculado em relação à data atual do servidor.
1. Para cada servidor mid-sourcing, a tarefa seleciona a lista de deliveries a serem excluídos.
1. A variável **[!UICONTROL Database cleanup]** o workflow exclui logs do delivery, anexos, informações de mirror page e todos os outros dados relacionados.
1. Antes de excluir o delivery definitivamente, o workflow limpa as informações vinculadas das seguintes tabelas:

   * Na tabela de exclusão de delivery (**NmsDlvExclusion**), a seguinte query é usada:

      ```sql
      DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
      ```

      onde **$(l)** é o identificador da entrega.

   * Na tabela de cupons (**NmsCouponValue**), a seguinte consulta é usada (com exclusões em massa):

      ```sql
      DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
      ```

      onde `$(l)` é o identificador da entrega.

   * Nas tabelas de log do delivery (**NmsBroadlogXxx**), as exclusões em massa são executadas em lotes de 20.000 registros.
   * Nas tabelas de apresentação de ofertas (**NmsPropositionXxx**), as exclusões em massa são executadas em lotes de 20.000 registros.
   * Nas tabelas de log de rastreamento (**NmsTrackinglogXxx**), as exclusões em massa são executadas em lotes de 20.000 registros.
   * Na tabela de fragmentos do delivery (**NmsDeliveryPart**), as exclusões em massa são executadas em lotes de 500.000 registros. Esta tabela contém informações de personalização sobre as mensagens restantes a serem entregues.
   * Na tabela de fragmento de dados da mirror page (**NmsMirrorPageInfo**), as exclusões em massa são executadas em lotes de 20.000 registros para peças de entrega expiradas e para peças acabadas ou canceladas. Esta tabela contém informações de personalização de todas as mensagens usadas para gerar mirror pages.
   * Na tabela de pesquisa da mirror page (**NmsMirrorPageSearch**), as exclusões em massa são executadas em lotes de 20.000 registros. Esta tabela é um índice de pesquisa que fornece acesso às informações de personalização armazenadas no **NmsMirrorPageInfo** tabela.
   * Na tabela de log do processo em lote (**XtkJobLog**), as exclusões em massa são executadas em lotes de 20.000 registros. Esta tabela contém o log de deliveries a serem excluídos.
   * Na tabela de rastreamento do URL de entrega (**NmsTrackingUrl**), a seguinte query é usada:

      ```sql
      DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
      ```

      onde `$(l)` é o identificador da entrega.

      Esta tabela contém os URLs encontrados nos deliveries a serem excluídos para ativar o rastreamento.

1. O delivery é excluído da tabela de delivery (**NmsDelivery**):

   ```sql
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   onde `$(l)` é o identificador da entrega.

#### Entregas usando mid-sourcing {#deliveries-using-mid-sourcing}

A variável **[!UICONTROL Database cleanup]** o fluxo de trabalho também exclui deliveries nos servidores mid-sourcing.

1. Para fazer isso, o workflow verifica se cada delivery está inativo (com base em seu status ). Se um delivery estiver ativo, ele será interrompido antes de ser excluído. A verificação é realizada executando a seguinte query:

   ```sql
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   onde **$(l)** é o identificador da entrega.

1. Se o valor do status for **[!UICONTROL Start pending]** , **[!UICONTROL In progress]** , **[!UICONTROL Recovery pending]** , **[!UICONTROL Recovery in progress]** , **[!UICONTROL Pause requested]** , **[!UICONTROL Pause in progress]** ou **[!UICONTROL Paused]** (valores 51, 55, 61, 62, 71, 72, 75), o delivery é interrompido e a tarefa limpa as informações vinculadas.

### Limpeza de entregas expiradas {#cleanup-of-expired-deliveries}

Esta tarefa interrompe os deliveries cujo período de validade expirou.

1. A variável **[!UICONTROL Database cleanup]** workflow cria a lista de deliveries que expiraram. Esta lista inclui todas as entregas expiradas com um status diferente de **[!UICONTROL Finished]** , bem como deliveries interrompidos recentemente com mais de 10.000 mensagens não processadas. A seguinte query é usada:

   ```sql
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   onde `delivery mode 1` corresponde ao **[!UICONTROL Mass delivery]** modo, `state 51` corresponde ao **[!UICONTROL Start pending]** estado, `state 85` corresponde ao **[!UICONTROL Stopped]** e o maior número de logs de entrega atualizados em massa no servidor de entrega for igual a 10.000.

1. O workflow inclui a lista de deliveries expirados recentemente que usam mid-sourcing. Os deliveries para os quais nenhum log de delivery ainda foi recuperado por meio do servidor mid-sourcing são excluídos.

   A seguinte query é usada:

   ```sql
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. A consulta a seguir é usada para detectar se a conta externa ainda está ativa ou não, para filtrar deliveries por data:

   ```sql
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. Na lista de deliveries expirados, os logs do delivery cujo status é **[!UICONTROL Pending]** , alterne para **[!UICONTROL Delivery cancelled]** e todos os deliveries nessa lista alternam para **[!UICONTROL Finished]** .

   As seguintes queries são usadas:

   ```sql
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   onde `$(curdate)`é a data atual do servidor de banco de dados, `$(bl)` é o identificador da mensagem de logs do delivery, `$(dl)` é o identificador de delivery, `delivery status 6` corresponde ao **[!UICONTROL Pending]** status e `delivery status 7` corresponde ao **[!UICONTROL Delivery cancelled]** status.

   ```sql
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   onde `delivery state 95` corresponde ao **[!UICONTROL Finished]** status e `$(dl)` é o identificador da entrega.

1. Todos os fragmentos (**deliveryParts**) de deliveries obsoletos são deletados e todos os fragmentos obsoletos de deliveries de notificação em andamento são deletados. A exclusão em massa é usada para essas tarefas.

   As seguintes queries são usadas:

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   onde `delivery state 95` corresponde ao **[!UICONTROL Finished]** status, `delivery state 85` corresponde ao **[!UICONTROL Stopped]** status e `$(curDate)` é a data atual do servidor.

### Limpeza de mirror pages {#cleanup-of-mirror-pages}

Essa tarefa exclui os recursos da Web (mirror pages) usados pelos deliveries.

1. Primeiro, a lista de deliveries a serem removidos é recuperada usando a seguinte query:

   ```sql
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)
   ```

   onde `$(curDate)` é a data atual do servidor.

1. A variável **NmsMirrorPageInfo** A tabela é então removida, se necessário, usando o identificador do delivery recuperado anteriormente. A exclusão em massa é usada para gerar as seguintes consultas:

   ```sql
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   ```sql
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   onde `$(dl)` é o identificador da entrega.

1. Uma entrada é adicionada ao log de delivery.
1. Os deliveries removidos são identificados para evitar a necessidade de reprocessá-los posteriormente. A seguinte consulta é executada:

   ```sql
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   onde `$(strIn)` é a lista de identificadores de delivery.

### Limpeza de tabelas de trabalho {#cleanup-of-work-tables}

Essa tarefa exclui do banco de dados todas as tabelas de trabalho que correspondem a deliveries cujo status é **[!UICONTROL Being edited]** , **[!UICONTROL Stopped]** ou **[!UICONTROL Deleted]** .

1. A lista de tabelas com nomes que começam com **wkDlv_** é recuperado primeiro com a seguinte consulta (postgresql):

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. As tabelas usadas por workflows em andamento são excluídas. Para fazer isso, a lista de deliveries em andamento é recuperada usando a seguinte query:

   ```sql
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   onde `0` é o valor que corresponde à variável **[!UICONTROL Being edited]** status do delivery, `85` corresponde ao **[!UICONTROL Stopped]** status e `100` corresponde ao **[!UICONTROL Deleted]** status.

1. As tabelas que não são mais usadas serão excluídas usando a seguinte query:

   ```sql
   DROP TABLE wkDlv_15487_1;
   ```

### Limpeza de rejeições geradas por importações {#cleanup-of-rejects-generated-by-imports-}

Essa etapa permite excluir registros cujos dados não foram processados durante a importação.

1. A exclusão em massa é realizada no **XtkReject** tabela com a seguinte consulta:

   ```sql
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l)
   ```

   onde `$(curDate)` é a data atual do servidor da qual subtraímos o período definido para o **NmsCleanup_RejectsPurgeDelay** (consulte [Assistente de implantação](#deployment-wizard)) e `$(l)` é o número máximo de registros a serem excluídos em massa.

1. Todas as rejeições órfãs são excluídas usando a seguinte query:

   ```sql
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### Limpeza de instâncias de fluxo de trabalho {#cleanup-of-workflow-instances}

Essa tarefa limpa cada instância de workflow usando seu identificador (**lWorkflowId**) e histórico (**lHistórico**). Ele exclui tabelas inativas executando a tarefa de limpeza da tabela de trabalho novamente. A limpeza também exclui todas as tabelas de trabalho órfãs (wkf% e wkfhisto%) dos fluxos de trabalho excluídos.

>[!NOTE]
>
>A frequência de limpeza do histórico é especificada para cada workflow na variável **Histórico em dias** (valor padrão de 30 dias). Esse campo pode ser encontrado no campo **Execução** das propriedades do workflow. Para obter mais informações, consulte [esta seção](../../workflow/using/workflow-properties.md#execution).

1. Para recuperar a lista de workflows a serem excluídos, a seguinte query é usada:

   ```sql
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. Essa consulta gera a lista de workflows que será usada para excluir todos os logs vinculados, tarefas concluídas e eventos concluídos, usando as seguintes consultas:

   ```sql
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```sql
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```sql
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   onde `$(lworkflow)` é o identificador do fluxo de trabalho e `$(lhistory)` é o identificador do histórico.

1. Todas as tabelas não utilizadas são excluídas. Para esse efeito, todas as tabelas são recolhidas graças a uma **wkf%** digite a máscara usando a seguinte query (postgresql):

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Em seguida, todas as tabelas usadas por uma instância de workflow pendente são excluídas. A lista de workflows ativos é recuperada usando a seguinte query:

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. Cada identificador de workflow é então recuperado para encontrar o nome das tabelas usadas pelos workflows em andamento. Esses nomes são excluídos da lista de tabelas recuperadas anteriormente.
1. as tabelas de histórico de atividades do tipo &quot;consulta incremental&quot; são excluídas usando as seguintes consultas:

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   onde `$(strcondition)` é a lista de tabelas que correspondem à variável **wkfhisto%** máscara.

1. As tabelas restantes são excluídas usando a seguinte query:

   ```sql
   DROP TABLE wkf15487_12;
   ```

### Limpeza de logons do fluxo de trabalho {#cleanup-of-workflow-logins}

Essa tarefa exclui logons de fluxo de trabalho usando a seguinte query:

```sql
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### Limpeza de tabelas de trabalho órfãs {#cleanup-of-orphan-work-tables}

Esta tarefa exclui tabelas de trabalho órfãs vinculadas a grupos. A variável **NmsGroup** a tabela armazena os grupos a serem limpos (com um tipo diferente de 0). O prefixo dos nomes de tabela é **grp**. Para identificar os grupos a serem limpos, a seguinte consulta é usada:

```sql
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### Limpeza de visitantes {#cleanup-of-visitors}

Essa tarefa exclui registros obsoletos da tabela de visitantes usando a exclusão em massa. Os registros obsoletos são aqueles para os quais a última modificação é anterior ao período de conservação definido no assistente de implantação (consulte [Assistente de implantação](#deployment-wizard)). A seguinte query é usada:

```sql
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

onde `$(tsDate)` é a data atual do servidor, da qual subtraímos o período definido para o **NmsCleanup_VisitorPurgeDelay** opção.

### Limpeza da NPAI {#cleanup-of-npai}

Essa tarefa permite excluir registros que correspondem a endereços válidos da **NmsAddress** tabela. A consulta a seguir é usada para executar a exclusão em massa:

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

onde `status 2` corresponde ao **[!UICONTROL Valid]** status, `$(tsDate1)` é a data atual do servidor e `$(tsDate2)` corresponde ao **NmsCleanup_LastCleanup** opção.

### Limpeza de assinaturas {#cleanup-of-subscriptions-}

Esta tarefa limpa todas as assinaturas excluídas pelo usuário do **NmsSubscription** tabela, usando exclusão em massa. A seguinte query é usada:

```sql
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### Limpeza de logs de rastreamento {#cleanup-of-tracking-logs}

Essa tarefa exclui registros obsoletos das tabelas de log de rastreamento e de rastreamento Web. Os registros obsoletos são aqueles que são anteriores ao período de conservação definido no assistente de implantação (consulte [Assistente de implantação](#deployment-wizard)).

1. Primeiro, a lista de tabelas de log de rastreamento é recuperada usando a seguinte query:

   ```sql
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. A exclusão em massa é usada para limpar todas as tabelas na lista de tabelas recuperadas anteriormente. A seguinte query é usada:

   ```sql
   DELETE FROM NmsTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM NmsTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   onde `$(tsDate)` é a data atual do servidor da qual subtraímos o período definido para o **NmsCleanup_TrackingLogPurgeDelay** opção.

1. A tabela de estatísticas de rastreamento é removida usando a exclusão em massa. A seguinte query é usada:

   ```sql
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   onde `$(tsDate)` é a data atual do servidor da qual subtraímos o período definido para o **NmsCleanup_TrackingStatPurgeDelay** opção.

### Limpeza de logs de entrega {#cleanup-of-delivery-logs}

Essa tarefa permite limpar os logs de delivery armazenados em várias tabelas.

1. Para essa finalidade, a lista de schemas de log de delivery é recuperada usando a seguinte query:

   ```sql
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. Ao utilizar o mid-sourcing, a **NmsBroadLogMid** a tabela não é referenciada nos mapeamentos de entrega. A variável **nms:broadLogMid** O schema é adicionado à lista recuperada pela consulta anterior.
1. A variável **Limpeza do banco de dados** O workflow então expurga dados obsoletos de tabelas recuperadas anteriormente. A seguinte query é usada:

   ```sql
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   onde `$(tableName)` é o nome de cada tabela na lista de schemas e `$(option)` é a data definida para o **NmsCleanup_BroadLogPurgeDelay** (consulte [Assistente de implantação](#deployment-wizard)).

1. Por fim, o workflow verifica se o **NmsProviderMsgId** tabela existente. Em caso afirmativo, todos os dados obsoletos são excluídos usando a seguinte query:

   ```sql
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   onde `$(option)` corresponde à data definida para o **NmsCleanup_BroadLogPurgeDelay** (consulte [Assistente de implantação](#deployment-wizard)).

### Limpeza da tabela NmsEmailErrorStat {#cleanup-of-the-nmsemailerrorstat-table-}

Essa tarefa limpa as **NmsEmailErrorStat** tabela. O programa principal (**aglutinarErros**) define duas datas:

* **Data inicial**: data do próximo processo que corresponde à **NmsLastErrorStatCoalesce** ou a data mais recente na tabela.
* **Data final**: data atual do servidor.

Se a data de início for posterior ou igual à data de término, nenhum processo será executado. Neste caso, o **coalesceUpToDate** é exibida.

Se a data inicial for anterior à data final, a variável **NmsEmailErrorStat** A tabela está limpa.

O número total de erros na variável **NmsEmailErrorStat** entre as datas de início e término, é recuperada usando a seguinte query:

```sql
SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)
```

onde `$end` e `$start` são as datas de início e término definidas anteriormente.

Se o total for maior que 0:

1. A seguinte consulta é executada para manter somente os erros além de um determinado limite (que é igual a 20):

   ```sql
   SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20
   ```

1. A variável **coalescingErrors** será exibida.
1. Uma nova conexão é criada para excluir todos os erros que ocorreram entre as datas de início e término. A seguinte query é usada:

   ```sql
   DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)
   ```

1. Cada erro é salvo na variável **NmsEmailErrorStat** usando a seguinte consulta:

   ```sql
   INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))
   ```

   onde cada variável corresponde a um valor recuperado pela consulta anterior.

1. A variável **start** é atualizada com os valores do processo anterior para finalizar o loop.

O loop e a interrupção da tarefa.

As limpezas são executadas no **NmsEmailError** e **cleanupNmsMxDomain** tabelas.

### Limpeza da tabela NmsEmailError {#cleanup-of-the-nmsemailerror-table-}

A seguinte query é usada:

```sql
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Esta consulta exclui todas as linhas sem registros vinculados na **NmsEmailErrorStat** do **NmsEmailError** tabela.

### Limpeza da tabela NmsMxDomain {#cleanup-of-the-nmsmxdomain-table-}

A seguinte query é usada:

```sql
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Esta consulta exclui todas as linhas sem um registro vinculado na **NmsEmailErrorStat** tabela do **NmsMxDomain** tabela.

### Limpeza de apresentações {#cleanup-of-propositions}

Se a variável **Interação** estiver instalado, essa tarefa será executada para limpar a **NmsPropositionXxx** tabelas.

A lista de tabelas de apresentações é recuperada e a exclusão em massa é realizada em cada uma, usando a seguinte query:

```sql
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

onde `$(option)` é a data definida para o **NmsCleanup_PropositionPurgeDelay** (consulte [Assistente de implantação](#deployment-wizard)).

### Limpeza de tabelas de simulação {#cleanup-of-simulation-tables}

Essa tarefa limpa as tabelas de simulação órfãs (que não estão mais vinculadas a uma simulação de oferta ou de delivery).

1. Para recuperar a lista de simulações que exigem limpeza, a seguinte consulta é usada:

   ```sql
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. O nome das tabelas a serem excluídas é composto pelo **wkSimu_** prefixo seguido pelo identificador da simulação (por exemplo: **wkSimu_456831_aggr**):

   ```sql
   DROP TABLE wkSimu_456831_aggr
   ```

### Limpeza da Trilha de auditoria {#cleanup-of-audit-trail}

A seguinte query é usada:

```sql
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

onde **$(tsDate)** é a data atual do servidor a partir da qual o período definido para a variável **XtkCleanup_AuditTrailPurgeDelay** é subtraída.

### Limpeza de Nmsaddress {#cleanup-of-nmsaddress}

A seguinte query é usada:

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

Essa consulta exclui todas as entradas relacionadas ao iOS e Android.

### Atualização de estatísticas e otimização de armazenamento {#statistics-update}

A variável **XtkCleanup_NoStats** permite controlar o comportamento da etapa de otimização de armazenamento do fluxo de trabalho de limpeza.

Se a variável **XtkCleanup_NoStats** não existe ou se o valor for 0, isso executará a otimização de armazenamento no modo detalhado (VACUUM VERBOSE ANALYZE) no PostgreSQL e atualizará as estatísticas em todos os outros bancos de dados. Para garantir que esse comando seja executado, verifique os logs do PostgreSQL. O VÁCUO gerará linhas no formato: `INFO: vacuuming "public.nmsactivecontact"` e ANALYZE gerarão linhas no formato: `INFO: analyzing "public.nmsactivecontact"`.

Se o valor da opção for 1, a atualização de estatísticas não será executada em nenhum banco de dados. A seguinte linha de log aparecerá nos logs de workflow: `Option 'XtkCleanup_NoStats' is set to '1'`.

Se o valor da opção for 2, isso executará a análise de armazenamento no modo detalhado (ANALYZE VERBOSE) no PostgreSQL e atualizará as estatísticas em todos os outros bancos de dados. Para garantir que esse comando seja executado, verifique os logs do PostgreSQL. ANALYZE gerará linhas no formato: `INFO: analyzing "public.nmsactivecontact"`.

### Limpeza de assinatura (NMAC) {#subscription-cleanup--nmac-}

Esta tarefa exclui todas as assinaturas relacionadas a serviços ou aplicativos móveis excluídos.

Para recuperar a lista de schemas de broadlog, a seguinte consulta é usada:

```sql
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

A tarefa recupera os nomes das tabelas vinculadas ao **appSubscription** vincular e excluir essas tabelas.

Esse fluxo de trabalho de limpeza também exclui todas as entradas em que está desativado = 1 que não foram atualizadas desde o tempo definido no **NmsCleanup_AppSubscriptionRcpPurgeDelay** opção.

### Informações da sessão de limpeza {#cleansing-session-information}

Esta tarefa limpa informações do **sessionInfo** , a seguinte consulta é usada:

```sql
DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### Limpeza de eventos expirados {#cleansing-expired-events}

Essa tarefa limpa os eventos recebidos e armazenados nas instâncias de execução e os eventos arquivados em uma instância de controle.

### Reações de limpeza {#cleansing-reactions}

Esta tarefa limpa as reações (tabela **NmsRemaMatchRcp**) em que as próprias hipóteses foram excluídas.
