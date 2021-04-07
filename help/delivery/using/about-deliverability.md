---
solution: Campaign Classic
product: campaign
title: Sobre a capacidade de delivery no Campaign
description: Saiba mais sobre as práticas recomendadas de delivery
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
translation-type: tm+mt
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 12%

---

# O que é a capacidade de entrega{#about-deliverability}

A capacidade de delivery permite medir o sucesso das campanhas em chegar à caixa de entrada dos recipients sem rejeição ou sem serem marcadas como spam. [Saiba por que a capacidade de entrega é importante](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html#why-deliverability-matters).

Mais precisamente, a capacidade de fornecimento de email refere-se ao conjunto de características que determinam a capacidade de uma mensagem de alcançar seu destino por meio de um endereço de email pessoal, dentro de um curto período e com a qualidade esperada em termos de conteúdo e formato.

Para aprofundar o assunto e saber mais sobre os termos, conceitos e abordagens principais da capacidade de entrega, consulte o [Guia de práticas recomendadas de capacidade de entrega do Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=pt-BR).

## Como melhorar a capacidade de entrega {#deliverability-key-points}

Os problemas de capacidade de entrega estão geralmente ligados às medidas de proteção contra spam implementadas pelos provedores de serviços de Internet e administradores de servidores de correio.

* Para obter recomendações gerais sobre como projetar campanhas de marketing por email bem-sucedidas, consulte [Estratégia e definição de capacidade de delivery](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html).

* Para obter recomendações mais específicas sobre como otimizar a capacidade de entrega dos emails do Adobe Campaign, o Adobe recomenda o uso das práticas recomendadas listadas nesta seção.

>[!NOTE]
>
>Como os ISPs são obrigados a desenvolver continuamente novas técnicas sofisticadas de filtragem para proteger seus clientes de remetentes de spam, a capacidade de fornecimento de email é caracterizada por critérios e regras em constante mudança. Certifique-se de consultar o [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html) que é atualizado regularmente.

### Taxa de entregabilidade

A taxa de deliverability é o número de mensagens que acessam as caixas de entrada dos recipients em comparação ao número de mensagens que foram entregues. Para melhorar o deliverability, você pode trabalhar para aumentar essa taxa.

Com o Adobe Campaign, a taxa de deliverability depende de vários fatores, especialmente:

* Configuração correta de suas instâncias: entre em contato com o representante do Adobe para obter assistência.
* Configuração de rede legítima: consulte [esta seção](../../delivery/using/optimize-delivery.md#network-config) e [Configuração e estratégia do domínio](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#domain-setup-and-strategy).
* Sua reputação do endereço IP: consulte [Estratégia de IP](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#ip-strategy).
* Qualidade dos endereços direcionados: consulte [Gestão de Quarentena](../../delivery/using/optimize-delivery.md#quarantine-management).
* Taxas de [reclamações](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html) e [rejeição permanente](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html#hard-bounces) baixas.
* O conteúdo da mensagem: consulte [Controle de conteúdo de email](../../delivery/using/control-message-content.md).
* Autenticação de mensagem (SPF, DKIM, DMARC): consulte [esta seção](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).
* Reputação do remetente: para saber como os ISPs principais avaliam a reputação de um remetente, consulte [esta seção](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html).

## Ferramentas de capacidade de entrega da campanha {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
O Adobe Campaign fornece várias ferramentas para acompanhar e melhorar o desempenho da capacidade de entrega da sua plataforma. Esta página também destaca os principais princípios que você deve ter em mente para otimizar a capacidade de entrega ao usar o Campaign.

### Crie cuidadosamente a sua mensagem

Ao configurar, projetar e testar sua mensagem, siga as práticas recomendadas mencionadas nas seções listadas abaixo. Aproveitar todos os recursos fornecidos pela Adobe Campaign ajuda a melhorar a capacidade de entrega.

* [Práticas recomendadas para delivery](../../delivery/using/delivery-best-practices.md)
* [Controle de conteúdo de e-mail](../../delivery/using/control-message-content.md)
* [Renderização da caixa de entrada](../../delivery/using/inbox-rendering.md)
* [Envio de uma prova](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)

### Verificar consentimento por meio da aceitação dupla {#double-opt-in}

Para evitar o envio de mensagens para endereços inválidos, limitar as comunicações inadequadas e melhorar a reputação do remetente, o Adobe recomenda a implementação de um mecanismo de aceitação dupla. Esse método permite garantir que seus recipients tenham assinado intencionalmente.

Para obter mais informações, consulte [Criar um formulário de inscrição com dupla aceitação](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).

Para obter mais informações sobre as práticas recomendadas ao coletar dados de seus clientes, consulte o [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html#data-quality-and-hygiene).

### Aproveite o gerenciamento de quarentena

O Adobe Campaign gerencia uma lista que reúne reclamações de spam, devoluções permanentes e devoluções temporárias que ocorrem de forma consistente.

Para proteger sua capacidade de delivery, os recipients cujos endereços estão nessa lista são excluídos por padrão de todos os deliveries futuros, porque o envio para esses contatos pode prejudicar sua reputação de envio.

Alguns provedores de acesso à Internet consideram automaticamente emails como spam se a taxa de endereços inválidos for muito alta. A quarentena, portanto, evita que você seja adicionado à lista de bloqueios por esses provedores.

Para obter mais informações, consulte as seguintes seções:

* [Noções básicas sobre falhas de delivery](../../delivery/using/understanding-delivery-failures.md)
* [Noções básicas sobre gestão de quarentena](../../delivery/using/understanding-quarantine-management.md)
* [Quarentena × lista de bloqueios](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)

### Usar ferramentas de monitoramento e relatórios

Use os recursos oferecidos pelo Adobe Campaign para monitorar sua capacidade de entrega.

O Adobe Campaign permite verificar o desempenho de seus deliveries por meio de um conjunto de indicadores e relatórios em tempo real incorporados, para obter insights aprimorados sobre seus deliveries.

Para obter mais informações, consulte as seguintes seções:

* [Monitoramento da capacidade de entrega](../../delivery/using/monitoring-deliverability.md)
* [Sobre o monitoramento de delivery](../../delivery/using/about-delivery-monitoring.md)
* [Sobre relatórios internos do Campaign](../../reporting/using/about-campaign-built-in-reports.md)

<!--TO REMOVE
## Background {#background}

Email deliverability presents a major challenge to marketers - whether they're sending a few thousand messages or several billion. One in five messages never reach the inbox, or their intended recipient.

Once relegated as a "technical issue" for the IT department, email deliverability continues to move higher on the marketing agenda. That's because savvy marketers recognize that although many of its elements are technical in nature, deliverability is ultimately a business issue with significant revenue implications.

Consider the email marketing funnel. Deliverability determines the number of messages received, which in turn impacts each subsequent stage of the funnel. Fewer emails received results in fewer opens, fewer clicks, and fewer conversions. **For companies with a large database, the difference between average and great deliverability could literally mean hundreds of thousands to millions of dollars in revenues.**

![](assets/deliverability_overview_1.png)

By settling for average (80%) deliverability, marketers are leaving significant conversions - and dollars - on the table.

What exactly is email deliverability? And how can marketers improve deliverability rates to widen the mouth of the funnel and squeeze more results from their email campaigns?

Email deliverability refers to the set of characteristics that determine a message's ability to reach its destination, via a personal e-mail address, within a short time, and with the expected quality in terms of content and format. These characteristics fall into four main categories: data quality, message and content, sending infrastructure, and reputation. Together, they form the foundation of a successful email deliverability program. This overview outlines the four fundamentals of email deliverability success and offers best practices for reaching the inbox and driving greater revenues from email marketing programs.

![](assets/deliverability_overview_2.png)-->
