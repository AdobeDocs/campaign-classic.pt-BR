---
product: campaign
title: Fluxo de trabalho de limpeza do banco de dados
description: Saiba como os dados obsoletos são limpos automaticamente
feature: Monitoring, Workflows
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 75d3a0af-9a14-4083-b1da-2c1b22f57cbe
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '2829'
ht-degree: 0%

---

# Fluxo de trabalho de limpeza do banco de dados{#database-cleanup-workflow}



## Introdução {#introduction}

O fluxo de trabalho **[!UICONTROL Database cleanup]** acessível por meio do nó **[!UICONTROL Administration > Production > Technical workflows]**, permite excluir dados obsoletos para evitar o crescimento exponencial do banco de dados. O fluxo de trabalho é acionado automaticamente sem a intervenção do usuário.

![limpeza](assets/ncs_cleanup_workflow.png)

## Configuração {#configuration}

A limpeza do banco de dados é configurada em dois níveis: no agendador de workflow e no assistente de implantação.

### Programador de workflow {#the-scheduler}

>[!NOTE]
>
>Para obter mais informações sobre o scheduler, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/flow-control-activities/scheduler.html){target="_blank"}.

Por padrão, o fluxo de trabalho **[!UICONTROL Database cleanup]** é configurado para iniciar diariamente às 4h. O scheduler permite alterar a frequência de acionamento do workflow. As seguintes frequências estão disponíveis:

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![scheduler](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>Para que o fluxo de trabalho **[!UICONTROL Database cleanup]** inicie na data e hora definidas no agendador, o mecanismo de fluxo de trabalho (wfserver) deve ser iniciado.

### assistente de implantação {#deployment-assistant}

O **[!UICONTROL deployment wizard]**, acessado por meio do menu **[!UICONTROL Tools > Advanced]**, permite configurar por quanto tempo os dados são salvos. Os valores são expressos em dias. Se esses valores não forem alterados, o workflow usará os valores padrão.

![](assets/ncs_cleanup_deployment-wizard.png)

Os campos da janela **[!UICONTROL Purge of data]** coincidem com as opções a seguir. Estes são usados por algumas das tarefas executadas pelo fluxo de trabalho **[!UICONTROL Database cleanup]**:

* Rastreamento consolidado: **NmsCleanup_TrackingStatPurgeDelay** (consulte [Limpeza de logs de rastreamento](#cleanup-of-tracking-logs))
* Logs de entrega: **NmsCleanup_BroadLogPurgeDelay** (consulte [Limpeza de logs de entrega](#cleanup-of-delivery-logs))
* Logs de rastreamento: **NmsCleanup_TrackingLogPurgeDelay** (consulte [Limpeza de logs de rastreamento](#cleanup-of-tracking-logs))
* Deliveries excluídos: **NmsCleanup_RecycledDeliveryPurgeDelay** (consulte [Limpeza de deliveries a serem excluídos ou reciclados](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* Importação de rejeições: **NmsCleanup_RejectsPurgeDelay** (consulte [Limpeza de rejeições geradas por importações](#cleanup-of-rejects-generated-by-imports-))
* Perfis do visitante: **NmsCleanup_VisitorPurgeDelay** (consulte [Limpeza de visitantes](#cleanup-of-visitors))
* Apresentações da oferta: **NmsCleanup_PropositionPurgeDelay** (consulte [Limpeza de apresentações](#cleanup-of-propositions))

  >[!NOTE]
  >
  >O campo **[!UICONTROL Offer propositions]** só está disponível quando o módulo **Interaction** está instalado.

* Eventos: **NmsCleanup_EventPurgeDelay** (consulte [Eventos expirados de limpeza](#cleansing-expired-events))
* Eventos arquivados: **NmsCleanup_EventHistoPurgeDelay** (consulte [Eventos expirados de limpeza](#cleansing-expired-events))

  >[!NOTE]
  >
  >Os campos **[!UICONTROL Events]** e **[!UICONTROL Archived events]** só estarão disponíveis se o módulo **Centro de Mensagens** estiver instalado.

* Trilha de auditoria: **XtkCleanup_AuditTrailPurgeDelay** (consulte [Limpeza da Trilha de auditoria](#cleanup-of-audit-trail))

Todas as tarefas executadas pelo fluxo de trabalho **[!UICONTROL Database cleanup]** estão descritas na seção a seguir.

## Tarefas realizadas pelo workflow de limpeza do banco de dados {#tasks-carried-out-by-the-database-cleanup-workflow}

Na data e hora definidas no agendador do fluxo de trabalho (consulte [O agendador](#the-scheduler)), o mecanismo de fluxo de trabalho inicia o processo de limpeza do banco de dados. A Limpeza do banco de dados se conecta ao banco de dados e executa as tarefas na sequência mostrada abaixo.

>[!IMPORTANT]
>
>Se uma dessas tarefas falhar, as próximas não serão executadas.
>
>Consultas SQL com um atributo **LIMIT** são executadas repetidamente até que todas as informações sejam processadas.


### Listas para excluir a limpeza {#lists-to-delete-cleanup}

A primeira tarefa executada pelo fluxo de trabalho **[!UICONTROL Database cleanup]** exclui todos os grupos com **deleteStatus != 0** atributo de **NmsGroup**. Os registros vinculados a esses grupos e que existem em outras tabelas também são excluídos.

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

1. A cada lista de tipos **Select** recuperada pela operação é excluída usando a seguinte consulta:

   ```sql
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   onde `$(l)` é o identificador da lista

### Limpeza de entregas a serem excluídas ou recicladas {#cleanup-of-deliveries-to-be-deleted-or-recycled}

Esta tarefa limpa todos os deliveries a serem excluídos ou reciclados.

1. O fluxo de trabalho **[!UICONTROL Database cleanup]** seleciona todas as entregas para as quais o campo **deleteStatus** tem o valor **[!UICONTROL Yes]** ou **[!UICONTROL Recycled]** e cuja data de exclusão é anterior ao período definido no campo **[!UICONTROL Deleted deliveries]** (**NmsCleanup_RecycledDeliveryPurgeDelay**) do assistente de implantação. Para obter mais informações, consulte [assistente de implantação](#deployment-assistant). Este período é calculado em relação à data atual do servidor.
1. Para cada servidor mid-sourcing, a tarefa seleciona a lista de deliveries a serem excluídos.
1. O fluxo de trabalho **[!UICONTROL Database cleanup]** exclui logs de entrega, anexos, informações de mirror page e todos os outros dados relacionados.
1. Antes de excluir o delivery definitivamente, o workflow limpa as informações vinculadas das seguintes tabelas:

   * Na tabela de exclusão de entrega (**NmsDlvExclusion**), a seguinte consulta é usada:

     ```sql
     DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
     ```

     onde **$(l)** é o identificador da entrega.

   * Na tabela de cupons (**NmsCouponValue**), a seguinte consulta é usada (com exclusões em massa):

     ```sql
     DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
     ```

     onde `$(l)` é o identificador da entrega.

   * Nas tabelas de log de entrega (**NmsBroadlogXxx**), exclusões em massa são executadas em lotes de 20.000 registros.
   * Nas tabelas de apresentação de ofertas (**NmsPropositionXxx**), exclusões em massa são executadas em lotes de 20.000 registros.
   * Nas tabelas de log de rastreamento (**NmsTrackinglogXxx**), exclusões em massa são executadas em lotes de 20.000 registros.
   * Na tabela de fragmentos de entrega (**NmsDeliveryPart**), exclusões em massa são executadas em lotes de 500.000 registros. Esta tabela contém informações de personalização sobre as mensagens restantes a serem entregues.
   * Na tabela de fragmento de dados da mirror page (**NmsMirrorPageInfo**), as exclusões em massa são executadas em lotes de 20.000 registros para partes de entrega expiradas e para partes concluídas ou canceladas. Esta tabela contém informações de personalização de todas as mensagens usadas para gerar mirror pages.
   * Na tabela de pesquisa da mirror page (**NmsMirrorPageSearch**), exclusões em massa são executadas em lotes de 20.000 registros. Esta tabela é um índice de pesquisa que fornece acesso às informações de personalização armazenadas na tabela **NmsMirrorPageInfo**.
   * Na tabela de log do processo em lote (**XtkJobLog**), exclusões em massa são executadas em lotes de 20.000 registros. Esta tabela contém o log de deliveries a serem excluídos.
   * Na tabela de rastreamento de URL de entrega (**NmsTrackingUrl**), a seguinte consulta é usada:

     ```sql
     DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
     ```

     onde `$(l)` é o identificador da entrega.

     Esta tabela contém os URLs encontrados nos deliveries a serem excluídos para ativar o rastreamento.

1. A entrega foi excluída da tabela de entrega (**NmsDelivery**):

   ```sql
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   onde `$(l)` é o identificador da entrega.

#### Entregas usando mid-sourcing {#deliveries-using-mid-sourcing}

O fluxo de trabalho **[!UICONTROL Database cleanup]** também exclui entregas no(s) servidor(es) mid-sourcing.

1. Para fazer isso, o workflow verifica se cada delivery está inativo (com base em seu status ). Se um delivery estiver ativo, ele será interrompido antes de ser excluído. A verificação é realizada executando a seguinte query:

   ```sql
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   onde **$(l)** é o identificador da entrega.

1. Se o valor do status for **[!UICONTROL Start pending]** , **[!UICONTROL In progress]** , **[!UICONTROL Recovery pending]** , **[!UICONTROL Recovery in progress]** , **[!UICONTROL Pause requested]** , **[!UICONTROL Pause in progress]** ou **[!UICONTROL Paused]** (valores 51, 55, 61, 62, 71, 72, 75), a entrega será interrompida e a tarefa limpará as informações vinculadas.

### Limpeza de entregas expiradas {#cleanup-of-expired-deliveries}

Esta tarefa interrompe os deliveries cujo período de validade expirou.

1. O fluxo de trabalho **[!UICONTROL Database cleanup]** cria a lista de entregas que expiraram. Esta lista inclui todas as entregas expiradas com status diferente de **[!UICONTROL Finished]**, bem como entregas interrompidas recentemente com mais de 10.000 mensagens não processadas. A seguinte query é usada:

   ```sql
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   onde `delivery mode 1` corresponde ao modo **[!UICONTROL Mass delivery]**, `state 51` corresponde ao estado **[!UICONTROL Start pending]**, `state 85` corresponde ao estado **[!UICONTROL Stopped]** e o número mais alto de logs de entrega atualizados em massa no servidor de entrega é igual a 10.000.

1. O workflow inclui a lista de deliveries expirados recentemente que usam mid-sourcing. Os deliveries para os quais nenhum log de delivery ainda foi recuperado por meio do servidor mid-sourcing são excluídos.

   A seguinte query é usada:

   ```sql
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. A consulta a seguir é usada para detectar se a conta externa ainda está ativa ou não, para filtrar deliveries por data:

   ```sql
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. Na lista de entregas expiradas, os logs de entrega cujo status é **[!UICONTROL Pending]** , alternam para **[!UICONTROL Delivery cancelled]** e todas as entregas nessa lista alternam para **[!UICONTROL Finished]** .

   As seguintes queries são usadas:

   ```sql
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   onde `$(curdate)` é a data atual do servidor de banco de dados, `$(bl)` é o identificador da mensagem dos logs de entrega, `$(dl)` é o identificador de entrega, `delivery status 6` corresponde ao status **[!UICONTROL Pending]** e `delivery status 7` corresponde ao status **[!UICONTROL Delivery cancelled]**.

   ```sql
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   onde `delivery state 95` corresponde ao status **[!UICONTROL Finished]** e `$(dl)` é o identificador da entrega.

1. Todos os fragmentos (**deliveryParts**) de entregas obsoletas são excluídos e todos os fragmentos obsoletos de entregas de notificação em andamento são excluídos. A exclusão em massa é usada para essas tarefas.

   As seguintes queries são usadas:

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   onde `delivery state 95` corresponde ao status **[!UICONTROL Finished]**, `delivery state 85` corresponde ao status **[!UICONTROL Stopped]** e `$(curDate)` é a data atual do servidor.

### Limpeza de mirror pages {#cleanup-of-mirror-pages}

Essa tarefa exclui os recursos da Web (mirror pages) usados pelos deliveries.

1. Primeiro, a lista de deliveries a serem removidos é recuperada usando a seguinte query:

   ```sql
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)
   ```

   onde `$(curDate)` é a data atual do servidor.

1. A tabela **NmsMirrorPageInfo** é então removida, se necessário, usando o identificador da entrega recuperada anteriormente. A exclusão em massa é usada para gerar as seguintes consultas:

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

   onde `$(strIn)` é a lista de identificadores de entrega.

### Limpeza de tabelas de trabalho {#cleanup-of-work-tables}

Esta tarefa exclui do banco de dados todas as tabelas de trabalho que correspondem a entregas cujo status é **[!UICONTROL Being edited]** , **[!UICONTROL Stopped]** ou **[!UICONTROL Deleted]**.

1. A lista de tabelas com nomes começando com **wkDlv_** é recuperada primeiro com a seguinte consulta (postgresql):

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. As tabelas usadas por workflows em andamento são excluídas. Para fazer isso, a lista de deliveries em andamento é recuperada usando a seguinte query:

   ```sql
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   onde `0` é o valor que corresponde ao status de entrega **[!UICONTROL Being edited]**, `85` corresponde ao status **[!UICONTROL Stopped]** e `100` corresponde ao status **[!UICONTROL Deleted]**.

1. As tabelas que não são mais usadas serão excluídas usando a seguinte query:

   ```sql
   DROP TABLE wkDlv_15487_1;
   ```

### Limpeza de rejeições geradas por importações {#cleanup-of-rejects-generated-by-imports-}

Essa etapa permite excluir registros cujos dados não foram processados durante a importação.

1. A exclusão em massa é realizada na tabela **XtkReject** com a seguinte consulta:

   ```sql
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l)
   ```

   onde `$(curDate)` é a data atual do servidor da qual subtraímos o período definido para a opção **NmsCleanup_RejectsPurgeDelay** (consulte [assistente de implantação](#deployment-assistant)) e `$(l)` é o número máximo de registros a serem excluídos em massa.

1. Todas as rejeições órfãs são excluídas usando a seguinte query:

   ```sql
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### Limpeza de instâncias de fluxo de trabalho {#cleanup-of-workflow-instances}

Esta tarefa limpa cada instância de fluxo de trabalho usando seu identificador (**lWorkflowId**) e histórico (**lHistory**). Ele exclui tabelas inativas executando a tarefa de limpeza da tabela de trabalho novamente. A limpeza também exclui todas as tabelas de trabalho órfãs (wkf% e wkfhisto%) dos fluxos de trabalho excluídos.

>[!NOTE]
>
>A frequência de limpeza do histórico é especificada para cada fluxo de trabalho no campo **Histórico em dias** (valor padrão de 30 dias). Este campo pode ser encontrado na guia **Execution** das propriedades do fluxo de trabalho. Para obter mais informações, consulte [esta seção](../../workflow/using/workflow-properties.md#execution).

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

1. Todas as tabelas não utilizadas são excluídas. Para esta finalidade, todas as tabelas são coletadas graças a uma máscara do tipo **wkf%** usando a seguinte query (postgresql):

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

   onde `$(strcondition)` é a lista de tabelas que correspondem à máscara **wkfhisto%**.

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

Esta tarefa exclui tabelas de trabalho órfãs vinculadas a grupos. A tabela **NmsGroup** armazena os grupos a serem limpos (com um tipo diferente de 0). O prefixo dos nomes de tabela é **grp**. Para identificar os grupos a serem limpos, a seguinte consulta é usada:

```sql
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### Limpeza de visitantes {#cleanup-of-visitors}

Essa tarefa exclui registros obsoletos da tabela de visitantes usando a exclusão em massa. Registros obsoletos são aqueles para os quais a última modificação é anterior ao período de conservação definido no assistente de implantação (consulte [assistente de implantação](#deployment-assistant)). A seguinte query é usada:

```sql
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

onde `$(tsDate)` é a data atual do servidor, da qual subtraímos o período definido para a opção **NmsCleanup_VisitorPurgeDelay**.

### Limpeza da NPAI {#cleanup-of-npai}

Esta tarefa permite excluir registros que correspondem a endereços válidos da tabela **NmsAddress**. A consulta a seguir é usada para executar a exclusão em massa:

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

onde `status 2` corresponde ao status **[!UICONTROL Valid]**, `$(tsDate1)` é a data atual do servidor e `$(tsDate2)` corresponde à opção **NmsCleanup_LastCleanup**.

### Limpeza de assinaturas {#cleanup-of-subscriptions-}

Esta tarefa limpa todas as assinaturas excluídas pelo usuário da tabela **NmsSubscription**, usando a exclusão em massa. A seguinte query é usada:

```sql
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### Limpeza de logs de rastreamento {#cleanup-of-tracking-logs}

Essa tarefa exclui registros obsoletos das tabelas de log de rastreamento e de rastreamento Web. Os registros obsoletos são aqueles que são anteriores ao período de conservação definido no assistente de implantação (consulte [assistente de implantação](#deployment-assistant)).

1. Primeiro, a lista de tabelas de log de rastreamento é recuperada usando a seguinte query:

   ```sql
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. A exclusão em massa é usada para limpar todas as tabelas na lista de tabelas recuperadas anteriormente. A seguinte query é usada:

   ```sql
   DELETE FROM NmsTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM NmsTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   onde `$(tsDate)` é a data atual do servidor da qual subtraímos o período definido para a opção **NmsCleanup_TrackingLogPurgeDelay**.

1. A tabela de estatísticas de rastreamento é removida usando a exclusão em massa. A seguinte query é usada:

   ```sql
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   onde `$(tsDate)` é a data atual do servidor da qual subtraímos o período definido para a opção **NmsCleanup_TrackingStatPurgeDelay**.

### Limpeza de logs de entrega {#cleanup-of-delivery-logs}

Essa tarefa permite limpar os logs de delivery armazenados em várias tabelas.

1. Para essa finalidade, a lista de schemas de log de delivery é recuperada usando a seguinte query:

   ```sql
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. Ao usar mid-sourcing, a tabela **NmsBroadLogMid** não é referenciada nos mapeamentos de entrega. O esquema **nms:broadLogMid** foi adicionado à lista recuperada pela consulta anterior.
1. O fluxo de trabalho **Limpeza do banco de dados** limpa dados obsoletos de tabelas recuperadas anteriormente. A seguinte query é usada:

   ```sql
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   onde `$(tableName)` é o nome de cada tabela na lista de esquemas e `$(option)` é a data definida para a opção **NmsCleanup_BroadLogPurgeDelay** (consulte o [assistente de implantação](#deployment-assistant)).

1. Finalmente, o fluxo de trabalho verifica se a tabela **NmsProviderMsgId** existe. Em caso afirmativo, todos os dados obsoletos são excluídos usando a seguinte query:

   ```sql
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   onde `$(option)` corresponde à data definida para a opção **NmsCleanup_BroadLogPurgeDelay** (consulte [assistente de implantação](#deployment-assistant)).

### Limpeza da tabela NmsEmailErrorStat {#cleanup-of-the-nmsemailerrorstat-table-}

Esta tarefa limpa a tabela **NmsEmailErrorStat**. O programa principal (**coalesceErrors**) define duas datas:

* **Data de início**: data do próximo processo que corresponde à opção **NmsLastErrorStatCoalesce** ou à data mais recente na tabela.
* **Data final**: data atual do servidor.

Se a data de início for posterior ou igual à data de término, nenhum processo será executado. Nesse caso, a mensagem **coalesceUpToDate** é exibida.

Se a data de início for anterior à data de término, a tabela **NmsEmailErrorStat** será limpa.

O número total de erros na tabela **NmsEmailErrorStat**, entre as datas de início e término, é recuperado com a seguinte consulta:

```sql
SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)
```

onde `$end` e `$start` são as datas de início e término definidas anteriormente.

Se o total for maior que 0:

1. A seguinte consulta é executada para manter somente os erros além de um determinado limite (que é igual a 20):

   ```sql
   SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20
   ```

1. A mensagem **coalescingErrors** é exibida.
1. Uma nova conexão é criada para excluir todos os erros que ocorreram entre as datas de início e término. A seguinte query é usada:

   ```sql
   DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)
   ```

1. Cada erro é salvo na tabela **NmsEmailErrorStat** usando esta consulta:

   ```sql
   INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))
   ```

   onde cada variável corresponde a um valor recuperado pela consulta anterior.

1. A variável **start** foi atualizada com os valores do processo anterior para concluir o loop.

O loop e a interrupção da tarefa.

As limpezas são executadas nas tabelas **NmsEmailError** e **cleanupNmsMxDomain**.

### Limpeza da tabela NmsEmailError {#cleanup-of-the-nmsemailerror-table-}

A seguinte query é usada:

```sql
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Esta consulta exclui todas as linhas sem registros vinculados em **NmsEmailErrorStat** da tabela **NmsEmailError**.

### Limpeza da tabela NmsMxDomain {#cleanup-of-the-nmsmxdomain-table-}

A seguinte query é usada:

```sql
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Esta consulta exclui todas as linhas sem um registro vinculado na tabela **NmsEmailErrorStat** da tabela **NmsMxDomain**.

### Limpeza de apresentações {#cleanup-of-propositions}

Se o módulo **Interaction** estiver instalado, esta tarefa será executada para limpar as tabelas **NmsPropositionXxx**.

A lista de tabelas de apresentações é recuperada e a exclusão em massa é realizada em cada uma, usando a seguinte query:

```sql
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

onde `$(option)` é a data definida para a opção **NmsCleanup_PropositionPurgeDelay** (consulte [assistente de implantação](#deployment-assistant)).

### Limpeza de tabelas de simulação {#cleanup-of-simulation-tables}

Essa tarefa limpa as tabelas de simulação órfãs (que não estão mais vinculadas a uma simulação de oferta ou de delivery).

1. Para recuperar a lista de simulações que exigem limpeza, a seguinte consulta é usada:

   ```sql
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. O nome das tabelas a serem excluídas é composto do prefixo **wkSimu_** seguido pelo identificador da simulação (por exemplo: **wkSimu_456831_aggr**):

   ```sql
   DROP TABLE wkSimu_456831_aggr
   ```

### Limpeza da Trilha de auditoria {#cleanup-of-audit-trail}

A seguinte query é usada:

```sql
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

onde **$(tsDate)** é a data atual do servidor a partir da qual o período definido para a opção **XtkCleanup_AuditTrailPurgeDelay** é subtraído.

### Limpeza de Nmsaddress {#cleanup-of-nmsaddress}

A seguinte query é usada:

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

Essa consulta exclui todas as entradas relacionadas ao iOS e Android.

### Atualização de estatísticas e otimização de armazenamento {#statistics-update}

A opção **XtkCleanup_NoStats** permite controlar o comportamento da etapa de otimização de armazenamento do fluxo de trabalho de limpeza.

Se a opção **XtkCleanup_NoStats** não existir ou se seu valor for 0, ela executará a otimização de armazenamento no modo detalhado (VACUUM VERBOSE ANALYZE) no PostgreSQL e atualizará as estatísticas em todos os outros bancos de dados. Para garantir que esse comando seja executado, verifique os logs do PostgreSQL. O VACUUM gerará linhas no formato: `INFO: vacuuming "public.nmsactivecontact"` e o ANALYZE gerará linhas no formato: `INFO: analyzing "public.nmsactivecontact"`.

Se o valor da opção for 1, a atualização de estatísticas não será executada em nenhum banco de dados. A seguinte linha de log aparecerá nos logs de fluxo de trabalho: `Option 'XtkCleanup_NoStats' is set to '1'`.

Se o valor da opção for 2, isso executará a análise de armazenamento no modo detalhado (ANALYZE VERBOSE) no PostgreSQL e atualizará as estatísticas em todos os outros bancos de dados. Para garantir que esse comando seja executado, verifique os logs do PostgreSQL. ANALYZE gerará linhas no formato: `INFO: analyzing "public.nmsactivecontact"`.

### Limpeza de assinatura (NMAC) {#subscription-cleanup--nmac-}

Esta tarefa exclui todas as assinaturas relacionadas a serviços ou aplicativos móveis excluídos.

Para recuperar a lista de schemas de broadlog, a seguinte consulta é usada:

```sql
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

A tarefa recupera os nomes das tabelas vinculadas ao link **appSubscription** e exclui essas tabelas.

Esse fluxo de trabalho de limpeza também exclui todas as entradas em que está desabilitado = 1 que não foram atualizadas desde a hora definida na opção **NmsCleanup_AppSubscriptionRcpPurgeDelay**.

### Informações da sessão de limpeza {#cleansing-session-information}

Esta tarefa limpa informações da tabela **sessionInfo**. A seguinte consulta é usada:

```sql
DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### Limpeza de eventos expirados {#cleansing-expired-events}

Essa tarefa limpa os eventos recebidos e armazenados nas instâncias de execução e os eventos arquivados em uma instância de controle.

### Reações de limpeza {#cleansing-reactions}

Esta tarefa limpa as reações (tabela **NmsRemaMatchRcp**) nas quais a própria hipótese foi excluída.
