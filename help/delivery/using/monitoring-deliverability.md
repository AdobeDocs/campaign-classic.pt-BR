---
title: Monitoramento da capacidade de entrega do Adobe Campaign Classic
description: Saiba mais sobre as ferramentas e as diretrizes sobre o monitoramento da capacidade de entrega no Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 0b5c5dbd-f532-4d8a-a255-9e6d88357d8d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 0baef937-f00b-4fc4-8608-a870997be684
translation-type: tm+mt
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 91%

---


# Monitoramento da capacidade de entrega{#monitoring-deliverability}

Abaixo, você encontrará detalhes sobre as diferentes ferramentas de monitoramento fornecidas pelo Adobe Campaign, bem como algumas diretrizes adicionais sobre o monitoramento da capacidade de entrega.

## Ferramentas de monitoramento {#monitoring-tools}

Use os recursos oferecidos pelo Adobe Campaign para monitorar a capacidade de entrega da sua plataforma.

O pacote de capacidade de entrega oferece acesso a:

* Relatórios de rastreamento técnico para o desempenho diário da capacidade de entrega (monitoramento técnico). Esse relatório, disponível sob demanda, permite que você receba um relatório diário por email em um endereço especificado. Para obter mais informações, entre em contato com a equipe de Atendimento ao cliente da Adobe.
* [Relatórios de renderização da Caixa de entrada](../../delivery/using/inbox-rendering.md), que permitem que você pré-visualize as mensagens nos principais clientes de email para verificar o conteúdo e a reputação.
* Visão geral da qualidade da mensagem (caixa de entrada, spam).

Você também pode usar as seguintes ferramentas:

* O relatório **[!UICONTROL Delivery throughput]** fornece uma visão geral de todo o rendimento da plataforma em um determinado período. Para obter mais informações, consulte [esta seção](../../reporting/using/global-reports.md#delivery-throughput).
* O relatório **[!UICONTROL Technical deliverability monitoring]** inclui vários indicadores de qualidade da capacidade de entrega para sua plataforma. Para obter mais informações, consulte [esta seção](#technical-deliverability-monitoring).
* Cada delivery gera um relatório de estatísticas de transmissão para os diferentes provedores de serviço da Internet (ISPs). Ele mostra algumas métricas de qualidade e reputação dos dados que podem afetar a capacidade de entrega, incluindo os seguintes números:
   * **[!UICONTROL Hard bounces]** indica a qualidade dos dados. Esse número deve ser inferior a 2%.
   * **[!UICONTROL Soft bounces]** indica a reputação. Este número não deve ser superior a 10% para qualquer ISP.

   Para obter mais informações, consulte a seção [Estatísticas do delivery](../../reporting/using/global-reports.md#delivery-statistics).
* Em geral, o [painel de delivery](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard) oferece acesso:
   * ao [resumo de delivery](../../delivery/using/monitoring-a-delivery.md#delivery-summary), que mostra os detalhes do envio e o [número de mensagens](../../delivery/using/monitoring-a-delivery.md#number-of-messages-sent) a enviar, processadas e enviadas com êxito;
   * aos [logs do delivery e o histórico](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history), que mostram qual público-alvo foi excluído e o porquê;
   * aos [logs de rastreamento](../../delivery/using/monitoring-a-delivery.md#tracking-logs), que mostram informações de rastreamento, como aberturas e cliques.

## Orientações de monitoramento {#monitoring-guidelines}

Estas são algumas diretrizes adicionais sobre o monitoramento da capacidade de entrega:

* Verifique regularmente a [taxa de transferência do delivery](../../reporting/using/global-reports.md#delivery-throughput) de toda a plataforma para verificar se ela é consistente com a configuração original.
* Verifique se as [tentativas](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) estão configuradas corretamente (30 minutos para o período de nova tentativa e mais de 20 tentativas) nos templates do delivery.
* Verifique regularmente se a caixa de [rejeição](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management) está acessível e se a conta não está prestes a expirar.
* Verifique a taxa de transferência de cada delivery para garantir que ela seja consistente com a validade do conteúdo do delivery (por exemplo, &quot;vendas rápidas&quot; devem ser entregues em minutos, não em dias).
* Ao usar as [ondas](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves), verifique se cada onda tem tempo suficiente para terminar antes que a próxima seja acionada.
* Verifique se o número de erros e as novas [quarentenas](../../delivery/using/understanding-quarantine-management.md) estão consistentes com outros deliveries.
* Carefully consult the [delivery logs](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history) in detail to check the kind of errors that are highlighted (denylists, DNS issues, anti-spam rules, etc.).

## Signal Spam {#signal-spam}

O Signal Spam é um serviço francês que oferece relatórios de ciclo de feedback anônimo para ISPs franceses (Orange, SFR).

* Esse serviço permite que você acompanhe a reputação dos ISPs franceses e rastreie a evolução da atividade dos clientes.

* O Signal Spam também fornece reclamações diretas que os usuários finais registram por meio de uma interface dedicada. Essas reclamações são colocadas em quarentena a partir do banco de dados de endereços de email.

## 250ok {#deliverability-250ok}

[O 250ok](https://250ok.com/) é uma solução de monitoramento complementar das ferramentas internas de entregabilidade do Adobe, que fornece  de IP e domínio e indicadores de reputação.

As informações fornecidas são em tempo real, o que permite uma assistência proativa.

## Relatório de monitoramento técnico da capacidade de entrega {#technical-deliverability-monitoring}

O relatório técnico de monitoramento da capacidade de entrega é atualizado diariamente e está disponível ao navegar até **[!UICONTROL Monitoring]** > **[!UICONTROL Overview]** e clicar no link **[!UICONTROL Technical monitoring]** da guia **[!UICONTROL Home]** do Adobe Campaign. Ele inclui vários indicadores de qualidade de deliverability para sua plataforma.

Esses indicadores são atualizados diariamente às 9h.

>[!NOTE]
>
>Além disso, você pode receber um relatório diário por email em um endereço especificado. Informe o endereço de email solicitado por email ou pelo Adobe Campaign Extranet.

![](assets/s_tn_del_monitoring.png)

Os seguintes indicadores são usados no relatório:

* **[!UICONTROL Reverse DNS]** : O Adobe Campaign verifica se um DNS reverso é fornecido para um endereço IP e se ele é apontado corretamente ao IP.

* **[!UICONTROL SPF]** (Estrutura de Política do Remetente): um mecanismo de autenticação que permite aos ISPs e provedores de caixa de correio verificar se o remetente de email está autorizado no domínio de envio.

* **[!UICONTROL DomainKeys]**: um serviço desenvolvido pelo Yahoo que verifica a identidade de um remetente de email.

* **[!UICONTROL IP and RBL domain]** (Lista em tempo real Blackhole): Uma lista de endereços IP e domínios que foram sinalizados por organizações de  lista de bloqueios por má reputação de envio. Essas listas são mantidas por organizações dedicadas como Spamhaus, Spamcop, SURBL/URIBL, etc. Atualmente, o Adobe Campaign processa verificações contra RBLs que têm um impacto significativo no delivery. Essas RBLs refletem sua reputação e podem ser consultadas pelos ISPs antes de aceitarem seus emails.

* **[!UICONTROL SNDS]** (Serviços de dados de rede inteligente): um [serviço anti-spam do Windows Live Hotmail](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx). O Hotmail é o único ISP que fornece esse tipo de informação. As pontuações de referência são um resultado de filtro verde, uma taxa de reclamação inferior a 0,1% e zero armadilhas de spam.

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
