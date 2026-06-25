---
product: campaign
title: Otimizar entrega de mensagens
description: Saiba como otimizar a entrega de mensagens
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Deliverability
role: User
hide: true
exl-id: 24b2ee47-bec7-43ce-81b3-0b2d1a5cebae
TQID: https://experienceleague.adobe.com/XiK0I9mZTlGWACRL-TTdDO5pByzBg-6oFdfcTNfhX44
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: b4dd41a7-ccf8-4e9d-918e-acaab534a307
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 758
ht-degree: 100%

---

# Otimizar a entrega {#optimize-delivery}

Antes mesmo de começar a criar as entregas, você pode realizar várias ações para proteger e otimizar o fluxo do processo de envio.

A seção a seguir descreve as práticas e os procedimentos recomendados para a configuração ideal do Adobe Campaign. Seguir essas práticas minimizará os problemas que você poderá enfrentar downstream.

## Desempenho da plataforma

Vários fatores podem afetar diretamente o desempenho do servidor e retardar a plataforma:

* O número e o tipo de elementos de personalização: a personalização em emails extrai dados do banco de dados para cada destinatário. Se houver muitos elementos de personalização, isso aumentará a quantidade de dados necessários para preparar a entrega.  Saiba mais sobre a personalização [nesta seção](about-personalization.md)

* A carga do servidor: quando o servidor de marketing estiver lidando com várias tarefas diferentes ao mesmo tempo, o desempenho poderá ser retardado. O servidor de marketing precisa coordenar todos os dados de entrada e saída de todas as entregas para garantir que os dados estejam corretos no momento correto.

  **Dica** - Para evitar isso, coordene a programação de entregas com os outros membros da equipe, garantindo um melhor desempenho.

* A execução do fluxos de trabalho: o monitoramento de seus fluxos de trabalho é essencial para evitar problemas de desempenho na plataforma. Siga as diretrizes listadas [neste documento](../../workflow/using/workflow-best-practices.md#execution-and-performance).

* Caso seja elegível, você poderá aproveitar os [recursos do Painel de controle](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=pt-BR) para monitorar sua plataforma usando as funcionalidades de [monitoramento de desempenho](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/about-performance-monitoring.html?lang=pt-BR).

## Verificar a configuração da rede {#network-config}

Para otimizar a entrega ao manipular emails em grandes volumes e evitar ser confundido com um spammer, verifique se você tem uma configuração de rede legítima que não tenta ocultar a identidade do servidor.

**Dica**: use um endereço de remetente transparente, correspondente ao site da sua marca. Por exemplo, a empresa TravelAgency gerencia a cadeia de hotéis Valentino. É proprietária do domínio valentino.com para o seu site. Para promover o hotel Valentino em Paris, ele usa o subdomínio paris.valentino.com. Portanto, um endereço de remetente relevante pode ser hotel@paris.valentino.com.

## Gerenciamento de avaliação de entrega {#deliverability-management}

Para alcançar a caixa de entrada de seus destinatários sem ser rejeitado ou ser marcado como spam, você precisa melhorar a taxa de entrega de suas mensagens.

* O que é a capacidade de entrega?

   * Ela se refere aos fatores de um email que determinam sua capacidade de ser aceito pelo servidor do destinatário. Os ISPs (provedores de serviço de internet) filtram emails identificados como SPAM ou bloqueiam o download de imagens. Se um determinado domínio estiver enviando muitos emails, eles definirão um número limite de emails provenientes desse remetente que serão aceitos.

   * Ao verificar seu email quanto à capacidade de entrega, você deseja se concentrar em quatro categorias principais: qualidade de dados, mensagem e conteúdo, infraestrutura de envio e reputação. Para aprofundar esse tópico, consulte [esta seção](about-deliverability.md).

* Aplique as recomendações detalhadas [neste documento](about-deliverability.md).

* Entre em contato com seu representante da Adobe para obter assistência.

## Gerenciamento de quarentena {#quarantine-management}

É de seu interesse manter bons processos de gerenciamento de quarentena.

Ao começar a enviar e-mails em uma nova plataforma, você pode usar uma lista de endereços que não são totalmente qualificados. Se você enviar para endereços inválidos ou endereços honeypot (caixas de correio criadas apenas para enganar spammers), a reputação da sua plataforma será afetada. Bons processos de gerenciamento de quarentena ajudam a manter a qualidade do endereço, evitar a lista de bloqueios de provedores de acesso à internet, reduzir a taxa de erro acelerando as entregas e a taxa de transferência.

**Dicas**

* Se você tiver uma lista de endereços inválidos, a Adobe recomenda importá-la para a tabela de quarentena, por meio de **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* Os destinatários cujos endereços estão em quarentena são excluídos por padrão durante a análise de entrega: não são direcionados. Isso irá acelerar as entregas, pois a taxa de erro tem um efeito significativo na velocidade da entrega. Um endereço de email pode ser colocado em quarentena, por exemplo, quando a caixa de entrada estiver cheia ou se o endereço não existir. [Saiba mais](#identifying-quarantined-addresses-for-a-delivery)

* O Adobe Campaign gerencia endereços incorretos de acordo com o tipo de erro retornado. Para obter mais informações, consulte [esta seção](delivery-failures-quarantine.md).


* Alguns provedores de acesso à Internet consideram automaticamente emails como spam se a taxa de endereços inválidos é muito alta. A quarentena, portanto, evita que você seja adicionado à lista de bloqueios por esses provedores.

* Além disso, o gerenciamento de quarentena ajuda a reduzir os custos de envio de SMS, excluindo números de telefone incorretos de entregas.

## Mecanismo de dupla aceitação {#double-opt-in}

Para evitar o envio de mensagens para endereços inválidos, limitar as comunicações inadequadas e melhorar a reputação do remetente, a Adobe recomenda a implementação de um mecanismo de aceitação de duplicação para confirmação pós-subscrição. Isso ajuda a garantir que um destinatário seja inscrito intencionalmente.

Os detalhes relativos à implementação deste mecanismo são descritos [nesta seção](../../web/using/use-cases-web-forms.md).
