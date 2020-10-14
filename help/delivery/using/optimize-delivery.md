---
title: Otimizar o delivery de mensagem
seo-title: Otimizar o delivery de mensagem
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
translation-type: tm+mt
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 94%

---


# Otimizar o delivery{#optimize-delivery}

Antes mesmo de começar a criar os deliveries, você pode realizar várias ações para proteger e otimizar o fluxo do processo de envio.

A seção a seguir descreve as práticas e os procedimentos recomendados para a configuração ideal do Adobe Campaign. Seguir essas práticas minimizará os problemas que você poderá enfrentar downstream.

## Desempenho da plataforma

Vários fatores podem afetar diretamente o desempenho do servidor e retardar a plataforma:

* O número e o tipo de elementos de personalização: a personalização em emails extrai dados do banco de dados para cada recipient. Se houver muitos elementos de personalização, isso aumentará a quantidade de dados necessários para preparar o delivery.  Saiba mais sobre a personalização [nesta seção](../../delivery/using/about-personalization.md)

* A carga do servidor: quando o servidor de marketing estiver lidando com várias tarefas diferentes ao mesmo tempo, o desempenho poderá ser retardado. O servidor de marketing precisa coordenar todos os dados de entrada e saída de todos os deliveries para garantir que os dados estejam corretos no momento correto.

   **Dica** - Para evitar isso, coordene a programação de deliveries com os outros membros da equipe, garantindo um melhor desempenho.

* A execução do workflow: o monitoramento de seus workflows é essencial para evitar problemas de desempenho na plataforma. Siga as diretrizes listadas [neste documento](../../workflow/using/workflow-best-practices.md#execution-and-performance).

* Como cliente hospedado, você pode aproveitar os [recursos do Painel de controle do Campaign](https://docs.adobe.com/content/help/pt-BR/control-panel/using/discover-control-panel/key-features.html) para monitorar sua plataforma, usando as funcionalidades de [monitoramento de desempenho](https://docs.adobe.com/content/help/pt-BR/control-panel/using/performance-monitoring/about-performance-monitoring.html).

## Verificar a configuração da rede {#network-config}

Para otimizar o delivery ao manipular emails em grandes volumes e evitar ser confundido com um spammer, verifique se você tem uma configuração de rede legítima que não tenta ocultar a identidade do servidor.

**Dica**: use um endereço de remetente transparente, correspondente ao site da sua marca. Por exemplo, a empresa TravelAgency gerencia a cadeia de hotéis Valentino. É proprietária do domínio valentino.com para o seu site. Para promover o hotel Valentino em Paris, ele usa o subdomínio paris.valentino.com. Portanto, um endereço de remetente relevante pode ser hotel@paris.valentino.com.

## Gerenciamento da capacidade de entrega {#deliverability-management}

Para alcançar a caixa de entrada de seus recipients sem ser rejeitado ou ser marcado como spam, você precisa melhorar a taxa de entrega de suas mensagens.

* O que é a capacidade de entrega?

   * Refere-se aos fatores de um e-mail que determinam sua capacidade de ser aceito pelo servidor do destinatário. Os ISPs (provedores de serviço de internet) filtram emails identificados como SPAM ou bloqueiam o download de imagens. Se um determinado domínio estiver enviando muitos emails, eles definirão um número limite de emails provenientes desse remetente que serão aceitos.

   * Ao verificar seu email quanto à capacidade de delivery, você deseja se concentrar em quatro categorias principais: qualidade de dados, mensagem e conteúdo, infraestrutura de envio e reputação. Para aprofundar esse tópico, consulte [esta seção](../../delivery/using/about-deliverability.md).

* Aplique as recomendações detalhadas [neste documento](../../delivery/using/deliverability-key-points.md).

* Entre em contato com seu representante da Adobe para obter assistência.

## Gerenciamento de quarentenas {#quarantine-management}

É de seu interesse manter bons processos de gerenciamento de quarentena.

Ao começar a enviar e-mails em uma nova plataforma, você pode usar uma lista de endereços que não são totalmente qualificados. Se você enviar para endereços inválidos ou endereços honeypot (caixas de correio criadas apenas para enganar spammers), a reputação da sua plataforma será afetada. Os bons processos de gerenciamento de quarentenas ajudam a: mantenha a qualidade do endereço, evite lista de bloqueios por provedores de acesso à Internet e reduza sua taxa de erro, acelerando delivery e throughput.

**Dicas**

* Se você tiver uma lista de endereços inválidos, a Adobe recomenda importá-la para a tabela de quarentena, por meio de **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* Os recipients cujos endereços estão em quarentena são excluídos por padrão durante a análise de delivery: não são direcionados. Isso irá acelerar os deliveries, pois a taxa de erro tem um efeito significativo na velocidade do delivery. Um endereço de email pode ser colocado em quarentena, por exemplo, quando a caixa de entrada estiver cheia ou se o endereço não existir. [Saiba mais](#identifying-quarantined-addresses-for-a-delivery)

* O Adobe Campaign gerencia endereços incorretos de acordo com o tipo de erro retornado. Para obter mais informações, consulte [esta seção](../../delivery/using/understanding-quarantine-management.md).


* Alguns provedores de acesso à Internet consideram automaticamente emails como spam se a taxa de endereços inválidos for muito alta. A quarentena, portanto, permite que você evite ser adicionada à lista de bloqueios por esses provedores.

* Além disso, o gerenciamento de quarentenas ajuda a reduzir os custos de envio de SMS, excluindo números de telefone incorretos dos deliveries.

## Mecanismo de aceitação de duplicação {#double-opt-in}

Para evitar o envio de mensagens para endereços inválidos, limitar as comunicações inadequadas e melhorar a reputação do remetente, a Adobe recomenda a implementação de um mecanismo de aceitação de duplicação para confirmação pós-subscrição. Isso ajuda a garantir que um destinatário seja inscrito intencionalmente.

Os detalhes relativos à implementação deste mecanismo são descritos [nesta seção](../../web/using/use-cases--web-forms.md).
