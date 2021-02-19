---
solution: Campaign Classic
product: campaign
title: Monitoramento da capacidade de entrega do Adobe Campaign Classic
description: Saiba mais sobre as ferramentas e as diretrizes sobre o monitoramento da capacidade de entrega no Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 11377b0218e20da9b1a5398539ebaa192801b283
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 100%

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
* Em geral, o [painel de delivery](../../delivery/using/about-delivery-monitoring.md) oferece acesso:
   * ao [resumo de delivery](../../delivery/using/delivery-dashboard.md#delivery-summary), que mostra os detalhes do envio e o número de mensagens a enviar, processadas e enviadas com êxito;
   * aos [logs do delivery e o histórico](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history), que mostram qual público-alvo foi excluído e o porquê;
   * aos [logs de rastreamento](../../delivery/using/delivery-dashboard.md#tracking-logs), que mostram informações de rastreamento, como aberturas e cliques.

## Orientações de monitoramento {#monitoring-guidelines}

Estas são algumas diretrizes adicionais sobre o monitoramento da capacidade de entrega:

* Verifique regularmente a [taxa de transferência do delivery](../../reporting/using/global-reports.md#delivery-throughput) de toda a plataforma para verificar se ela é consistente com a configuração original.
* Verifique se as [tentativas](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) estão configuradas corretamente (30 minutos para o período de nova tentativa e mais de 20 tentativas) nos templates do delivery.
* Verifique regularmente se a caixa de [rejeição](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management) está acessível e se a conta não está prestes a expirar.
* Verifique a taxa de transferência de cada delivery para garantir que ela seja consistente com a validade do conteúdo do delivery (por exemplo, &quot;vendas rápidas&quot; devem ser entregues em minutos, não em dias).
* Ao usar as [ondas](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves), verifique se cada onda tem tempo suficiente para terminar antes que a próxima seja acionada.
* Verifique se o número de erros e as novas [quarentenas](../../delivery/using/understanding-quarantine-management.md) estão consistentes com outros deliveries.
* Consulte detalhadamente os [logs do delivery](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) para verificar o tipo de erro destacado (lista de bloqueios, problemas de DNS, regras anti-spam, etc.).

## Signal Spam {#signal-spam}

O Signal Spam é um serviço francês que oferece relatórios de ciclo de feedback anônimo para ISPs franceses (Orange, SFR).

* Esse serviço permite que você acompanhe a reputação dos ISPs franceses e rastreie a evolução da atividade dos clientes.

* O Signal Spam também fornece reclamações diretas que os usuários finais registram por meio de uma interface dedicada. Essas reclamações são colocadas em quarentena a partir do banco de dados de endereços de email.

## 250ok {#deliverability-250ok}

A [250ok](https://250ok.com/) é uma solução de monitoramento complementar das ferramentas internas de delivery da Adobe, que fornece lista de bloqueios de IP e de domínios e indicadores de reputação.

As informações fornecidas são em tempo real, o que permite uma assistência proativa.

## Relatório de monitoramento técnico da capacidade de entrega {#technical-deliverability-monitoring}

O relatório de **Monitoramento técnico de qualidade de entrega** inclui vários indicadores de qualidade da capacidade de entrega para sua plataforma. Você pode receber esse relatório diário por email. Para solicitar, abra um [Caso de suporte](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) específico e detalhe as seguintes informações:

* o nome da instância
* os endereços de email para os quais enviar o relatório

Esses relatórios contêm os seguintes indicadores:

* **[!UICONTROL Reverse DNS]** : O Adobe Campaign verifica se um DNS reverso é fornecido para um endereço IP e se ele é apontado corretamente ao IP.

* **[!UICONTROL SPF]** (Estrutura de Política do Remetente): um mecanismo de autenticação que permite aos ISPs e provedores de caixa de correio verificar se o remetente de email está autorizado no domínio de envio.

* **[!UICONTROL DomainKeys]**: um serviço desenvolvido pelo Yahoo que verifica a identidade de um remetente de email.

* **[!UICONTROL IP and RBL domain]** (Lista de buracos negros em tempo real): uma lista de endereços IP e domínios que foram sinalizados por organizações de listas de bloqueios por má reputação de envios. Essas listas são mantidas por organizações dedicadas como Spamhaus, Spamcop, SURBL/URIBL, etc. Atualmente, o Adobe Campaign processa verificações contra RBLs que têm um impacto significativo no delivery. Essas RBLs refletem sua reputação e podem ser consultadas pelos ISPs antes de aceitarem seus emails.

* **[!UICONTROL SNDS]** (Serviços de dados de rede inteligente): um [serviço anti-spam do Windows Live Hotmail](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx). O Hotmail é o único ISP que fornece esse tipo de informação. As pontuações de referência são um resultado de filtro verde, uma taxa de reclamação inferior a 0,1% e zero armadilhas de spam.

Esses indicadores são atualizados diariamente às 9h.


<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
