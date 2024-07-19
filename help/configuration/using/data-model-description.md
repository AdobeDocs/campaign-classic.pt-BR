---
product: campaign
title: Descrição do modelo de dados do Adobe Campaign Classic
description: Este documento descreve o modelo de dados do Adobe Campaign
feature: Data Model
role: Data Engineer, Developer
exl-id: fc0fd23c-f9ea-4e30-b47b-a84143d882ca
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '2399'
ht-degree: 1%

---

# Descrição do modelo de dados do Campaign{#data-model-description}


O Adobe Campaign vem com um modelo de dados predefinido. Esta seção fornece alguns detalhes sobre as tabelas integradas do modelo de dados do Adobe Campaign e suas interações.

Para acessar a descrição de cada tabela, vá para **[!UICONTROL Admin > Configuration > Data schemas]**, selecione um recurso na lista e clique na guia **[!UICONTROL Documentation]**.

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>A estrutura física e lógica dos dados transportados no aplicativo é descrita em XML. Ela obedece a uma gramática específica do Adobe Campaign, chamada de schema. Para obter mais informações sobre esquemas do Adobe Campaign, leia [esta seção](../../configuration/using/about-schema-reference.md).

## Descrição dos principais quadros {#description-main-tables}

O Adobe Campaign depende de um banco de dados relacional contendo tabelas vinculadas.

O diagrama a seguir mostra as associações entre as principais tabelas de negócios do modelo de dados do Adobe Campaign com os principais campos de cada um.

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

O modelo de dados predefinido do Adobe Campaign inclui as principais tabelas listadas abaixo.

### NmsRecipient {#NmsRecipient}

Esta tabela corresponde ao esquema **nms:recipient**.

É a tabela padrão usada para os **destinatários de entregas**. Como resultado, contém as informações necessárias para deliveries por meio dos vários canais:

* sEmail: endereço de email.
* iEmailFormat: formato preferido para emails (1 para Texto, 2 para HTML e 0 se indefinido).
* sAddress1, sAddress2, sAddress3, sAddress4, sZipCode, sCity são usados para criar o endereço postal (de acordo com o padrão XPZ 10-011 AFNOR de maio de 1997).
* sPhone, sMobilePhone, sFax contêm os números de telefone, telefone celular e fax, respectivamente.
* iBlackList é o sinalizador de recusa padrão usado para os perfis (1 significa &quot;cancelado&quot;, caso contrário, 0).

O campo iFolderId é a chave externa que vincula o recipient à sua pasta de execução. Para obter mais informações, consulte [XtkFolder](#XtkFolder).

O campo sCountryCode é o código ISO 3166-1 Alpha 2 (2 caracteres) do país associado ao recipient. Na verdade, esse campo é uma chave estrangeira na tabela de referência de país (NmsCountry), que contém os rótulos de país e outros dados de código de país. Se o país não estiver preenchido, o valor &quot;XX&quot; será armazenado (e usado no lugar de um registro de ID zero).

Para obter mais informações sobre a tabela Recipient, consulte [esta seção](../../configuration/using/about-data-model.md#default-recipient-table).

### NmsGroup {#NmsGroup}

Esta tabela corresponde ao esquema **nms:group**.

Ela permite criar **grupos estáticos de destinatários**. Há uma relação muitos para muitos entre recipients e grupos. Por exemplo, um destinatário pode pertencer a vários grupos e um grupo pode conter vários destinatários. Os grupos podem ser criados manualmente, por meio de uma importação ou pelo direcionamento de delivery. Os grupos são usados com frequência como alvos de delivery. Há um índice exclusivo no campo que representa o nome interno do grupo sName. O grupo está vinculado a uma pasta (a chave é iFolderId. Para obter mais informações, consulte [XtkFolder](#XtkFolder)).

### NmsRcpGrpRel {#NmsRcpGrpRel}

A tabela de relação NmsRcpGrpRel contém apenas os dois campos correspondentes aos identificadores das tabelas vinculadas iRecipientId e iGroupId.

### NmsService {#NmsService}

Esta tabela corresponde ao esquema **nms:service**.

No Adobe Campaign, é possível criar e gerenciar assinaturas para serviços de informações (tópicos). A tabela NmsService armazena a definição dos serviços de informações (tópicos) aos quais você oferece aos destinatários a subscrição (um boletim informativo, por exemplo).

Os serviços são entidades semelhantes a grupos (agrupamentos estáticos de recipients), exceto que eles circulam mais informações e permitem um gerenciamento fácil de assinaturas e unsubscriptions por meio de formulários.

Há um índice exclusivo no campo que representa o nome interno do serviço sName. O serviço está vinculado a uma pasta (a chave é iFolderId). Para obter mais informações, consulte [XtkFolder](#XtkFolder)). Finalmente, o campo iType especifica o canal de delivery desse serviço (0 para email, 1 para SMS, 2 para telefone, 3 para correspondência direta e 4 para fax).

### NmsSubscription {#NmsSubscription}

Esta tabela corresponde ao esquema **nms:subscription**.

Ele permite gerenciar assinaturas de recipients para serviços de informações.

### NmsSubHisto {#NmsSubHisto}

Esta tabela corresponde ao esquema **nms:subHisto**.

Se as assinaturas forem gerenciadas usando formulários web ou a interface do aplicativo, todas as assinaturas e cancelamentos de assinaturas serão historicizados na tabela NmsSubHisto. O campo iAction especifica a ação (0 para unsubscription e 1 para subscription) executada na data armazenada no campo tsDate.

### NmsDelivery {#NmsDelivery}

Esta tabela corresponde ao esquema **nms:delivery**.

Cada registro nesta tabela representa uma **ação de entrega** ou um **modelo de entrega**. Ele contém todos os parâmetros necessários para executar deliveries (o target, o conteúdo, etc.). Logs de entrega (transmissão) (NmsBroadLog) e URLs de rastreamento associadas (NmsTrackingUrl) são criados durante a fase de análise (veja abaixo mais detalhes sobre essas duas tabelas).

Há um índice exclusivo no campo que representa o nome interno da entrega ou do cenário sInternalName. O delivery é vinculado a uma pasta de execução (a chave externa é iFolderProcessId. Para obter mais informações, consulte [XtkFolder](#XtkFolder)).

### XtkFolder {#XtkFolder}

Ele contém **todas as pastas da árvore** visíveis na guia **Navegação** do console.

As pastas são digitadas: o valor do campo sModel especifica o tipo de dados que pode estar contido na pasta. Esse campo também permite que o console do cliente exiba os dados corretamente com os formulários correspondentes. Os valores possíveis para esse campo são definidos na navTree.

A árvore é gerenciada pelos campos iParentId e iChildCount. O campo sFullName fornece o caminho completo da pasta na árvore. Por fim, há um índice exclusivo no campo que representa o nome interno da pasta sName.

## Entrega e rastreamento {#delivery-and-tracking}

Este conjunto de tabelas está vinculado ao módulo **Delivery**, que permite monitorar entregas e eventuais problemas encontrados quando as mensagens são enviadas. Para obter mais informações, consulte [Monitoramento de deliveries](../../delivery/using/about-delivery-monitoring.md). Para obter mais informações sobre rastreamento, consulte [Mensagens de rastreamento](../../delivery/using/about-message-tracking.md).

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**: esta tabela corresponde ao esquema **nms:broadLogMsg**. É uma extensão da tabela de log de delivery.

## Gerenciamento de campanhas {#campaign-management}

Este conjunto de tabelas está vinculado ao módulo **Campanhas de marketing**, que permite definir, otimizar, executar e analisar campanhas de comunicação e marketing. Para obter mais informações, consulte [Sobre campanhas de marketing](../../campaign/using/designing-marketing-campaigns.md).

![](assets/data-model_campaign.png)

* **NmsOperation**: esta tabela corresponde ao esquema **nms:operation**. Ele contém os dados de campanhas de marketing.
* **NmsDeliveryOutline**: esta tabela corresponde ao esquema **nms:deliveryOutline**. Ele contém as propriedades estendidas do delivery (delivery outline).
* **NmsDlvOutlineItem**: esta tabela corresponde ao esquema **nms:dlvOutlineItem**. Ele contém os artigos de um delivery outline.
* **NmsDeliveryCustomization**: esta tabela corresponde ao esquema **nms:deliveryCustomization**. Ele contém os campos de personalização de um delivery.
* **NmsBudget**: esta tabela corresponde ao esquema **nms:budget**. Ele contém os dados de um orçamento em uma campanha, um plano, um programa, uma tarefa e/ou deliveries.
* **NmsDocument**: esta tabela corresponde ao esquema **nms:document**. Ele contém os documentos de marketing da campanha na forma de arquivos (imagens, arquivos do Excel ou Word etc.)
* **XtkWorkflow**: esta tabela corresponde ao esquema **xtk:workflow**. Ele contém direcionamento de campanha.
* **NmsTask**: esta tabela corresponde ao esquema **nms:task**. Ela contém a definição de uma tarefa de marketing.
* **NmsAsset**: esta tabela corresponde ao esquema **nms:asset**. Ele contém a definição de um recurso de marketing.

## Consistência de comunicação {#communication-consistency}

Este conjunto de tabelas está vinculado ao módulo **Otimização de Campanha**, que permite controlar, filtrar e monitorar o envio de entregas. Para obter mais informações, consulte [Sobre tipologias da campanha](../../campaign-opt/using/about-campaign-typologies.md).

![](assets/data-model_typology.png)

* **NmsTypologyRule**: esta tabela corresponde ao esquema **nms:typologyRule**. Ele contém as regras que se aplicam aos deliveries dependendo das tipologias.
* **NmsTypology**: esta tabela corresponde ao esquema **nms:typology**. Ele contém o conjunto de regras a serem aplicadas aos deliveries que correspondem à tipologia.
* **NmsTypologyRuleRel**: esta tabela corresponde ao esquema **nms:typologyRuleRel**. Ela contém as relações entre tipologias e suas regras.
* **NmsVolumeLine**: esta tabela corresponde ao esquema **nms:volumeLine**. Ele contém o conjunto de linhas de disponibilidade das regras de capacidade.
* **NmsVolumeConsumed**: esta tabela corresponde ao esquema **nms:volumeConsumed**. Ele contém todas as linhas de consumo das regras de capacidade.

## Gerenciamento de resposta {#response-management}

Este conjunto de tabelas está vinculado ao módulo **Gestor de Resposta**, que permite medir o sucesso e a lucratividade de campanhas de marketing ou propostas de oferta para todos os canais de comunicação. Para obter mais informações, consulte [Sobre o gestor de resposta](../../response/using/about-response-manager.md).

![](assets/data-model_response.png)

### NmsRemaHypothesis {#NmsRemaHypothesis}

Esta tabela coincide com o esquema **nms:remaHypothesis**. Ele contém a definição da hipótese de mensuração.

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

**Script de sobrecarga de hipótese (informações armazenadas em XML)**

O script de sobrecarga da hipótese é um código JavaScript que permite sobrecarregar o conteúdo da hipótese durante a execução.

**Indicadores de medição**

Os seguintes indicadores são atualizados automaticamente durante a execução da hipótese:

* Número de reações: **iTransaction**. Número de linhas na tabela de logs de reação.
* Número de contatos: **iContactReacted**. Número distinto de contatos direcionados na hipótese.
* Contagem de grupos de controle: **iProofReacted**. Número distinto de contatos de grupos de controle direcionados na hipótese.
* Taxa de resposta de contato: **dContactReactedRate**. Taxa de resposta dos contatos direcionados na hipótese.
* Taxa de resposta do grupo de controle: **dProofReactedRate**. Taxa de resposta do grupo de controle de hipóteses.
* Receita total da população contatada: **dContactReactedTotalAmount**. Receita total dos contatos direcionados na hipótese.
* Receita média do grupo de controle: **dContactReactedAvgAmount**. Receita média dos contatos do grupo de controle direcionado na hipótese.
* Receita total do grupo de controle: **dProofReactedTotalAmount**. Receita total do grupo de controle de hipóteses.
* Receita média do grupo de controle: **dProofReactedAvgAmount**. Receita média do grupo de controle de hipóteses.
* Margem total por contato: **dContactReactedTotalMargin**. Margem total por contato direcionado na hipótese.
* Margem média por contato: **dContactReactedAvgMargin**. Margem média por contato direcionado na hipótese.
* Margem total do grupo de controle: **dProofReactedTotalMargin**. Margem total do grupo de controle direcionado na hipótese.
* Margem média do grupo de controle: **dProofReactedAvgMargin**. Margem média do grupo de controle direcionado na hipótese.
* Receita adicional: **dAdditionalAmount**. (Receita média do contato - Receita média do grupo de controle) * Número de contatos.
* Margem adicional: **dAdditionalMargin**. (Margem média do contato - Margem média do grupo de controle) / Número de contatos.
* Custo médio por contato (expressão SQL). Custo de entrega calculado/Número de contatos.
* ROI (expressão SQL). Custo de entrega calculado/margem total de contatos.
* ROI efetivo (expressão SQL). Custo de entrega calculado/margem adicional.
* Significance: **iSignificativy** (expressão SQL). Contém valores de 0 a 3 dependendo do significado da campanha.

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

Esta tabela corresponde ao esquema **nms:remaMatchRcp**.

Ele contém um registro que representa a reação de um indivíduo a uma determinada hipótese. Esses registros foram criados durante a execução da hipótese.

## Simulação e entrega {#simulation-and-delivery}

Este conjunto de tabelas está vinculado ao módulo **Simulation**, que permite testar a distribuição de ofertas pertencentes a uma categoria ou um ambiente antes de enviar sua proposta para os recipients. Para obter mais informações, consulte [Sobre a simulação de ofertas](../../interaction/using/about-offers-simulation.md).

![](assets/data-model_simulation.png)

* **NmsSimulation**: esta tabela corresponde ao esquema **nms:simulation**. Ele representa uma simulação de um conjunto de deliveries ou ofertas em uma determinada população.
* **NmsDlvSimulationRel**: esta tabela corresponde ao esquema **nms:dlvSimulationRel**. Ele contém a lista de deliveries considerados na simulação. O escopo da simulação é armazenado em XML.
* **NmsOfferSimulationRel**: esta tabela corresponde ao esquema **nms:offerSimulationRel**. Ele permite vincular uma simulação a uma oferta.

## Módulo de interação {#interaction-module}

Este conjunto de tabelas está vinculado ao módulo **Interaction**, que permite responder em tempo real durante uma interação com um determinado contato, tornando-o uma única ou várias ofertas adaptadas. Para obter mais informações, consulte [Interação e gerenciamento de ofertas](../../interaction/using/interaction-and-offer-management.md).

* **NmsOffer**: esta tabela corresponde ao esquema **nms:offer**. Ele contém a definição de cada oferta de marketing.
* **NmsPropositionRcp**: esta tabela corresponde ao esquema **nms:propositionRcp**. Ele contém o log entre canais de apresentações de marketing enviadas a cada indivíduo. O registro é criado quando uma proposta é preparada ou efetivamente feita a um indivíduo.
* **NmsOfferSpace**: esta tabela corresponde ao esquema **nms:offerSpace**. Ele contém a definição de locais em que as apresentações são feitas.
* **NmsOfferContext**: esta tabela corresponde ao esquema **nms:offerContext**. Contém critérios adicionais sobre a aplicabilidade da proposta, bem como a definição da fórmula de cálculo do peso.
* **NmsOfferView**: esta tabela corresponde a **nms:offerView**. Ele contém as representações de oferta.
* **NmsOfferCategory**: esta tabela corresponde a **nms:offerCategory**. Ele contém as categorias de oferta.
* **NmsOfferEnv**: esta tabela corresponde a **nms:offerEnv**. Ele contém os ambientes de oferta.

## Módulo do Centro de mensagens {#message-center-module}

O conjunto de tabelas a seguir está vinculado ao módulo **Mensagens transacionais** (Centro de Mensagens), que permite gerenciar comunicações individuais e exclusivas enviadas a um usuário e geradas a partir de eventos acionados de sistemas de informações. Para obter mais informações, consulte [Sobre mensagens transacionais](../../message-center/using/about-transactional-messaging.md).

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

Esta tabela corresponde ao esquema **nms:rtEvent**. Ele contém uma definição de eventos em tempo real.

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

Esta tabela corresponde ao esquema **nms:batchEvent**. Ela contém a definição de eventos por lote.

<!--## Microsites Module {#microsites-module}

This set of tables is linked to the **Web applications** functionality, which allows to create and publish dynamic and interactive web applications with data from the database and content adapted to the rights of the connected user. For more on this, see [About web applications](../../web/using/about-web-applications.md).

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: This table matches the **nms:trackingUrl** schema.

* **NmsPurl**: This table matches the **nms:purl** schema.-->

## Módulo NMAC {#nmac-module}

Este conjunto de tabelas está vinculado ao **Canal de Aplicativo Móvel**, que permite enviar notificações personalizadas para terminais iOS e Android por meio de aplicativos. Para obter mais informações, consulte [Sobre o canal de aplicativo móvel](../../delivery/using/about-mobile-app-channel.md).

* **NmsMobileApp**: esta tabela corresponde ao esquema **nms:mobileApp**. Ele contém os aplicativos móveis definidos no Adobe Campaign.
* **NmsAppSubscription**: esta tabela corresponde ao esquema **nms:appSubscription**. Ele contém as informações dos assinantes referentes a um ou mais aplicativos.
* **NmsAppSubscriptionRcp**: esta tabela corresponde ao esquema **nms:appSubscriptionRcp**. Ela permite vincular visitantes que se inscreveram em um aplicativo à tabela de recipients.
* **NmsExcludeLogAppSubRcp**: esta tabela corresponde ao esquema **nms:excludeLogAppSubRcp**.
* **NmsTrackingLogAppSubRcp**: esta tabela corresponde ao esquema **nms:trackingLogAppSubRcp**.
* **NmsBroadLogAppSubRcp**: esta tabela corresponde ao esquema **nms:broadLogAppSubRcp**.

## Módulo de marketing social {#social-marketing-module}

Este conjunto de tabelas está vinculado ao módulo **Gerenciamento de redes sociais**, que permite interagir com clientes atuais e potenciais via Facebook e X (anteriormente conhecido como Twitter). Para obter mais informações, consulte [Sobre marketing social](../../social/using/about-social-marketing.md).

![](assets/data-model_social.png)

* **NmsVisitor**: esta tabela corresponde ao esquema **nms:visitor**. Ele contém informações sobre visitantes.
* **NmsVisitorSub**: esta tabela corresponde ao esquema **nms:visitorSub**. Ela permite vincular um visitante aos serviços aos quais ele se inscreveu (X ou Facebook).
* **NmsFriendShipRel**: esta tabela corresponde ao esquema **nms:friendshipRel**. Ela permite vincular visitantes com seus amigos no contexto do serviço do Facebook.
* **NmsVisitorInterestRel**: esta tabela corresponde ao esquema **nms:visitorInterestRel**. Ela permite vincular visitantes e seus interesses.
* **NmsInterest**: esta tabela corresponde ao esquema **nms:interest**. Ele contém a lista de interesses de cada visitante.
