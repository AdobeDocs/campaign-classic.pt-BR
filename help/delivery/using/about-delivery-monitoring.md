---
product: campaign
title: Introdução ao monitoramento de entrega
description: Saiba mais sobre os recursos de monitoramento de entrega do Campaign Classic
feature: Monitoring, Deliverability
role: User
exl-id: 9ce11da0-e37b-459e-8ec7-d2bddf59bdf7
source-git-commit: 62ab16b206563aa25b8943e606d03a3184eb00db
workflow-type: ht
source-wordcount: '814'
ht-degree: 100%

---

# Introdução ao monitoramento de entrega {#about-delivery-monitoring}

>[!IMPORTANT]
>
>Esta página documenta os **recursos de monitoramento específicos do Campaign Classic v7** para implantações híbridas e locais.

## Recursos de monitoramento

### Monitoramento de entrega {#monitoring-deliveries}

**Para implantações híbridas/locais do Campaign Classic v7**, monitoramento adicional é necessário para os recursos do servidor e a configuração do MTA (Agente de Transferência de Correspondência).

#### Solução de problemas de entregas pendentes {#pending-deliveries}

E se as entregas não estiverem sendo enviadas e seu status permanecer **Pendente**?

* O processo de execução está aguardando a disponibilidade de alguns recursos. O MTA pode não ter sido iniciado.
Verifique se os módulos mta@instance estão abertos nos servidores MTA e, caso necessário, inicie o módulo MTA. [Saiba mais](../../production/using/administration.md).

* Pode ser que a entrega esteja usando uma afinidade não configurada na instância de envio.
Dica: verifique a configuração do gerenciamento de tráfego (afinidade IP). Para obter mais informações, consulte Controlar tráfego SMTP de saída.

>[!NOTE]
>
>Essas etapas só podem ser realizadas por um usuário especialista em instalações locais.

### Monitoramento da capacidade de entrega {#deliverability-monitoring}

#### Instalação do pacote de capacidade de entrega {#deliverability-package}

Esse recurso está disponível por meio de um pacote dedicado no Adobe Campaign. Para usá-lo, esse pacote deve ser instalado. Depois de concluído, reinicie o servidor para que o pacote seja considerado.

* Para clientes hospedados e híbridos, a opção **Deliverability monitoring** é configurada em sua instância pelo suporte técnico e consultores da Adobe. Para obter mais informações, entre em contato com o executivo da sua conta Adobe.

* Para instalações no local, você deve instalar o pacote **[!UICONTROL Deliverability monitoring (Email Deliverability)]** por meio do menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**. Para obter mais informações, consulte [Instalar pacotes padrão do Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).

#### Fluxo de trabalho de capacidade de entrega {#deliverability-workflow}

No Adobe Campaign Classic, o **Monitoramento da capacidade de entrega** é gerenciado pelo fluxo de trabalho **[!UICONTROL Refresh for deliverability]**. Ele é instalado por padrão em todas as instâncias e permite inicializar a lista de regras de qualificação de email de devolução, a lista de domínios e a lista de MXs. Quando o pacote **[!UICONTROL Deliverability monitoring (Email Deliverability)]** estiver instalado, esse fluxo de trabalho será executado durante a noite para atualizar regularmente a lista de regras e permitir que você gerencie ativamente a capacidade de entrega da plataforma.

**O pacote de capacidade de entrega oferece acesso a:**

* [Relatórios de renderização da Caixa de entrada](inbox-rendering.md), que permitem que você pré-visualize as mensagens nos principais clientes de email para verificar o conteúdo e a reputação.
* Visão geral da qualidade da mensagem (caixa de entrada, spam).

#### Ferramentas de monitoramento {#monitoring-tools}

**Para instalações locais**, use as seguintes ferramentas de monitoramento:

* O relatório **[!UICONTROL Delivery throughput]** fornece uma visão geral de todo o rendimento da plataforma em um determinado período. Para obter mais informações, consulte [esta seção](../../reporting/using/global-reports.md#delivery-throughput).
* Cada entrega gera um relatório de estatísticas de transmissão para os diferentes provedores de serviço da Internet (ISPs). Ele mostra algumas métricas de qualidade e reputação dos dados que podem afetar a capacidade de entrega, incluindo os seguintes números:
   * **[!UICONTROL Hard bounces]** indica a qualidade dos dados. Esse número deve ser inferior a 2%.
   * **[!UICONTROL Soft bounces]** indica a reputação. Este número não deve ser superior a 10% para qualquer ISP.

  Para obter mais informações, consulte a seção [Estatísticas da entrega](../../reporting/using/global-reports.md#delivery-statistics).

#### Diretrizes de monitoramento {#monitoring-guidelines}

**Para instalações locais**, estas são algumas diretrizes adicionais sobre o monitoramento da capacidade de entrega:

* Verifique regularmente a [taxa de transferência da entrega](../../reporting/using/global-reports.md#delivery-throughput) de toda a plataforma para verificar se ela é consistente com a configuração original.
* Verifique se as [tentativas](delivery-failures-quarantine.md#retries-after-a-delivery-temporary-failure) estão configuradas corretamente (30 minutos para o período de nova tentativa e mais de 20 tentativas) nos modelos da entrega.
* Verifique regularmente se a caixa de [rejeição](delivery-failures-quarantine.md#bounce-mail-management) está acessível e se a conta não está prestes a expirar.
* Verifique a taxa de transferência de cada delivery, que pode ser acessada no [painel de delivery](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}, para garantir que ela seja consistente com a validade do conteúdo do delivery (por exemplo, &quot;vendas rápidas&quot; devem ser entregues em minutos, não em dias).
* Ao usar ondas, verifique se cada uma tem tempo suficiente para terminar antes que a próxima seja acionada.
* Verifique se o número de erros e as novas [quarentenas](delivery-failures-quarantine.md) estão consistentes com outras entregas.
* Consulte detalhadamente os [logs da entrega](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/monitor/delivery-dashboard#delivery-logs-and-history){target="_blank"} para verificar o tipo de erro destacado (lista de bloqueios, problemas de DNS, regras anti-spam, etc.).

### Solução de problemas {#delivery-troubleshooting}

Ações específicas podem ser realizadas ao encontrar problemas nas entregas em **implantações híbridas/locais**:

* [Problemas na capacidade de entrega](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Problemas de exibição de imagem](../../production/using/image-display-issues.md)
* [Problemas de desempenho da entrega](delivery-performance-troubleshooting.md)
* [Problemas com arquivos temporários](../../production/using/temporary-files.md) – *somente clientes locais*

## Monitore entregas

Os seguintes recursos ajudarão a monitorar e rastrear o desempenho de entrega no Campaign Classic v7:

### Acessar o painel de entrega

Saiba como acessar as listas de entrega e usar o painel de entrega para monitorar a atividade de envio:

* [Monitorar entregas na interface do Campaign](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (Documentação do Campaign v8 - aplica-se tanto à v7 quanto à v8)
* [Status de entrega](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (documentação do Campaign v8)
* [Avançado: personalizar logs de entrega](customize-delivery-logs.md) (v7 híbrido/somente local – extensão de schema)

### Rastrear interações em mensagens

Rastrear aberturas, cliques e interações do destinatário com entregas:

* [Documentação de rastreamento de mensagens](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"} (documentação do Campaign v8 - aplica-se tanto à v7 quanto à v8)
* [Configurar links rastreados](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"} (documentação do Campaign v8)
* [Acessar logs de rastreamento](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"} (documentação do Campaign v8)

### Otimizar o desempenho de entrega

Práticas recomendadas e solução de problemas de desempenho de entrega:

* [Práticas recomendadas de entrega](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (documentação do Campaign v8 - aplica-se tanto à v7 quanto à v8)
* [Solução de problemas e desempenho de entrega](delivery-performance-troubleshooting.md) (configurações específicas da v7 híbrida/local)

### Saiba mais sobre falhas e quarentenas

Gerenciar falhas em entregas, emails rejeitados e endereços em quarentena:

* [Noções básicas sobre falhas de entrega](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (documentação do Campaign v8 - guia abrangente para v7 e v8)
* [Gerenciamento de quarentena](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (documentação do Campaign v8 - guia abrangente para v7 e v8)
* [Configurações de quarentena e falhas de entrega](delivery-failures-quarantine.md) (configurações específicas da v7 hibrida/local)
