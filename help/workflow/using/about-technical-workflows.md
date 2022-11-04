---
product: campaign
title: Workflows técnicos
description: Saiba mais sobre os fluxos de trabalho técnicos disponíveis com os pacotes do Campaign Classic.
feature: Workflows
exl-id: 9aed2665-cd4b-419c-b9f2-ea04fc1d8f01
source-git-commit: 1635366b9e1302acd3d8997312bf07d5c1a68982
workflow-type: tm+mt
source-wordcount: '1705'
ht-degree: 100%

---

# Workflows técnicos{#about-technical-workflows}

![](../../assets/v7-only.svg)

## Sobre workflows técnicos {#overview}

Os fluxos de trabalho detalhados nesta seção são instalados com os diferentes pacotes integrados do Adobe Campaign. Esses pacotes e os fluxos de trabalho técnicos relacionados dependem do contrato de licença. Os pacotes integrados estão detalhados [nesta seção](../../installation/using/installing-campaign-standard-packages.md).

Por padrão, os fluxos de trabalho técnicos estão disponíveis em uma subpasta do seguinte nó **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

Observe que os fluxos de trabalho técnicos só podem ser iniciados e modificados por operadores com direito de Administração. Para obter mais informações sobre permissões, consulte esta [seção](../../platform/using/access-management-groups.md#default-groups).

>[!NOTE]
>
>Os workflows técnicos relacionados ao módulo do Centro de Mensagens estão disponíveis por padrão no nó **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Message Center]** > **[!UICONTROL Technical workflows]**.

Para obter mais informações sobre como monitorar workflows técnicos, consulte a [seção específica](monitoring-technical-workflows.md).

## Lista de workflows técnicos {#list-technical-workflows}

| Fluxo de trabalho técnico | Pacote | Descrição |
|------|--------|-----------|
| **Limpeza de alias** (aliasCleansing) | Delivery | Esse workflow padroniza os valores de enumeração. É acionado todos os dias às 3h por padrão. |
| **Faturamento** (billing) | Delivery | Esse fluxo de trabalho envia o relatório de atividades do sistema para o operador &quot;faturamento&quot; por email. É acionado todo dia 25 de cada mês na instância de marketing. |
| **Cálculo de estatísticas do Twitter** (statsTwitter) | Redes sociais (Marketing social)  - somente Campaign v7 | Esse fluxo de trabalho calcula estatísticas vinculadas a retweets e visitas no Twitter. |
| **Processos do Campaign** (operationMgt) | Campanhas de marketing (Campaign) | Esse fluxo de trabalho gerencia os processos das campanhas de marketing (inicia o direcionamento, faz a extração de arquivos etc.). Ele também cria workflows relacionados a campanhas recorrentes e periódicas. |
| **Coletar dados para o serviço HeatMap** (collectDataHeatMapService) | Instalado por padrão | Esse fluxo de trabalho recupera dados exigidos pelo serviço HeatMap. |
| **Coletar solicitações de privacidade** (collectPrivacyRequests) | Regulamento de Proteção de Dados de Privacidade | Esse fluxo de trabalho gera os dados do recipient armazenados no Adobe Campaign e os disponibiliza para baixar na tela de solicitação de privacidade. |
| **Cálculo de custo** (budgetMgt) | Campanhas de marketing (Campaign) | Esse fluxo de trabalho inicia o cálculo das linhas de despesas e custos nos orçamentos, planos, programas, campanhas, deliveries e tarefas. |
| **Limpeza do banco de dados** (limpeza) | Delivery | Este é o fluxo de trabalho manutenção do banco de dados: faz diferentes cálculos das estatísticas e dos processos e exclui dados obsoletos do banco de dados de acordo com a configuração definida no assistente de implantação. É acionado todos os dias às 4h por padrão. Para obter mais informações, consulte [esta página](../../production/using/database-cleanup-workflow.md#monitoring-campaign-classic). |
| **Excluir usuários do LINE bloqueados** (deleteBlockedLineUsersV2) | Canal LINE | Esse fluxo de trabalho garante que os dados dos usuários do LINE V2 sejam excluídos após bloquearem a conta oficial do LINE por 180 dias. |
| **Excluir dados de solicitação de privacidade** (deletePrivacyRequestsData) | Regulamento de Proteção de Dados de Privacidade | Esse fluxo de trabalho exclui os dados do recipient armazenados no Adobe Campaign. |
| **Indicadores de delivery** (deliveryIndicators) | Plataforma Mid-sourcing | Esse fluxo de trabalho atualiza os indicadores de rastreamento de delivery para um delivery. Esse fluxo de trabalho é acionado a cada hora por padrão. |
| **Processos de fórum de discussão** (newsgroupMgt) | Recursos de marketing (MRM) | Este fluxo de trabalho gerencia o delivery de notificações dos fóruns de discussão. É acionado ao receber um sinal de aprovação |
| **Processos de marketing distribuído** (centralLocalMgt) | Marketing central/local (Marketing distribuído) | Este fluxo de trabalho inicia o processamento relacionado ao uso do módulo de marketing distribuído. Ele inicia a criação de campanhas locais e gerencia notificações de pedidos e disponibilidade de pacotes de campanha. |
| **Limpeza de evento** (webAnalyticsPurgeWebEvents) | Conectores de análise da Web | Esse fluxo de trabalho permite excluir todos os eventos do campo de banco de dados de acordo com o período configurado no campo Vida útil. |
| **Exportar audiências para a Adobe Experience Cloud** (exportSharedAudience) | Integração com a Adobe Experience Cloud | Esse fluxo de trabalho exporta públicos-alvo como públicos-alvo/segmentos compartilhados. Esses públicos-alvo podem ser usados nas diferentes soluções da Adobe Experience Cloud que você usa. |
| **Previsão** (forecasting) | Delivery | Esse fluxo de trabalho analisa os deliveries salvos no calendário provisional (cria logs provisionais). É acionado todos os dias à 1h por padrão. |
| **Cálculo agregado completo (propositionrcp cube)** (agg_nmspropositionrcp_full) | Dispositivo de oferta (interação) | Esse fluxo de trabalho atualiza o agregado completo do cubo de apresentação da oferta. É acionado todos os dias às 6h por padrão. Esse agregado captura as seguintes dimensões: canal, delivery, oferta de marketing e data. O cubo de apresentação da oferta é usado para gerar relatórios com base em ofertas. Você pode saber mais sobre cubos [nesta seção](../../reporting/using/ac-cubes.md). |
| **Identificação de contatos convertidos** (webAnalyticsFindConverted) | Conectores de análise da Web | Esse fluxo de trabalho indexa os visitantes do site que concluíram sua compra após uma campanha de remarketing. Os dados recuperados por esse fluxo de trabalho podem ser acessados no relatório de eficiência de remarketing (consulte esta página). |
| **Importar audiências da Adobe Experience Cloud** (importSharedAudience) | Integração com a Adobe Experience Cloud | Esse fluxo de trabalho permite importar públicos-alvo/segmentos de diferentes soluções da Adobe Experience Cloud para o Adobe Campaign. |
| **Processos de deliveries em campanhas** (deliveryMgt) | Campanhas de marketing (Campaign) | Esse fluxo de trabalho aciona os deliveries aprovados e inicia o pós-processamento no provedor de serviços para um delivery externo. Também envia notificações e lembretes de aprovação. |
| **Processos de provedores de serviços** (supplierMgt) | Campanhas de marketing (Campaign) | Esse fluxo de trabalho inicia processos do provedor de serviços (email para o roteador e o pós-processamento) após a aprovação de deliveries. |
| **Atualização do token de acesso do LINE V2** (updateLineV2AccessToken) | Canal LINE  - somente Campaign v7 | Esse fluxo de trabalho atualiza o token de acesso para LINE V2. |
| **Migração do MID para LineUserID** (MIDToUserIDMigration) | Canal LINE | Esse fluxo de trabalho gera a ID de usuários do LINE V2 para a migração de LINE V1 para LINE V2. |
| **Notificações de recurso de marketing** (assetMgt) | Recursos de marketing (MRM) | Esse fluxo de trabalho gerencia notificações vinculadas à aprovação e à publicação de recursos de marketing. |
| **Centro de mensagens &lt;external_account_name>** (mcSynch_&lt;external_account_name>) | Controle de mensagens transacionais (Centro de mensagens - Controle) | Esse fluxo de trabalho: <ul><li>recupera a lista de eventos processados pela(s) operação(s).</li><li>sincroniza com a tabela NmsBroadLogMsg para recuperar as qualificações da mensagem de delivery.</li><li>recupera logs de delivery de eventos assim que a sincronização com a tabela NmsBroadLogMsg for concluída.</li><li>sincroniza com a tabela NmsTrackingUrl para recuperar o rastreamento para as URLs de delivery.</li><li>recupera as URLs de rastreamento de eventos assim que a sincronização com a tabela NmsTrackingUrl for concluída.</li><li>permite recuperar todos os endereços de email colocados em quarentena a cada três horas após o envio de um delivery.</li></ul> |
| **Cálculo agregado completo do MessageCenter** (agg_messageCenter_full) | Controle de mensagens transacionais (Centro de mensagens - Controle) | Esse fluxo de trabalho atualiza o agregado completo para o cubo do centro de mensagens. É acionado todos os dias às 3h por padrão. Esse agregado captura as seguintes dimensões: canal, data, status e tipo de evento. O cubo do centro de mensagens é usado para gerar relatórios com base em eventos. Você pode saber mais sobre cubos [nesta seção](../../reporting/using/ac-cubes.md) |
| **Mid-sourcing (contadores de delivery)** (defaultMidSourcingDlv) | Transferência para mid-sourcing | Esse fluxo de trabalho coleta informações de contagem para deliveries no servidor mid-sourcing. Informações de contagem incluem indicadores de deliveries gerais, como número de deliveries enviados, etc. As informações de rastreamento, como aberturas, não são incluídas. É acionado a cada dez minutos por padrão. |
| **Mid-sourcing (logs de delivery)** (defaultMidSourcingLog) | Transferência para mid-sourcing | Esse fluxo de trabalho coleta logs do delivery no servidor mid-sourcing. É acionado a cada hora por padrão. |
| **Gerenciamento de recusa de NMAC** (mobileAppOptOutMgt) | Canal de aplicativo móvel | Esse workflow atualiza a notificação de unsubscriptions em dispositivos móveis. É acionado a cada 6 horas entre 1:00 AM e meia-noite. Para obter mais detalhes, consulte [esta seção](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines). |
| **Notificação de oferta** (offerMgt) | Delivery | Esse fluxo de trabalho implanta ofertas aprovadas no ambiente online, bem como todas as categorias contidas no catálogo de oferta. |
| **Limpeza de fluxos de trabalho pausados** (cleanupPausedWorkflows) | Delivery | Triggers is translated correctly in this case. Esse fluxo de trabalho analisa fluxos de trabalho pausados que têm a severidade definida como normal e emite avisos e notificações quando ficam pausados por muito tempo. Após um mês, os workflows técnicos pausados são interrompidos definitivamente. Por padrão, é acionado toda segunda-feira às 5h. Para obter mais informações, consulte[Tratamento de fluxos de trabalho pausados](monitoring-workflow-execution.md#handling-of-paused-workflows). |
| **Limpeza de solicitação de privacidade** (cleanupPrivacyRequests) | Regulamento de Proteção de Dados de Privacidade | Esse fluxo de trabalho apaga os arquivos de solicitação de acesso criados há mais de 90 dias. |
| **Processamento de eventos em lote** (batchEventsProcessing) | Execução de mensagens transacionais (Centro de Mensagens - Execução) | Esse fluxo de trabalho permite colocar eventos em lote em uma fila antes de associá-los a um modelo de mensagem. |
| **Processamento de eventos em tempo real** (rtEventsProcessing) | Execução de mensagens transacionais (Centro de Mensagens - Execução) | Esse fluxo de trabalho permite colocar eventos em tempo real em uma fila antes de associá-los a um modelo de mensagem. |
| **Sincronização de apresentação** (propositionSynch) | Controle do mecanismo de oferta com instância de execução | Esse fluxo de trabalho sincroniza as apresentações entre a instância de marketing e a instância de execução usada para interações. |
| **Recuperação de eventos da Web** (webAnalyticsGetWebEvents) | Conectores de análise da Web | A cada hora, esse fluxo de trabalho baixa segmentos do comportamento do usuário na Internet em um determinado site, os coloca no banco de dados do Adobe Campaign e inicia o fluxo de trabalho de remarketing. |
| **Agregados de relatórios** (reportingAggregates) | Delivery | Esse fluxo de trabalho atualiza agregados usados em relatórios. É acionado todos os dias às 2h por padrão. |
| **Envio de indicadores e atributos de campanha** (webAnalyticsSendMetrics) | Conectores de análise da Web | Esse fluxo de trabalho permite enviar indicadores de campanha de email do Adobe Campaign para o Adobe Experience Cloud Suite por meio do conector do Adobe® Analytics. Os indicadores relacionados são: Enviado (iSent), Contagem total de aberturas (iTotalRecipientOpen), Número total de destinatários que clicaram (iTotalRecipientClick), Erros (iError), Recusa (opt-out) (iOptOut). |
| **Estoque: pedidos e alertas** (stockMgt) | Campanhas de marketing (Campaign) | Esse fluxo de trabalho inicia o cálculo de estoque nas linhas de pedido e gerencia os limites de aviso. |
| **Sincronização de fãs do Facebook** (syncFacebookFans) | Redes sociais (Marketing social)  - somente Campaign v7 | Esse fluxo de trabalho importa os fãs do Facebook para o Adobe Campaign todos os dias às 7h. |
| **Sincronização de páginas do Facebook** (syncFacebook) | Redes sociais (Marketing social)  - somente Campaign v7 | Esse fluxo de trabalho sincroniza páginas do Facebook com o Adobe Campaign todos os dias às 7h. |
| **Sincronização de páginas do Twitter** (syncTwitter) | Redes sociais (Marketing social)  - somente Campaign v7 | Esse fluxo de trabalho importa seguidores do Twitter para o Adobe Campaign todos os dias às 7h. |
| **Notificação de tarefa** (taskMgt) | Recursos de marketing (MRM)  - somente Campaign v7 | Esse fluxo de trabalho permite enviar mensagens de notificação relacionadas às tarefas em campanhas de marketing. |
| **Rastreamento** (tracking)) | Delivery | Esse workflow realiza a recuperação e a consolidação de informações de rastreamento. Também garante o recálculo de rastreamento e estatísticas de delivery, principalmente aqueles usados pelos workflows de arquivamento do Centro de Mensagens. Por padrão, é acionado uma vez por hora. |
| **Atualizar status do evento** (updateEventsStatus) | Execução de mensagens transacionais (Centro de Mensagens - Execução) | Esse fluxo de trabalho permite atribuir um status a um evento. Os status do evento são descritos a seguir:<ul><li>Pendente: o evento está em uma fila. Nenhum modelo de mensagem foi associado a ele.</li><li>Delivery pendente: o evento está em uma fila, um modelo de mensagem foi associado a ele e está sendo processado no momento pelo delivery.</li><li>Enviado: esse status é copiado dos logs do delivery. Significa que o delivery foi enviado.</li><li>Ignorado pelo delivery: esse status é copiado dos logs do delivery. Significa que o delivery foi ignorado.</li><li>Erro de delivery: esse status é copiado dos logs do delivery. Significa que o delivery falhou.</li><li>Evento não coberto: o evento falhou ao ser associado a um modelo de mensagem. O evento não será reprocessado.</li></ul> |
| **Atualizar para capacidade de entrega** (deliverabilityUpdate) | Delivery | Esse fluxo de trabalho é executado à noite e gerencia as regras de qualificação de emails rejeitados, bem como a lista de domínios e MXs. Isso requer que a porta HTTPS esteja aberta na plataforma. |