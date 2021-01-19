---
solution: Campaign Classic
product: campaign
title: 'Fluxos de trabalho técnicos '
description: Saiba mais sobre os workflows técnicos disponíveis com os pacotes Campaign Classic.
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: f57f52d8807eb771e2416b6648e1d746a206fa96
workflow-type: tm+mt
source-wordcount: '1816'
ht-degree: 70%

---


# Fluxos de trabalho técnicos{#about-technical-workflows}

## Sobre workflows técnicos {#overview}

Os workflows detalhados nesta seção são instalados com os diferentes pacotes integrados do Adobe Campaign. Esses pacotes e os workflows técnicos relacionados dependem do contrato de licença. Os pacotes incorporados estão detalhados em [esta seção](../../installation/using/installing-campaign-standard-packages.md).

Por padrão, os workflows técnicos estão disponíveis em uma subpasta do seguinte nó: **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

>[!NOTE]
>
>Os workflows técnicos relacionados ao módulo do Centro de Mensagens estão disponíveis por padrão no nó **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Message Center]** > **[!UICONTROL Technical workflows]**.

Para obter mais informações sobre como monitorar workflows técnicos, consulte a [seção dedicada](../../workflow/using/monitoring-technical-workflows.md).

## Lista de fluxos de trabalho técnicos {#list-technical-workflows}

| Fluxo de trabalho técnico | Embalagem | Descrição |
|------|--------|-----------|
| **Limpeza**  de alias (aliasCleansing) | Delivery | Esse workflow padroniza os valores de enumeração. É acionado todos os dias às 3:00 AM por padrão. |
| **Faturamento**  (faturamento) | Delivery | Esse workflow envia o relatório de atividades do sistema para o operador &#39;faturamento&#39; por email. É disparado todo dia 25 de cada mês por padrão. |
| **Cálculo de estatísticas**  do Twitter (statsTwitter) | Redes sociais (Marketing social) | Esse workflow calcula estatísticas vinculadas a retweets e visitas no Twitter. |
| **Tarefas**  de campanha (operationMgt) | Campanhas de marketing (Campanha) | Esse workflow gerencia as tarefas para campanhas de marketing (inicia o target, extrai arquivos etc.). Ele também cria workflows relacionados a campanhas recorrentes e periódicas. |
| **Coletar dados para o serviço**  HeatMap (collectDataHeatMapService) | Instalado por padrão | Esse fluxo de trabalho recupera dados exigidos pelo serviço HeatMap. |
| **Coletar solicitações**  de privacidade (collectPrivacyRequests) | Regulamento de Proteção de Dados de Privacidade | Esse workflow gera os dados do recipient armazenados no Adobe Campaign e o disponibiliza para download na tela da solicitação de privacidade. |
| **Cálculo**  de custo (budgetMgt) | Campanhas de marketing (Campanha) | Esse workflow inicia o cálculo das linhas de despesas e custos nos orçamentos, planos, programas, campanhas, deliveries e tarefas. |
| **Limpeza**  do banco de dados (limpeza) | Delivery | Este workflow é o workflow de manutenção do banco de dados: faz diferentes cálculos das estatísticas e dos processos e exclui dados obsoletos do banco de dados de acordo com a configuração definida no assistente de implantação. É acionado todos os dias às 4:00 AM por padrão. Para saber mais, consulte [esta página](../../production/using/database-cleanup-workflow.md#monitoring-campaign-classic). |
| **Excluir usuários**  bloqueados da LINHA (deleteBlockedLineUsersV2) | Canal LINE | Esse workflow garante que os dados dos usuários LINE V2 sejam excluídos após bloquearem a conta oficial LINE por 180 dias. |
| **Excluir dados**  de solicitações de privacidade (deletePrivacyRequestsData) | Regulamento de Proteção de Dados de Privacidade | Esse workflow exclui os dados do recipient armazenados no Adobe Campaign. |
| **Indicadores**  de delivery (indicadores de entrega) | Plataforma Mid-sourcing | Esse workflow atualiza os indicadores de rastreamento de delivery para um delivery. Esse workflow é acionado a cada hora por padrão. |
| **Processos**  do fórum de discussão (newsgroupMgt) | Recursos de marketing (MRM) | Este workflow gerencia o delivery de notificações dos fóruns de discussão. É acionado ao receber um sinal de aprovação |
| **Processos**  de marketing distribuídos (centralLocalMgt) | Marketing Central/local (Marketing distribuído) | Esse workflow executa processos vinculados ao uso do módulo de marketing distribuído. Ele inicia a criação de campanha local e gerencia notificações vinculadas a pedidos e à disponibilidade do pacote de campanha. |
| **Expurgação**  do evento (webAnalyticsPurgeWebEvents) | Conectores do Web Analytics | Esse fluxo de trabalho permite que você exclua cada evento do campo do banco de dados de acordo com o período configurado no campo Duração. |
| **Exportar audiências para o Adobe Experience Cloud**  (exportSharedAudience) | Integração com a Adobe Experience Cloud | Esse workflow exporta audiences como audiences/segmentos compartilhados. Esses audiences podem ser usados nas diferentes soluções da Adobe Experience Cloud que você usa. |
| **Previsão** (previsão) | Delivery | Este workflow analisa os deliveries salvos no calendário provisional (cria logs provisionais). É acionado todos os dias às 1:00 AM por padrão. |
| **Cálculo de agregação completa (cubo propositionrcp)** (agg_nmspropositionrcp_full) | motor de oferta (interação) | Esse workflow atualiza o agregado completo do cubo da Apresentação da oferta. É acionado todos os dias às 6:00 AM por padrão. Esse agregado captura as seguintes dimensões: canal, delivery, oferta de marketing e data. O cubo da Apresentação de oferta é usado para gerar relatórios com base em ofertas. Você pode saber mais sobre cubos [nesta seção](../../reporting/using/about-cubes.md). |
| **Identificação de contatos**  convertidos (webAnalyticsFindConverted) | Conectores do Web Analytics | Este workflow indexa os visitantes do site que concluíram sua compra após uma campanha de re-marketing. Os dados recuperados por esse fluxo de trabalho podem ser acessados no relatório de eficiência de remarketing (consulte esta página). |
| **Importar audiências do Adobe Experience Cloud** (importSharedAudience) | Integração com a Adobe Experience Cloud | Esse workflow permite importar audiences/segmentos de diferentes soluções da Adobe Experience Cloud para o Adobe Campaign. |
| **Trabalhos em delivery no campanha** (deliveryMgt) | Campanhas de marketing (Campanha) | Esse workflow aciona os deliveries aprovados e inicia o pós-processamento no provedor de serviços para um delivery externo. Também envia notificações e lembretes de aprovação. |
| **Ordens de produção em provedores de serviço** (vendorMgt) | Campanhas de marketing (Campanha) | Esse workflow inicia processos do provedor de serviços (email para o roteador e o pós-processamento) após a aprovação de deliveries. |
| **Atualização**  do token de acesso LINE V2 (updateLineV2AccessToken) | Canal LINE | Este workflow atualiza o token de acesso para LINE V2. |
| **Migração**  de MID para LineUserID (MIDToUserIDMigration) | Canal LINE | Esse workflow gera a ID de usuários LINE V2 para migração de LINE V1 para LINE V2. |
| **Notificações**  de recurso de marketing (assetMgt) | Recursos de marketing (MRM) | Esse workflow gerencia notificações vinculadas à aprovação e à publicação de recursos de marketing. |
| **Centro de mensagens  &lt;external_account_name>** (mcSynch_&lt;external_account_name>) | Controle de mensagens transacionais (Centro de mensagens - Controle) | Esse workflow: <ul><li>recupera a lista de eventos processados pela(s) operação(s).</li><li>sincroniza com a tabela NmsBroadLogMsg para recuperar as qualificações da mensagem de delivery.</li><li>recupera logs de delivery de eventos assim que a sincronização com a tabela NmsBroadLogMsg for concluída.</li><li>sincroniza com a tabela NmsTrackingUrl para recuperar o rastreamento para as URLs de delivery.</li><li>recupera as URLs de rastreamento de eventos assim que a sincronização com a tabela NmsTrackingUrl for concluída.</li><li>permite recuperar todos os endereços de email colocados em quarentena a cada três horas após o envio de um delivery.</li></ul> |
| **Cálculo**  da agregação completa do MessageCenter (agg_messageCenter_full) | Controle de mensagens transacionais (Centro de mensagens - Controle) | Esse fluxo de trabalho atualiza a agregação completa do cubo do centro de mensagens. É acionado todos os dias às 3:00 AM por padrão. Esse agregado captura as seguintes dimensões: canal, data, status e tipo de evento. O cubo do centro de mensagens é então usado para gerar relatórios com base em eventos. Você pode saber mais sobre cubos em [esta seção](../../reporting/using/about-cubes.md) |
| **Mid-sourcing (contadores de delivery)** (defaultMidSourcingDlv) | Transferência para mid-sourcing | Este workflow coleta informações de contagem para deliveries no servidor mid-sourcing. Informações de contagem incluem indicadores de deliveries gerais, como número de deliveries enviados, etc. As informações de rastreamento, como aberturas, não são incluídas. É acionado a cada dez minutos por padrão. |
| **Mid-sourcing (logs do delivery)** (defaultMidSourcingLog) | Transferência para mid-sourcing | Esse workflow coleta logs de delivery no servidor mid-sourcing. É acionado a cada hora por padrão. |
| **Gerenciamento**  de não participação NMAC (mobileAppOptOutMgt) | Canal de aplicativo móvel | Esse workflow atualiza a notificação de unsubscriptions em dispositivos móveis. É acionado a cada 6 horas entre 1:00 AM e meia-noite. Para obter mais detalhes, consulte [esta seção](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines). |
| **Número de perfis**  de faturamento ativos (billingActiveContactCount) | Delivery | Esse workflow conta o número de perfis ativos. É acionado todas as noites às 1:00 AM por padrão. “Perfil” significa um registro de informações (por exemplo: um registro na tabela nmsRecipient ou uma tabela externa contendo um cookie de identificação, uma identificação do cliente, um identificador para dispositivos móveis ou outras informações relevantes para um canal específico) representando um cliente final, um prospecto ou um cliente potencial. Faturamento só afeta Perfis que estão &quot;ativos&quot;. Um Perfil é considerado &quot;ativo&quot; quando ele for alvo ou recebe comunicação nos últimos 12 meses por meio de qualquer canal. Os canais Facebook e Twitter não são considerados. É possível ter uma visão geral do Number of active profiles no menu Administration > Campaign Management > Customer metrics. |
| **Notificação**  de oferta (offerMgt) | Delivery | Esse workflow implanta ofertas aprovadas no ambiente online, bem como todas as categorias contidas no catálogo de oferta. |
| **Limpeza**  de workflows pausados (cleanupPausedWorkflows) | Delivery | Esse workflow analisa workflows pausados que têm a severidade definida como normal e emite avisos e notificações quando ficam pausados por muito tempo. Após um mês, os workflows técnicos pausados são interrompidos definitivamente. Por padrão, é acionado toda segunda-feira às 5:00 AM. Para obter mais informações, consulte [Manuseio de workflows pausados](../../workflow/using/monitoring-workflow-execution.md#handling-of-paused-workflows). |
| **Limpeza**  da solicitação de privacidade (cleanupPrivacyRequests) | Regulamento de Proteção de Dados de Privacidade | Esse workflow apaga os arquivos de solicitação de acesso criados há mais de 90 dias. |
| **Processando eventos batch** (batchEventsProcessing) | Execução de mensagens transacionais (Centro de Mensagens - Execução) | Esse workflow permite colocar eventos batch em uma fila antes de associá-los a um template de mensagem. |
| **Processando eventos em tempo real** (rtEventsProcessing) | Execução de mensagens transacionais (Centro de Mensagens - Execução) | Esse workflow permite colocar eventos em tempo real em uma fila antes de associá-los a um template de mensagem. |
| **Sincronização**  da proposta (propositionSynch) | Controlo do motor de oferta com instância de execução | Esse workflow sincroniza as apresentações entre a instância de marketing e a instância de execução usada para interações. |
| **Recuperação de eventos**  da Web (webAnalyticsGetWebEvents) | Conectores do Web Analytics | A cada hora, este workflow baixa segmentos do comportamento do usuário na Internet em um determinado site, os coloca no banco de dados do Adobe Campaign e inicia o workflow de re-marketing. |
| **Agregações**  do relatórios (reportAggregates) | Delivery | Este workflow atualiza agregados usados em relatórios. É acionado todos os dias às 2:00 AM por padrão. |
| **Envio de indicadores e atributos**  de campanha (webAnalyticsSendMetrics) | Conectores do Web Analytics | Esse workflow permite enviar indicadores de campanha de email do Adobe Campaign para o Adobe Experience Cloud Suite por meio do conector do Adobe® Genesis. Os indicadores em causa são os seguintes: Enviado (Enviado), Contagem total de aberturas (iTotalRecipientOpen), Número total de recipient que clicaram (iTotalRecipientClick), Erros (iError), Recusa (recusa) (iOptOut). |
| **Stock: Pedidos e alertas** (stockMgt) | Campanhas de marketing (Campanha) | Este workflow inicia o cálculo de estoque nas linhas de pedido e gerencia os limites de aviso. |
| **Sincronizando fãs**  do Facebook (syncFacebookFans) | Redes sociais (Marketing social) | Esse workflow importa os fãs do Facebook para o Adobe Campaign todos os dias às 7:00 AM. |
| **Sincronizar páginas**  do Facebook (syncFacebook) | Redes sociais (Marketing social) | Esse workflow sincroniza páginas do Facebook com o Adobe Campaign todos os dias às 7:00 AM. |
| **Sincronizar páginas**  do Twitter (syncTwitter) | Redes sociais (Marketing social) | Esse workflow importa seguidores do Twitter para o Adobe Campaign todos os dias às 7:00 AM. |
| **Notificação**  de tarefa (taskMgt) | Recursos de marketing (MRM) | Esse workflow permite enviar mensagens de notificação relacionadas às tarefas em campanhas de marketing. |
| **Rastreamento** (rastreamento) | Delivery | Esse workflow realiza a recuperação e a consolidação de informações de rastreamento. Também garante o recálculo de rastreamento e estatísticas de delivery, principalmente aqueles usados pelos workflows de arquivamento do Centro de Mensagens. Por padrão, é acionado uma vez por hora. |
| **Atualizar status**  do evento (updateEventsStatus) | Execução de mensagens transacionais (Centro de Mensagens - Execução) | Esse workflow permite atribuir um status a um evento. Os status do evento são como descritos a seguir:<ul><li>Pendente: o evento está em uma fila. Nenhum template de mensagem foi associado a ele.</li><li>Delivery pendente: o evento está em uma fila, um template de mensagem foi associado a ele e está sendo processado no momento pelo delivery.</li><li>Enviado: esse status é copiado dos logs de delivery. Significa que o delivery foi enviado.</li><li>Ignorado pelo delivery: esse status é copiado dos logs de delivery. Significa que o delivery foi ignorado.</li><li>Erro de delivery: esse status é copiado dos logs de delivery. Significa que o delivery falhou.</li><li>Evento não coberto: o evento falhou ao ser associado a um template de mensagem. O evento não será reprocessado.</li></ul> |
| **Atualização para o material de entrega** (material de entregaUpdate) | Delivery | Depois que o pacote de monitoramento de entregabilidade (Entrega por email) é instalado, esse fluxo de trabalho é executado noturna e gerencia as regras de qualificação de e-mails de rejeição, bem como a lista de domínios e MXs. Isso requer que a porta HTTPS seja aberta na plataforma |
| **Atualizar rede semente para Renderização**  da Caixa de Entrada (updateRenderingSeeds) | Renderização da caixa de entrada (IR) | Esse fluxo de trabalho atualiza endereços de email usados para renderização da Caixa de entrada e só funciona se a porta HTTPS estiver aberta para entrega.neolane.net. |
