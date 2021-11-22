---
product: campaign
title: Descrição do modelo de dados do Adobe Campaign Classic
description: Este documento descreve o modelo de dados Adobe Campaign.
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: fc0fd23c-f9ea-4e30-b47b-a84143d882ca
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '2374'
ht-degree: 1%

---

# Descrição do modelo de dados da campanha{#data-model-description}

![](../../assets/v7-only.svg)

O Adobe Campaign vem com um modelo de dados predefinido. Esta seção fornece alguns detalhes sobre as tabelas integradas do modelo de dados do Adobe Campaign e sua interação.

Para acessar a descrição de cada tabela, acesse **[!UICONTROL Admin > Configuration > Data schemas]**, selecione um recurso na lista e clique no botão **[!UICONTROL Documentation]** guia .

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>A estrutura física e lógica dos dados transportados no aplicativo é descrita em XML. Ela obedece a uma gramática específica do Adobe Campaign, chamada de schema. Para obter mais informações sobre schemas Adobe Campaign, leia [esta seção](../../configuration/using/about-schema-reference.md).

## Descrição dos quadros principais {#description-main-tables}

O Adobe Campaign depende de um banco de dados relacional contendo tabelas vinculadas.

O diagrama a seguir mostra as associações entre as principais tabelas de negócios do modelo de dados do Adobe Campaign com os campos principais de cada um.

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

O modelo de dados Adobe Campaign predefinido inclui as principais tabelas listadas abaixo.

### NmsRecipient {#NmsRecipient}

Essa tabela corresponde ao **nms:recipient** esquema.

É a tabela padrão usada para a variável **recipients de deliveries**. Como resultado, ele contém as informações necessárias para os deliveries por meio dos vários canais:

* sEmail: endereço de email.
* iEmailFormat: formato preferencial para emails (1 para Texto, 2 para HTML e 0 se indefinido).
* sAddress1, sAddress2, sAddress3, sAddress4, sZipCode, sCity são usadas para criar o endereço postal (em conformidade com o padrão AFNOR XPZ 10-011 de maio de 1997).
* sPhone, sMobilePhone, sFax contêm números de telefone, celular e fax, respectivamente.
* iBlackList é o sinalizador de recusa padrão usado para os perfis (1 significa &quot;cancelado de assinatura&quot;, 0 caso contrário).

O campo iFolderId é a chave estrangeira que vincula o recipient à pasta de execução. Para obter mais informações, consulte [XtkFolder](#XtkFolder).

O campo sCountryCode é o código ISO 3166-1 Alpha 2 (2 caracteres) do país associado ao recipient. Na verdade, esse campo é uma chave estrangeira na tabela de referência do país (NmsCountry), que contém os rótulos do país e outros dados de código do país. Se o país não estiver preenchido, o valor &#39;XX&#39; será armazenado (e usado no lugar de um registro de ID zero).

Para obter mais informações sobre a tabela Recipient, consulte [esta seção](../../configuration/using/about-data-model.md#default-recipient-table).

### NmsGroup {#NmsGroup}

Essa tabela corresponde ao **nms:group** esquema.

Ele permite criar **grupos estáticos de recipients**. Há uma relação muitos para muitos entre recipients e grupos. Por exemplo, um recipient pode pertencer a vários grupos e um grupo pode conter vários recipients. Os grupos podem ser criados manualmente, por meio de uma importação ou por meio do target de delivery. Os grupos são frequentemente usados como alvos do delivery. Há um índice exclusivo no campo que representa o nome interno do grupo sName. O grupo está vinculado a uma pasta (A chave é iFolderId. Para obter mais informações, consulte [XtkFolder](#XtkFolder)).

### NmsRcpGrpRel {#NmsRcpGrpRel}

A tabela de relacionamento NmsRcpGrpRel contém apenas os dois campos correspondentes aos identificadores das tabelas vinculadas iRecipientId e iGroupId.

### NmsService {#NmsService}

Essa tabela corresponde ao **nms:service** esquema.

No Adobe Campaign, é possível criar e gerenciar subscrições de serviços de informações (tópicos). A tabela NmsService armazena a definição dos serviços de informações (tópicos) aos quais você oferece aos recipients para assinar (um boletim informativo, por exemplo).

Os serviços são entidades semelhantes a grupos (agrupamentos de recipients estáticos), exceto que circulam mais informações e permitem o gerenciamento fácil de subscrições e unsubscriptions por meio de formulários.

Há um índice exclusivo no campo que representa o nome interno do serviço sName. O serviço está vinculado a uma pasta (A chave é iFolderId. Para obter mais informações, consulte [XtkFolder](#XtkFolder)). Finalmente, o campo iType especifica o canal de delivery desse serviço (0 para email, 1 para SMS, 2 para telefone, 3 para correspondência direta e 4 para fax).

### NmsSubscription {#NmsSubscription}

Essa tabela corresponde ao **nms:subscription** esquema.

Ele permite gerenciar assinaturas de destinatários de serviços de informações.

### NmsSubHisto {#NmsSubHisto}

Essa tabela corresponde ao **nms:subHisto** esquema.

Se as assinaturas forem gerenciadas usando formulários web ou a interface do aplicativo, todas as assinaturas e unsubscriptions serão historicamente registradas na tabela NmsSubHisto . O campo iAction especifica a ação (0 para cancelamento de subscrição e 1 para subscrição) executada na data armazenada no campo tsDate .

### NmsDelivery {#NmsDelivery}

Essa tabela corresponde ao **nms:delivery** esquema.

Cada registro nesta tabela representa um **ação de delivery** ou **template do delivery**. Ela contém todos os parâmetros necessários para executar deliveries (o target, o conteúdo, etc.). Logs de delivery (transmissão) (NmsBroadLog) e URLs de rastreamento associadas (NmsTrackingUrl) são criados durante a fase de análise (veja abaixo para obter mais detalhes sobre essas duas tabelas).

Há um índice exclusivo no campo que representa o nome interno do delivery ou do cenário sInternalName. O delivery é vinculado a uma pasta de execução (a chave externa é iFolderProcessId. Para obter mais informações, consulte [XtkFolder](#XtkFolder)).

### XtkFolder {#XtkFolder}

Ele contém **todas as pastas na árvore** visível no **Navegação** do console.

As pastas são digitadas: o valor do campo sModel especifica o tipo de dados que pode ser contido na pasta. Esse campo também permite que o console do cliente exiba os dados corretamente com os formulários correspondentes. Os valores possíveis para esse campo são definidos na navTree.

A árvore é gerenciada pelos campos iParentId e iChildCount . O campo sFullName fornece o caminho completo da pasta na árvore. Finalmente, há um índice exclusivo no campo que representa o nome interno da pasta sName.

## Delivery e rastreamento {#delivery-and-tracking}

Esse conjunto de tabelas está vinculado à variável **Delivery** , que permite monitorar deliveries e eventuais problemas encontrados quando as mensagens são enviadas. Para obter mais informações, consulte [Monitoramento de deliveries](../../delivery/using/about-delivery-monitoring.md). Para obter mais informações sobre o rastreamento, consulte [Rastreamento de mensagens](../../delivery/using/about-message-tracking.md).

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**: Essa tabela corresponde ao **nms:broadLogMsg** esquema. É uma extensão da tabela de log do delivery.

## Gerenciamento de campanhas {#campaign-management}

Esse conjunto de tabelas está vinculado à variável **Campanhas de marketing** , que permite definir, otimizar, executar e analisar campanhas de comunicações e marketing. Para obter mais informações, consulte [Sobre campanhas de marketing](../../campaign/using/designing-marketing-campaigns.md).

![](assets/data-model_campaign.png)

* **NmsOperation**: Essa tabela corresponde ao **nms:operation** esquema. Ele contém os dados das campanhas de marketing.
* **NmsDeliveryOutline**: Essa tabela corresponde ao **nms:deliveryOutline** esquema. Ele contém as propriedades estendidas do delivery (delivery outline).
* **NmsDlvOutlineItem**: Essa tabela corresponde ao **nms:dlvOutlineItem** esquema. Ele contém os artigos de um delivery outline.
* **NmsDeliveryCustomization**: Essa tabela corresponde ao **nms:deliveryCustomization** esquema. Ele contém os campos de personalização de um delivery.
* **NmsBudget**: Essa tabela corresponde ao **nms:budget** esquema. Ele contém os dados de um orçamento em uma campanha, um plano, um programa, uma tarefa e/ou deliveries.
* **NmsDocument**: Essa tabela corresponde ao **nms:document** esquema. Ele contém os documentos de marketing da campanha na forma de arquivos (imagens, arquivos excel ou word etc.)
* **XtkWorkflow**: Essa tabela corresponde ao **xtk:workflow** esquema. Ele contém o direcionamento da campanha.
* **NmsTask**: Essa tabela corresponde ao **nms:task** esquema. Ele contém a definição de uma tarefa de marketing.
* **NmsAsset**: Essa tabela corresponde ao **nms:asset** esquema. Ele contém a definição de um recurso de marketing.

## Consistência da comunicação {#communication-consistency}

Esse conjunto de tabelas está vinculado à variável **Otimização de campanha** , que permite controlar, filtrar e monitorar o envio de deliveries. Para obter mais informações, consulte [Sobre tipologias de campanha](../../campaign-opt/using/about-campaign-typologies.md).

![](assets/data-model_typology.png)

* **NmsTypologyRule**: Essa tabela corresponde ao **nms:typologyRule** esquema. Ele contém as regras que se aplicam aos deliveries, dependendo das tipologias.
* **NmsTypology**: Essa tabela corresponde ao **nms:tipologia** esquema. Ele contém o conjunto de regras a serem aplicadas aos deliveries que correspondem à tipologia.
* **NmsTypologyRuleRel**: Essa tabela corresponde ao **nms:typologyRuleRel** esquema. Ele contém os relacionamentos entre tipologias e suas regras.
* **NmsVolumeLine**: Essa tabela corresponde ao **nms:volumeLine** esquema. Ele contém o conjunto de linhas de disponibilidade das regras de capacidade.
* **NmsVolumeConsumed**: Essa tabela corresponde ao **nms:volumeConsumed** esquema. Ele contém todas as linhas de consumo das regras de capacidade.

## Gestor de resposta {#response-management}

Esse conjunto de tabelas está vinculado à variável **Gestor de Resposta** , que permite medir o sucesso e a lucratividade de campanhas de marketing ou apresentações de oferta para todos os canais de comunicação. Para obter mais informações, consulte [Sobre o gestor de resposta](../../response/using/about-response-manager.md).

![](assets/data-model_response.png)

### NmsRemaHypothesis {#NmsRemaHypothesis}

Esta tabela coincide com o **nms:remaHypothesis** esquema. Ele contém a definição da hipótese de medição.

Esta tabela contém informações significativas armazenadas em XML, incluindo:

**Contexto de execução (informações armazenadas em XML)**

O contexto de execução preenche as tabelas e os campos a serem considerados para o cálculo da medição, a saber:
* O schema de armazenamento do log de reação nms:remaMatchRcp.
* O schema da tabela de transações (compras por exemplo).
* O schema querying , que permite definir a tabela inicial das condições da hipótese.
* Os links para indivíduos, que permitem identificar o indivíduo com base no schema de consulta.
* A data da transação. Este campo não é obrigatório, mas recomendamos usá-lo para restringir o perímetro de cálculo.
* O valor da transação: é um campo opcional para calcular indicadores de receita automaticamente.

**Perímetro da hipótese (informações armazenadas em XML)**

O perímetro da hipótese consiste na filtragem da hipótese com base na tabela do schema de query.

**Script de sobrecarga da hipótese (informações armazenadas em XML)**

O script de sobrecarga da hipótese é um código JavaScript que permite sobrecarregar o conteúdo da hipótese durante a execução.

**Indicadores de medição**

Os seguintes indicadores são atualizados automaticamente durante a execução da hipótese:

* Número de reações: **iTransaction**. Número de linhas na tabela de logs de reação.
* Número de contatos: **iContactReacted**. Número distinto de contatos direcionados na hipótese.
* Contagem do grupo de controle: **iProofReacted**. Número distinto de contatos de grupo de controle direcionado na hipótese.
* Taxa de resposta contatada: **dContactReactedRate**. Taxa de resposta dos contatos direcionados na hipótese.
* Taxa de resposta do grupo de controle: **dProofReactedRate**. Taxa de resposta do grupo de controle da hipótese.
* Receita total da população contactada: **dContactReactedTotalAmount**. Receita total dos contatos direcionados na hipótese.
* Receita média do grupo de controle: **dContactReactedAvgAmount**. Receita média dos contatos do grupo de controle direcionado na hipótese.
* Receitas totais do grupo de controlo: **dProofReactedTotalAmount**. Receita total do grupo de controle da hipótese.
* Receita média do grupo de controle: **dProofReactedAvgAmount**. Receita média do grupo de controle da hipótese.
* Margem total por contato: **dContactReactedTotalMargin**. Margem total por contato direcionado na hipótese.
* Margem média por contato: **dContactReactedAvgMargin**. Margem média por contato direcionado na hipótese.
* Margem total do grupo de controle: **dProofReactedTotalMargin**. Margem total do grupo de controle direcionado na hipótese.
* Margem média do grupo de controle: **dProofReactedAvgMargin**. Margem média do grupo de controle direcionado na hipótese.
* Receita adicional: **dAdditionalAmount**. (Average revenue of contact - Average revenue of control group) * Número de contatos.
* Margem adicional: **dAdditionalMargin**. (Average margin of contact - Average margin of control group) / Número de contatos.
* Custo médio por contato (expressão SQL). Custo calculado do delivery/Número de contatos.
* ROI (expressão SQL). Custo calculado do delivery / margem total do contato.
* ROI efetivo (expressão SQL). Custo calculado do delivery / margem adicional.
* Significância: **iSignificativo** (expressão SQL). Contém valores de 0 a 3 dependendo do significado da campanha.

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

Essa tabela corresponde ao **nms:remaMatchRcp** esquema.

Ele contém um registro que representa a reação de um indivíduo a uma determinada hipótese. Esses registros foram criados durante a execução da hipótese.

## Simulação e delivery {#simulation-and-delivery}

Esse conjunto de tabelas está vinculado à variável **Simulação** , que permite testar a distribuição de ofertas pertencentes a uma categoria ou um ambiente antes de enviar sua proposta para os recipients. Para obter mais informações, consulte [Sobre a simulação de ofertas](../../interaction/using/about-offers-simulation.md).

![](assets/data-model_simulation.png)

* **NmsSimulation**: Essa tabela corresponde ao **nms:simulation** esquema. Ela representa uma simulação para um conjunto de deliveries ou ofertas em uma determinada população.
* **NmsDlvSimulationRel**: Essa tabela corresponde ao **nms:dlvSimulationRel** esquema. Ele contém a lista de deliveries considerados na simulação. O escopo da simulação é armazenado em XML.
* **NmsOfferSimulationRel**: Essa tabela corresponde ao **nms:offerSimulationRel** esquema. Ela permite vincular uma simulação a uma oferta.

## Interaction Module {#interaction-module}

Esse conjunto de tabelas está vinculado à variável **Interação** , que permite responder em tempo real durante uma interação com um determinado contato, tornando-o uma única ou várias ofertas adaptadas. For more on this, see [Interaction and offer management](../../interaction/using/interaction-and-offer-management.md).

* **NmsOffer**: Essa tabela corresponde ao **nms:offer** esquema. Ele contém a definição de cada oferta de marketing.
* **NmsPropositionRcp**: Essa tabela corresponde ao **nms:propositionRcp** esquema. It contains the cross-channel log of marketing propositions sent to each individual. O registro é criado quando uma proposta é preparada ou efetivamente feita a um indivíduo.
* **NmsOfferSpace**: Essa tabela corresponde ao **nms:offerSpace** esquema. Ele contém a definição de locais em que as apresentações são feitas.
* **NmsOfferContext**: Essa tabela corresponde ao **nms:offerContext** esquema. Contém critérios adicionais sobre a aplicabilidade da proposta, bem como sobre a definição da fórmula de cálculo do peso.
* **NmsOfferView**: Essa tabela corresponde ao **nms:offerView**. Ele contém as representações de oferta.
* **NmsOfferCategory**: Essa tabela corresponde ao **nms:offerCategory**. Ele contém as categorias de ofertas.
* **NmsOfferEnv**: Essa tabela corresponde ao **nms:offerEnv**. Ele contém os ambientes de oferta.

## Módulo do Centro de Mensagens {#message-center-module}

O seguinte conjunto de tabelas está vinculado à variável **Mensagens transacionais** Módulo (Centro de mensagens), que permite gerenciar comunicações individuais e exclusivas enviadas a um usuário e geradas por eventos acionados de sistemas de informações. Para obter mais informações, consulte [Sobre mensagens transacionais](../../message-center/using/about-transactional-messaging.md).

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

Essa tabela corresponde ao **nms:rtEvent** esquema. Ele contém uma definição de eventos em tempo real.

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

Essa tabela corresponde ao **nms:batchEvent** esquema. Ele contém a definição de eventos por lote.

<!--## Microsites Module {#microsites-module}

This set of tables is linked to the **Web applications** functionality, which allows to create and publish dynamic and interactive web applications with data from the database and content adapted to the rights of the connected user. For more on this, see [About web applications](../../web/using/about-web-applications.md).

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: This table matches the **nms:trackingUrl** schema.

* **NmsPurl**: This table matches the **nms:purl** schema.-->

## Módulo NMAC {#nmac-module}

Esse conjunto de tabelas está vinculado à variável **Canal de aplicativo móvel**, que permite enviar notificações personalizadas para terminais iOS e Android por meio de aplicativos. Para obter mais informações, consulte [Sobre o canal de aplicativo móvel](../../delivery/using/about-mobile-app-channel.md).

* **NmsMobileApp**: Essa tabela corresponde ao **nms:mobileApp** esquema. Ele contém os aplicativos móveis definidos no Adobe Campaign.
* **NmsAppSubscription**: Essa tabela corresponde ao **nms:appSubscription** esquema. Ele contém as informações dos assinantes sobre um ou mais aplicativos.
* **NmsAppSubscriptionRcp**: Essa tabela corresponde ao **nms:appSubscriptionRcp** esquema. Ele permite vincular os visitantes que se inscreveram em um aplicativo com a tabela de recipients.
* **NmsExcludeLogAppSubRcp**: Essa tabela corresponde ao **nms:excludeLogAppSubRcp** esquema.
* **NmsTrackingLogAppSubRcp**: Essa tabela corresponde ao **nms:trackingLogAppSubRcp** esquema.
* **NmsBroadLogAppSubRcp**: Essa tabela corresponde ao **nms:broadLogAppSubRcp** esquema.

## Módulo de marketing social {#social-marketing-module}

Esse conjunto de tabelas está vinculado à variável **Gerenciamento de redes sociais** , que permite interagir com clientes e clientes potenciais via Facebook e Twitter. Para obter mais informações, consulte [Sobre marketing social](../../social/using/about-social-marketing.md).

![](assets/data-model_social.png)

* **NmsVisitor**: Essa tabela corresponde ao **nms:visitor** esquema. Ele contém informações sobre visitantes.
* **NmsVisitorSub**: Essa tabela corresponde ao **nms:visitorSub** esquema. Ela permite vincular um visitante aos serviços que ele assinou (Twitter ou Facebook).
* **NmsFriendShippingRel**: Essa tabela corresponde ao **nms:friendlyRel** esquema. Ela permite vincular visitantes com seus amigos no contexto do serviço Facebook.
* **NmsVisitorInterestRel**: Essa tabela corresponde ao **nms:visitorInterestRel** esquema. Permite vincular visitantes e seus interesses.
* **NmsInterest**: Essa tabela corresponde ao **nms:interest** esquema. Ele contém a lista de interesses para cada visitante.
