---
product: campaign
title: Descrição do modelo de dados do Adobe Campaign Classic
description: Este documento descreve o modelo de dados do Adobe Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Data Model
exl-id: fc0fd23c-f9ea-4e30-b47b-a84143d882ca
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '2374'
ht-degree: 2%

---

# Descrição do modelo de dados do Campaign{#data-model-description}


O Adobe Campaign vem com um modelo de dados predefinido. Esta seção fornece alguns detalhes sobre as tabelas integradas do modelo de dados do Adobe Campaign e suas interações.

Para acessar a descrição de cada tabela, vá para **[!UICONTROL Admin > Configuration > Data schemas]**, selecione um recurso na lista e clique no botão **[!UICONTROL Documentation]** guia.

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>A estrutura física e lógica dos dados transportados no aplicativo é descrita em XML. Ela obedece a uma gramática específica do Adobe Campaign, chamada de schema. Para obter mais informações sobre esquemas do Adobe Campaign, leia [nesta seção](../../configuration/using/about-schema-reference.md).

## Descrição dos principais quadros {#description-main-tables}

O Adobe Campaign depende de um banco de dados relacional contendo tabelas vinculadas.

O diagrama a seguir mostra as associações entre as principais tabelas de negócios do modelo de dados do Adobe Campaign com os principais campos de cada um.

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

O modelo de dados predefinido do Adobe Campaign inclui as principais tabelas listadas abaixo.

### NmsRecipient {#NmsRecipient}

Esta tabela corresponde à **nms:recipient** esquema.

É a tabela padrão usada para o **recipients de deliveries**. Como resultado, contém as informações necessárias para deliveries por meio dos vários canais:

* sEmail: endereço de email.
* iEmailFormat: formato preferido para emails (1 para Texto, 2 para HTML e 0 se indefinido).
* sAddress1, sAddress2, sAddress3, sAddress4, sZipCode, sCity são usados para criar o endereço postal (de acordo com o padrão XPZ 10-011 AFNOR de maio de 1997).
* sPhone, sMobilePhone, sFax contêm os números de telefone, telefone celular e fax, respectivamente.
* iBlackList é o sinalizador de recusa padrão usado para os perfis (1 significa &quot;cancelado&quot;, caso contrário, 0).

O campo iFolderId é a chave externa que vincula o recipient à sua pasta de execução. Para obter mais informações, consulte [XtkFolder](#XtkFolder).

O campo sCountryCode é o código ISO 3166-1 Alfa 2 (2 caracteres) do país associado ao recipient. Na verdade, esse campo é uma chave estrangeira na tabela de referência de país (NmsCountry), que contém os rótulos de país e outros dados de código de país. Se o país não estiver preenchido, o valor &quot;XX&quot; será armazenado (e usado no lugar de um registro de ID zero).

Para obter mais informações sobre a tabela Recipient, consulte [nesta seção](../../configuration/using/about-data-model.md#default-recipient-table).

### NmsGroup {#NmsGroup}

Esta tabela corresponde à **nms:group** esquema.

Ele permite criar **grupos estáticos de destinatários**. Há uma relação muitos para muitos entre recipients e grupos. Por exemplo, um destinatário pode pertencer a vários grupos e um grupo pode conter vários destinatários. Os grupos podem ser criados manualmente, por meio de uma importação ou pelo direcionamento de delivery. Os grupos são usados com frequência como alvos de delivery. Há um índice exclusivo no campo que representa o nome interno do grupo sName. O grupo está vinculado a uma pasta (a chave é iFolderId. Para obter mais informações, consulte [XtkFolder](#XtkFolder)).

### NmsRcpGrpRel {#NmsRcpGrpRel}

A tabela de relação NmsRcpGrpRel contém apenas os dois campos correspondentes aos identificadores das tabelas vinculadas iRecipientId e iGroupId.

### NmsService {#NmsService}

Esta tabela corresponde à **nms:service** esquema.

No Adobe Campaign, é possível criar e gerenciar assinaturas para serviços de informações (tópicos). A tabela NmsService armazena a definição dos serviços de informações (tópicos) aos quais você oferece aos destinatários a subscrição (um boletim informativo, por exemplo).

Os serviços são entidades semelhantes a grupos (agrupamentos estáticos de recipients), exceto que eles circulam mais informações e permitem um gerenciamento fácil de assinaturas e unsubscriptions por meio de formulários.

Há um índice exclusivo no campo que representa o nome interno do serviço sName. O serviço está vinculado a uma pasta (a chave é iFolderId). Para obter mais informações, consulte [XtkFolder](#XtkFolder)). Finalmente, o campo iType especifica o canal de delivery desse serviço (0 para email, 1 para SMS, 2 para telefone, 3 para correspondência direta e 4 para fax).

### NmsSubscription {#NmsSubscription}

Esta tabela corresponde à **nms:subscription** esquema.

Ele permite gerenciar assinaturas de recipients para serviços de informações.

### NmsSubHisto {#NmsSubHisto}

Esta tabela corresponde à **nms:subHisto** esquema.

Se as assinaturas forem gerenciadas usando formulários web ou a interface do aplicativo, todas as assinaturas e cancelamentos de assinaturas serão historicizados na tabela NmsSubHisto. O campo iAction especifica a ação (0 para unsubscription e 1 para subscription) executada na data armazenada no campo tsDate.

### NmsDelivery {#NmsDelivery}

Esta tabela corresponde à **nms:delivery** esquema.

Cada registro nesta tabela representa um **ação de entrega** ou um **template do delivery**. Ele contém todos os parâmetros necessários para executar deliveries (o target, o conteúdo, etc.). Logs de entrega (transmissão) (NmsBroadLog) e URLs de rastreamento associadas (NmsTrackingUrl) são criados durante a fase de análise (veja abaixo mais detalhes sobre essas duas tabelas).

Há um índice exclusivo no campo que representa o nome interno da entrega ou do cenário sInternalName. O delivery é vinculado a uma pasta de execução (a chave externa é iFolderProcessId. Para obter mais informações, consulte [XtkFolder](#XtkFolder)).

### XtkFolder {#XtkFolder}

Ele contém **todas as pastas na árvore** visível na **Navegação** do console.

As pastas são digitadas: o valor do campo sModel especifica o tipo de dados que pode estar contido na pasta. Esse campo também permite que o console do cliente exiba os dados corretamente com os formulários correspondentes. Os valores possíveis para esse campo são definidos na navTree.

A árvore é gerenciada pelos campos iParentId e iChildCount. O campo sFullName fornece o caminho completo da pasta na árvore. Por fim, há um índice exclusivo no campo que representa o nome interno da pasta sName.

## Entrega e rastreamento {#delivery-and-tracking}

Esse conjunto de tabelas está vinculado à variável **Entrega** módulo, que permite monitorar deliveries e eventuais problemas encontrados quando as mensagens são enviadas. Para obter mais informações, consulte [Monitoramento de deliveries](../../delivery/using/about-delivery-monitoring.md). Para obter mais informações sobre rastreamento, consulte [Rastreamento de mensagens](../../delivery/using/about-message-tracking.md).

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**: esta tabela corresponde aos parâmetros de **nms:broadLogMsg** esquema. É uma extensão da tabela de log de delivery.

## Gerenciamento de campanhas {#campaign-management}

Esse conjunto de tabelas está vinculado à variável **Campanhas de marketing** módulo, que permite definir, otimizar, executar e analisar campanhas de comunicação e marketing. Para obter mais informações, consulte [Sobre campanhas de marketing](../../campaign/using/designing-marketing-campaigns.md).

![](assets/data-model_campaign.png)

* **NmsOperation**: esta tabela corresponde aos parâmetros de **nms:operation** esquema. Ele contém os dados de campanhas de marketing.
* **NmsDeliveryOutline**: esta tabela corresponde aos parâmetros de **nms:deliveryOutline** esquema. Ele contém as propriedades estendidas do delivery (delivery outline).
* **NmsDlvOutlineItem**: esta tabela corresponde aos parâmetros de **nms:dlvOutlineItem** esquema. Ele contém os artigos de um delivery outline.
* **NmsDeliveryCustomization**: esta tabela corresponde aos parâmetros de **nms:deliveryCustomization** esquema. Ele contém os campos de personalização de um delivery.
* **NmsBudget**: esta tabela corresponde aos parâmetros de **nms:budget** esquema. Ele contém os dados de um orçamento em uma campanha, um plano, um programa, uma tarefa e/ou deliveries.
* **NmsDocument**: esta tabela corresponde aos parâmetros de **nms:documento** esquema. Ele contém os documentos de marketing da campanha na forma de arquivos (imagens, arquivos do Excel ou Word etc.)
* **XtkWorkflow**: esta tabela corresponde aos parâmetros de **xtk:workflow** esquema. Ele contém direcionamento de campanha.
* **TarefaNms**: esta tabela corresponde aos parâmetros de **nms:task** esquema. Ela contém a definição de uma tarefa de marketing.
* **NmsAsset**: esta tabela corresponde aos parâmetros de **nms:asset** esquema. Ele contém a definição de um recurso de marketing.

## Consistência de comunicação {#communication-consistency}

Esse conjunto de tabelas está vinculado à variável **Otimização de campanha** módulo, que permite controlar, filtrar e monitorar o envio de deliveries. Para obter mais informações, consulte [Sobre tipologias de campanha](../../campaign-opt/using/about-campaign-typologies.md).

![](assets/data-model_typology.png)

* **NmsTypologyRule**: esta tabela corresponde aos parâmetros de **nms:typologyRule** esquema. Ele contém as regras que se aplicam aos deliveries dependendo das tipologias.
* **TipologiaNms**: esta tabela corresponde aos parâmetros de **nms:tipologia** esquema. Ele contém o conjunto de regras a serem aplicadas aos deliveries que correspondem à tipologia.
* **NmsTypologyRuleRel**: esta tabela corresponde aos parâmetros de **nms:typologyRuleRel** esquema. Ela contém as relações entre tipologias e suas regras.
* **NmsVolumeLine**: esta tabela corresponde aos parâmetros de **nms:volumeLine** esquema. Ele contém o conjunto de linhas de disponibilidade das regras de capacidade.
* **NmsVolumeConsumed**: esta tabela corresponde aos parâmetros de **nms:volumeConsumed** esquema. Ele contém todas as linhas de consumo das regras de capacidade.

## Gestor de resposta {#response-management}

Esse conjunto de tabelas está vinculado à variável **Gestor de Resposta** módulo, que permite medir o sucesso e a lucratividade de campanhas de marketing ou apresentações de oferta para todos os canais de comunicação. Para obter mais informações, consulte [Sobre o gestor de resposta](../../response/using/about-response-manager.md).

![](assets/data-model_response.png)

### NmsRemaHypothesis {#NmsRemaHypothesis}

Este quadro coincide com o quadro **nms:remaHypothesis** esquema. Ele contém a definição da hipótese de mensuração.

Esta tabela contém informações importantes armazenadas em XML, incluindo:

**Contexto de execução (informações armazenadas em XML)**

O contexto de execução preenche as tabelas e os campos a serem considerados para o cálculo da medição, ou seja:
* O esquema de armazenamento do log de reação nms:remaMatchRcp.
* O schema da tabela de transações (compras, por exemplo).
* O schema de consulta, que permite definir a tabela inicial das condições de hipótese.
* Os links para indivíduos, que permitem identificar o indivíduo com base no schema de consulta.
* A data da transação. Esse campo não é obrigatório, mas recomendamos que você o use para restringir o perímetro de cálculo.
* O valor da transação: é um campo opcional para calcular automaticamente os indicadores de receita.

**Perímetro da Hipótese (informações armazenadas em XML)**

O perímetro da hipótese consiste na filtragem da hipótese com base na tabela do schema de consulta.

**Script de sobrecarga da hipótese (informações armazenadas em XML)**

O script de sobrecarga da hipótese é um código JavaScript que permite sobrecarregar o conteúdo da hipótese durante a execução.

**Indicadores de medição**

Os seguintes indicadores são atualizados automaticamente durante a execução da hipótese:

* Número de reações: **iTransaction**. Número de linhas na tabela de logs de reação.
* Número de contatos: **iContactReacted**. Número distinto de contatos direcionados na hipótese.
* Contagem de grupos de controle: **iProofReacted**. Número distinto de contatos de grupos de controle direcionados na hipótese.
* Taxa de resposta de contatados: **dContactReactedRate**. Taxa de resposta dos contatos direcionados na hipótese.
* Taxa de resposta do grupo de controle: **dProofReactedRate**. Taxa de resposta do grupo de controle de hipóteses.
* Receita total da população contatada: **dContactReactedTotalAmount**. Receita total dos contatos direcionados na hipótese.
* Receita média do grupo de controle: **dContactReactedAvgAmount**. Receita média dos contatos do grupo de controle direcionado na hipótese.
* Receita total do grupo de controle: **dProofReactedTotalAmount**. Receita total do grupo de controle de hipóteses.
* Receita média do grupo de controle: **dProofReactedAvgAmount**. Receita média do grupo de controle de hipóteses.
* Margem total por contato: **dContactReactedTotalMargin**. Margem total por contato direcionado na hipótese.
* Margem média por contato: **dContactReactedAvgMargin**. Margem média por contato direcionado na hipótese.
* Margem total do grupo de controle: **dProofReactedTotalMargin**. Margem total do grupo de controle direcionado na hipótese.
* Margem média do grupo de controle: **dProofReactedAvgMargin**. Margem média do grupo de controle direcionado na hipótese.
* Receita adicional: **ValorAdicional**. (Receita média do contato - Receita média do grupo de controle) * Número de contatos.
* Margem adicional: **MargemAdicional**. (Margem média do contato - Margem média do grupo de controle) / Número de contatos.
* Custo médio por contato (expressão SQL). Custo de entrega calculado/Número de contatos.
* ROI (expressão SQL). Custo de entrega calculado/margem total de contatos.
* ROI efetivo (expressão SQL). Custo de entrega calculado/margem adicional.
* Significância: **iSignificativamente** (expressão SQL). Contém valores de 0 a 3 dependendo do significado da campanha.

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

Esta tabela corresponde à **nms:remaMatchRcp** esquema.

Ele contém um registro que representa a reação de um indivíduo a uma determinada hipótese. Esses registros foram criados durante a execução da hipótese.

## Simulação e entrega {#simulation-and-delivery}

Esse conjunto de tabelas está vinculado à variável **Simulação** módulo, que permite testar a distribuição de ofertas pertencentes a uma categoria ou um ambiente antes de enviar sua proposta para os recipients. Para obter mais informações, consulte [Sobre a simulação de ofertas](../../interaction/using/about-offers-simulation.md).

![](assets/data-model_simulation.png)

* **NmsSimulation**: esta tabela corresponde aos parâmetros de **nms:simulação** esquema. Ele representa uma simulação de um conjunto de deliveries ou ofertas em uma determinada população.
* **NmsDlvSimulationRel**: esta tabela corresponde aos parâmetros de **nms:dlvSimulationRel** esquema. Ele contém a lista de deliveries considerados na simulação. O escopo da simulação é armazenado em XML.
* **NmsOfferSimulationRel**: esta tabela corresponde aos parâmetros de **nms:offerSimulationRel** esquema. Ele permite vincular uma simulação a uma oferta.

## Módulo de interação {#interaction-module}

Esse conjunto de tabelas está vinculado à variável **Interação** módulo, que permite responder em tempo real durante uma interação com um determinado contato, tornando-o uma única ou várias ofertas adaptadas. Para obter mais informações, consulte [Interação e gestão de ofertas](../../interaction/using/interaction-and-offer-management.md).

* **NmsOffer**: esta tabela corresponde aos parâmetros de **nms:offer** esquema. Ele contém a definição de cada oferta de marketing.
* **NmsPropositionRcp**: esta tabela corresponde aos parâmetros de **nms:propositionRcp** esquema. Ele contém o log entre canais de apresentações de marketing enviadas a cada indivíduo. O registro é criado quando uma proposta é preparada ou efetivamente feita a um indivíduo.
* **NmsOfferSpace**: esta tabela corresponde aos parâmetros de **nms:offerSpace** esquema. Ele contém a definição de locais em que as apresentações são feitas.
* **NmsOfferContext**: esta tabela corresponde aos parâmetros de **nms:offerContext** esquema. Contém critérios adicionais sobre a aplicabilidade da proposta, bem como a definição da fórmula de cálculo do peso.
* **NmsOfferView**: esta tabela corresponde aos parâmetros de **nms:offerView**. Ele contém as representações de oferta.
* **NmsOfferCategory**: esta tabela corresponde aos parâmetros de **nms:offerCategory**. Ele contém as categorias de oferta.
* **NmsOfferEnv**: esta tabela corresponde aos parâmetros de **nms:offerEnv**. Ele contém os ambientes de oferta.

## Módulo do Centro de mensagens {#message-center-module}

O conjunto de tabelas a seguir está vinculado à variável **Mensagens transacionais** (Centro de mensagens) módulo, que permite gerenciar comunicações individuais e exclusivas enviadas a um usuário e geradas a partir de eventos acionados de sistemas de informação. Para obter mais informações, consulte [Sobre mensagens transacionais](../../message-center/using/about-transactional-messaging.md).

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

Esta tabela corresponde à **nms:rtEvent** esquema. Ele contém uma definição de eventos em tempo real.

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

Esta tabela corresponde à **nms:batchEvent** esquema. Ela contém a definição de eventos por lote.

<!--## Microsites Module {#microsites-module}

This set of tables is linked to the **Web applications** functionality, which allows to create and publish dynamic and interactive web applications with data from the database and content adapted to the rights of the connected user. For more on this, see [About web applications](../../web/using/about-web-applications.md).

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: This table matches the **nms:trackingUrl** schema.

* **NmsPurl**: This table matches the **nms:purl** schema.-->

## Módulo NMAC {#nmac-module}

Esse conjunto de tabelas está vinculado à variável **Canal de aplicativo móvel**, que permite enviar notificações personalizadas para terminais iOS e Android por meio de aplicativos. Para obter mais informações, consulte [Sobre o canal de aplicativo móvel](../../delivery/using/about-mobile-app-channel.md).

* **NmsMobileApp**: esta tabela corresponde aos parâmetros de **nms:mobileApp** esquema. Ele contém os aplicativos móveis definidos no Adobe Campaign.
* **NmsAppSubscription**: esta tabela corresponde aos parâmetros de **nms:appSubscription** esquema. Ele contém as informações dos assinantes referentes a um ou mais aplicativos.
* **NmsAppSubscriptionRcp**: esta tabela corresponde aos parâmetros de **nms:appSubscriptionRcp** esquema. Ela permite vincular visitantes que se inscreveram em um aplicativo à tabela de recipients.
* **NmsExcludeLogAppSubRcp**: esta tabela corresponde aos parâmetros de **nms:excludeLogAppSubRcp** esquema.
* **NmsTrackingLogAppSubRcp**: esta tabela corresponde aos parâmetros de **nms:trackingLogAppSubRcp** esquema.
* **NmsBroadLogAppSubRcp**: esta tabela corresponde aos parâmetros de **nms:broadLogAppSubRcp** esquema.

## Módulo de marketing social {#social-marketing-module}

Esse conjunto de tabelas está vinculado à variável **Gerenciamento de redes sociais** módulo, que permite interagir com clientes atuais e potenciais via Facebook e Twitter. Para obter mais informações, consulte [Sobre marketing social](../../social/using/about-social-marketing.md).

![](assets/data-model_social.png)

* **NmsVisitor**: esta tabela corresponde aos parâmetros de **nms:visitor** esquema. Ele contém informações sobre visitantes.
* **NmsVisitorSub**: esta tabela corresponde aos parâmetros de **nms:visitorSub** esquema. Ela permite vincular um visitante aos serviços aos quais ele se inscreveu (Twitter ou Facebook).
* **NmsFriendShipRel**: esta tabela corresponde aos parâmetros de **nms:friendshipRel** esquema. Ela permite vincular visitantes com seus amigos no contexto do serviço do Facebook.
* **NmsVisitorInterestRel**: esta tabela corresponde aos parâmetros de **nms:visitorInterestRel** esquema. Ela permite vincular visitantes e seus interesses.
* **NmsInterest**: esta tabela corresponde aos parâmetros de **nms:interest** esquema. Ele contém a lista de interesses de cada visitante.
