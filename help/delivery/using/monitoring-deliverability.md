---
title: Monitoramento da entrega no Adobe Campaign Classic
description: Saiba mais sobre as ferramentas e as diretrizes sobre o monitoramento da capacidade de entrega no Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 0b5c5dbd-f532-4d8a-a255-9e6d88357d8d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 0baef937-f00b-4fc4-8608-a870997be684
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a30c4a2d31c3f674ac4a7bb4827a6951b36014ab
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 33%

---


# Monitoramento da capacidade de entrega{#monitoring-deliverability}

Abaixo, você encontrará detalhes sobre as diferentes ferramentas de monitoramento fornecidas pelo Adobe Campaign, bem como algumas diretrizes adicionais sobre o monitoramento da entrega.

## Monitoring tools {#monitoring-tools}

Use os recursos oferecidos pelo Adobe Campaign para monitorar a capacidade de entrega de sua plataforma.

O pacote de Disponibilidade oferece acesso a:

* Relatório de acompanhamento técnico para o desempenho diário da entrega (monitoramento técnico). Este relatório, disponível sob demanda, permite que você receba um relatório diário por email em um endereço especificado. Para obter mais informações, entre em contato com a equipe de Atendimento ao cliente da Adobe.
* O relatório [de renderização da](../../delivery/using/inbox-rendering.md) Caixa de entrada que permite que você pré-visualização suas mensagens nos principais clientes de email para verificar o conteúdo e a reputação.
* Visão geral da qualidade da mensagem (caixa de entrada, spam).

Você também pode usar as seguintes ferramentas:

* O **[!UICONTROL Delivery throughput]** relatório fornece uma visão geral de toda a throughput da plataforma em um determinado período. Para obter mais informações, consulte [esta seção](../../reporting/using/global-reports.md#delivery-throughput).
* The **[!UICONTROL Technical deliverability monitoring]** report includes a number of deliverability quality indicators for your platform. Para obter mais informações, consulte [esta seção](#technical-deliverability-monitoring).
* O painel [do](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard) delivery fornece acesso ao resumo [do](../../delivery/using/monitoring-a-delivery.md#delivery-summary)Delivery, aos [Logs do delivery e histórico](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history) e aos [Logs de rastreamento](../../delivery/using/monitoring-a-delivery.md#tracking-logs). Eles mostram os detalhes do envio, qual público alvo foi excluído e por que, bem como as informações de rastreamento, como abrir e clicar. <!--For more on this, see [Monitoring a delivery](../../delivery/using/monitoring-a-delivery.md).-->
* Você também pode verificar o número de mensagens a serem enviadas, processadas e enviadas com sucesso. Para obter mais informações, consulte [esta seção](../../delivery/using/monitoring-a-delivery.md#number-of-messages-sent)
   <!--[SpamAssassin](../../installation/using/configuring-spamassassin.md)?-->

## Orientações de acompanhamento {#monitoring-guidelines}

Estas são algumas diretrizes adicionais sobre o monitoramento de entrega:

* Verifique regularmente a taxa de transferência [do](../../reporting/using/global-reports.md#delivery-throughput) delivery para a plataforma inteira para verificar se ela é consistente com a configuração original.
* Verifique se o [tentativas](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) está configurado corretamente (30 minutos para o período de tentativas e mais de 20 tentativas) nos templates do delivery.
* Verifique regularmente se a caixa de correio de [rejeição](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management) está acessível e se a conta não está prestes a expirar.
* Verifique a throughput de cada delivery para verificar se ela é consistente com a validade do conteúdo do delivery (por exemplo, &quot;vendas em flash&quot; devem ser entregues em minutos, não em dias).
* Ao usar o [ondas](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves), verifique se cada onda tem tempo suficiente para terminar antes que a próxima seja acionada.
* Verifique se o número de erros e as novas [quarentenas](../../delivery/using/understanding-quarantine-management.md) estão consistentes com outros delivery.
* Consulte os [logs do delivery](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history) cuidadosamente detalhadamente para verificar o tipo de erros que são destacados (listas cinza ou preta, problemas de DNS, regras antisspam etc.).

## Spam de sinal {#signal-spam}

Signal Spam é um serviço francês que oferta relatórios de ciclo de feedback anônimo para ISPs franceses (Orange, SFR).

* Esse serviço permite que você acompanhe a reputação dos ISPs franceses e rastreie a evolução atividade dos clientes.

* O Signal Spam também fornece reclamações diretas que os usuários finais registram por meio de uma interface dedicada. Essas reclamações são colocadas em quarentena a partir do banco de dados de endereços de email.

## 250ok {#deliverability-250ok}

[O 250ok](https://250ok.com/) é uma solução de monitoramento complementar das ferramentas internas de entrega da Adobe, que fornece IP, lista negra de domínios e indicadores de reputação.

As informações fornecidas são em tempo real, o que permite uma assistência pró-ativa.

## Relatório de monitoramento técnico de deliverability {#technical-deliverability-monitoring}

The technical deliverability monitoring report is updated daily and available by navigating to **[!UICONTROL Monitoring]** > **[!UICONTROL Overview]** and clicking the **[!UICONTROL Technical monitoring]** link from the Adobe Campaign **[!UICONTROL Home]** tab. Ele inclui vários indicadores de qualidade de deliverability para sua plataforma.

Esses indicadores são atualizados diariamente às 9h.

>[!NOTE]
>
>Além disso, você pode receber um relatório diário por email em um endereço especificado. Informe-nos sobre o endereço de e-mail solicitado por e-mail ou pela Extranet do Adobe Campaign.

![](assets/s_tn_del_monitoring.png)

Os seguintes indicadores são usados no relatório:

* **[!UICONTROL Reverse DNS]** : O Adobe Campaign verifica se um DNS reverso é fornecido para um endereço IP e que isso seja apontado corretamente ao IP.

* **[!UICONTROL SPF]** (Estrutura de Política do Remetente): um mecanismo de autenticação que permite aos ISPs e provedores de caixa de correio verificar se o remetente de email está autorizado no domínio de envio.

* **[!UICONTROL DomainKeys]**: um serviço desenvolvido pelo Yahoo e destinado a certificar a identidade de um remetente de email.

* **[!UICONTROL IP and RBL domain]** (Lista de buracos negros em tempo real): uma lista de endereços IP e domínios que foram sinalizados por organizações de listas de bloqueios para má reputação de envio. Essas listas são mantidas por organizações dedicadas como Spamhaus, Spamcop, SURBL/URIBL, etc. Atualmente, o Adobe Campaign processa verificações contra RBLs que têm um impacto significativo no delivery. Essas RBLs refletem sua reputação e podem ser consultadas pelos ISPs antes de aceitarem seus emails.

* **[!UICONTROL SNDS]** (Serviços de dados de rede inteligente): um [serviço anti-spam do Windows Live Hotmail](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx). O Hotmail é o único ISP que fornece esse tipo de informação. As pontuações de referência são um resultado de filtro verde, uma taxa de reclamação inferior a 0,1% e zero armadilhas de spam.

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
