---
product: campaign
title: Monitoramento da capacidade de entrega do Adobe Campaign Classic
description: Saiba mais sobre as ferramentas e as diretrizes sobre o monitoramento da capacidade de entrega no Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 100%

---

# Monitoramento da capacidade de entrega{#monitoring-deliverability}

![](../../assets/common.svg)

Abaixo você encontrará detalhes sobre as diferentes ferramentas de monitoramento fornecidas pelo Adobe Campaign, bem como algumas diretrizes adicionais sobre como aproveitar os recursos oferecidos pelo Adobe Campaign para monitorar a capacidade de entrega de sua plataforma.

## Monitoramento da capacidade de entrega {#configuration}

Esse recurso está disponível por meio de um pacote dedicado no Adobe Campaign. Para usá-lo, esse pacote deve ser instalado. Depois de concluído, reinicie o servidor para que o pacote seja considerado.
* Para clientes hospedados e híbridos, a opção **Deliverability monitoring** é configurada em sua instância pelo suporte técnico e consultores da Adobe. Para obter mais informações, entre em contato com o executivo da sua conta Adobe.

* Para instalações no local, você deve instalar o pacote **[!UICONTROL Deliverability monitoring (Email Deliverability)]** por meio do menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**. Para obter mais informações, consulte [Instalação de pacotes padrão do Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).

No Adobe Campaign Classic, o **Monitoramento da capacidade de entrega** é gerenciado pelo workflow **[!UICONTROL Refresh for deliverability]**. Ele é instalado por padrão em todas as instâncias e permite inicializar a lista de regras de qualificação de email de devolução, a lista de domínios e a lista de MXs. Quando o pacote **[!UICONTROL Deliverability monitoring (Email Deliverability)]** estiver instalado, esse workflow será executado durante a noite para atualizar regularmente a lista de regras e permitir que você gerencie ativamente a capacidade de entrega da plataforma.

O pacote de capacidade de delivery oferece acesso a:

* [Relatórios de renderização da Caixa de entrada](inbox-rendering.md), que permitem que você pré-visualize as mensagens nos principais clientes de email para verificar o conteúdo e a reputação.
* Visão geral da qualidade da mensagem (caixa de entrada, spam).

## Ferramentas de monitoramento {#monitoring-tools}

Você também pode usar as seguintes ferramentas:

* O relatório **[!UICONTROL Delivery throughput]** fornece uma visão geral de todo o rendimento da plataforma em um determinado período. Para obter mais informações, consulte [esta seção](../../reporting/using/global-reports.md#delivery-throughput).
* Cada delivery gera um relatório de estatísticas de transmissão para os diferentes provedores de serviço da Internet (ISPs). Ele mostra algumas métricas de qualidade e reputação dos dados que podem afetar a capacidade de entrega, incluindo os seguintes números:
   * **[!UICONTROL Hard bounces]** indica a qualidade dos dados. Esse número deve ser inferior a 2%.
   * **[!UICONTROL Soft bounces]** indica a reputação. Este número não deve ser superior a 10% para qualquer ISP.

   Para obter mais informações, consulte a seção [Estatísticas do delivery](../../reporting/using/global-reports.md#delivery-statistics).
* Em geral, o [painel de delivery](about-delivery-monitoring.md) oferece acesso:
   * ao [resumo de delivery](delivery-dashboard.md#delivery-summary), que mostra os detalhes do envio e o número de mensagens a enviar, processadas e enviadas com êxito;
   * aos [logs do delivery e o histórico](delivery-dashboard.md#delivery-logs-and-history), que mostram qual público-alvo foi excluído e o porquê;
   * aos [logs de rastreamento](delivery-dashboard.md#tracking-logs), que mostram informações de rastreamento, como aberturas e cliques.

## Diretrizes de monitoramento {#monitoring-guidelines}

Estas são algumas diretrizes adicionais sobre o monitoramento da capacidade de entrega:

* Verifique regularmente a [taxa de transferência do delivery](../../reporting/using/global-reports.md#delivery-throughput) de toda a plataforma para verificar se ela é consistente com a configuração original.
* Verifique se as [tentativas](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) estão configuradas corretamente (30 minutos para o período de nova tentativa e mais de 20 tentativas) nos templates do delivery.
* Verifique regularmente se a caixa de [rejeição](understanding-delivery-failures.md#bounce-mail-management) está acessível e se a conta não está prestes a expirar.
* Verifique a taxa de transferência de cada delivery, que pode ser acessada no [painel de delivery](delivery-dashboard.md), para garantir que ela seja consistente com a validade do conteúdo do delivery (por exemplo, &quot;vendas rápidas&quot; devem ser entregues em minutos, não em dias).
* Ao usar as [ondas](steps-sending-the-delivery.md#sending-using-multiple-waves), verifique se cada onda tem tempo suficiente para terminar antes que a próxima seja acionada.
* Verifique se o número de erros e as novas [quarentenas](understanding-quarantine-management.md) estão consistentes com outros deliveries.
* Consulte detalhadamente os [logs do delivery](delivery-dashboard.md#delivery-logs-and-history) para verificar o tipo de erro destacado (lista de bloqueios, problemas de DNS, regras anti-spam, etc.).

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
