---
product: campaign
title: Introdução à capacidade de entrega no Campaign
description: Saiba mais sobre as práticas recomendadas de capacidade de entrega
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Deliverability
role: User
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: ht
source-wordcount: '656'
ht-degree: 100%

---

# O que é capacidade de entrega{#about-deliverability}

A capacidade de entrega permite medir o sucesso das campanhas que chegam à caixa de entrada dos destinatários sem rejeição ou sem serem marcadas como spam. [Saiba por que a capacidade de entrega é importante](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html?lang=pt-BR#why-deliverability-matters).

Mais precisamente, a capacidade de entrega de email refere-se ao conjunto de características que determinam o potencial de uma mensagem de alcançar seu destino, por meio de um endereço de email pessoal, dentro de um curto período e com a qualidade esperada em termos de conteúdo e formato.

Para aprofundar o assunto e saber mais sobre os termos, conceitos e abordagens principais da capacidade de entrega, consulte o [Manual de práticas recomendadas de capacidade de entrega da Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=pt-BR).

## Como melhorar a capacidade de entrega {#deliverability-key-points}

Os problemas de capacidade de entrega estão geralmente ligados às medidas de proteção contra spam implementadas pelos provedores de serviços de Internet e administradores de servidores de correio.

* Para obter recomendações gerais sobre como projetar campanhas de marketing por email bem-sucedidas, consulte [Estratégia e definição de capacidade de entrega](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html?lang=pt-BR).

* Para obter recomendações mais específicas sobre como otimizar a capacidade de entrega dos emails do Adobe Campaign, a Adobe recomenda a utilização das práticas recomendadas listadas nesta seção.

>[!NOTE]
>
>Como os ISPs são obrigados a desenvolver continuamente novas técnicas sofisticadas de filtragem para proteger seus clientes contra remetentes de spam, a capacidade de entrega de email é caracterizada por critérios e regras em constante mudança. Consulte o [Manual de práticas recomendadas de capacidade de entrega da Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=pt-BR), que é atualizado regularmente.

### Taxa da capacidade de entrega

A taxa de capacidade de entrega é o número de mensagens que chegam nas caixas de entrada dos destinatários em comparação ao número de mensagens que foram entregues. Para melhorar a capacidade de entrega, você pode trabalhar para aumentar essa taxa.

Com o Adobe Campaign, a taxa da capacidade de entrega depende de vários fatores, principalmente:

* Configuração correta das instâncias: entre em contato com o representante da Adobe para obter assistência.
* Configuração de rede legítima: consulte [Configuração e estratégia do domínio](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=pt-BR#domain-setup-and-strategy).
* Reputação do seu endereço IP: consulte [Estratégia de IP](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=pt-BR#ip-strategy).
* Baixas taxas de [reclamação](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html?lang=pt-BR) e [rejeição permanente](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html?lang=pt-BR#hard-bounces).
* Conteúdo da mensagem: consulte [Controlar o conteúdo do email](control-message-content.md).
* Autenticação de mensagem (SPF, DKIM, DMARC): consulte [esta seção](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=pt-BR#authentication).
* Reputação do remetente: para saber como os principais ISPs avaliam a reputação de um remetente, consulte [esta seção](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html?lang=pt-BR).

## Ferramentas de capacidade de entrega do Campaign {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
O Adobe Campaign fornece várias ferramentas para acompanhar e melhorar o desempenho da capacidade de entrega da sua plataforma. Esta página também destaca os princípios mais importantes que você deve ter em mente para otimizar a capacidade de entrega ao usar o Campaign.

### Crie cuidadosamente a sua mensagem

Ao configurar, projetar e testar sua mensagem, siga as práticas recomendadas mencionadas nas seções listadas abaixo. Aproveitar todos os recursos fornecidos pelo Adobe Campaign ajuda a melhorar a capacidade de entrega.

* [Práticas recomendadas para entregas](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/delivery-best-practices.html?lang=pt-BR){target="_blank"}.
* [Controlar o conteúdo do email](control-message-content.md)
* [Renderização da caixa de entrada](inbox-rendering.md)
* [Envio de uma prova](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/preview-and-proof.html?lang=pt-BR){target="_blank"}

### Verificar consentimento por meio da aceitação dupla {#double-opt-in}

Para evitar o envio de mensagens a endereços inválidos, limitar as comunicações inadequadas e melhorar a reputação do remetente, a Adobe recomenda a implementação de um mecanismo de aceitação dupla. Esse método garante que seus destinatários se inscreveram intencionalmente.

Para obter mais informações, consulte [Criar um formulário de assinatura com aceitação dupla](../../web/using/use-cases-web-forms.md#create-a-subscription--form-with-double-opt-in).

Para obter mais informações sobre as práticas recomendadas ao coletar dados de clientes, consulte o [Manual de práticas recomendadas de capacidade de entrega da Adobe](https://experienceleague.adobe.com/pt-br/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth#data-quality-and-hygiene).

### Aproveitar o gerenciamento de quarentena

O Adobe Campaign gerencia uma lista que reúne reclamações de spam, rejeições permanentes e rejeições temporárias que ocorrem de forma consistente.

Para proteger sua capacidade de entrega, os destinatários cujos endereços estão nessa lista são excluídos por padrão de todas as entregas futuras, porque o envio para esses contatos pode prejudicar sua reputação de envio.

Alguns provedores de acesso à Internet consideram automaticamente emails como spam se a taxa de endereços inválidos é muito alta. A quarentena, portanto, evita que você seja adicionado à lista de bloqueios por esses provedores.

Para obter mais informações, consulte estas seções:

* [Entender as falhas de entrega](understanding-delivery-failures.md)
* [Entender o gerenciamento de quarentena](understanding-quarantine-management.md)
* [Quarentena × lista de bloqueios](understanding-quarantine-management.md#quarantine-vs-denylist)

### Usar ferramentas de monitoramento e relatórios

Use os recursos oferecidos pelo Adobe Campaign para monitorar a capacidade de entrega da sua plataforma.

O Adobe Campaign permite verificar o desempenho de suas entregas por meio de um conjunto de indicadores e relatórios em tempo real integrados para obter insights avançados sobre suas entregas.

Para obter mais informações, consulte estas seções:

* [Monitorar a capacidade de entrega](monitoring-deliverability.md)
* [Introdução ao monitoramento de entrega](about-delivery-monitoring.md)
* [Introdução aos relatórios integrados do Campaign](../../reporting/using/about-campaign-built-in-reports.md)
