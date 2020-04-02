---
title: Descrição do modelo de dados Adobe Campaign Classic
description: Este documento descreve o modelo de dados Adobe Campaign Classic.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 707e16e9e493e175c70af606bf4568a9127cedb2

---


# Descrição do modelo de dados de Campanha{#data-model-description}

O Adobe Campaign vem com um modelo de dados predefinido. Esta seção fornece alguns detalhes sobre as tabelas incorporadas do modelo de dados Adobe Campaign e suas interações.

Para acessar a descrição de cada tabela, vá até **[!UICONTROL Admin > Configuration > Data schemas]**, selecione um recurso da lista e clique na **[!UICONTROL Documentation]** guia.

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>A estrutura física e lógica dos dados transportados no aplicativo é descrita em XML. Ela obedece a uma gramática específica do Adobe Campaign, chamada de schema. For more on Adobe Campaign schemas, read out this [section](../../configuration/using/about-schema-reference.md).

## Descrição dos quadros principais {#description-main-tables}

O Adobe Campaign depende de um banco de dados relacional que contém tabelas vinculadas.

O diagrama a seguir mostra as junções entre as principais tabelas de negócios do modelo de dados do Adobe Campaign com os campos principais de cada um.

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

O modelo de dados de Adobe Campaign predefinido inclui as principais tabelas listadas abaixo.

### NmsRecipient {#NmsRecipient}

Esta tabela corresponde ao schema **nms:recipient** .

É a tabela padrão usada para os **recipient de delivery**. Como resultado, contém as informações necessárias para os delivery através dos vários canais:

* sEmail: endereço de email.
* iEmailFormat: formato preferencial para emails (1 para Texto, 2 para HTML e 0 se não estiver definido).
* sAddress1, sAddress2, sAddress3, sAddress4, sZipCode, sCity são usados para criar o endereço postal (em conformidade com o padrão AFNOR XPZ 10-011 de maio de 1997).
* sPhone, sMobilePhone, sFax contêm os números de telefone, telefone celular e fax, respectivamente.
* iBlackList é o sinalizador de opção de não participação padrão usado para os perfis (1 significa &quot;não inscrito&quot;, 0 caso contrário).

O campo iFolderId é a chave estrangeira que vincula o recipient à pasta de execução. For more on this, see [XtkFolder](#XtkFolder).

O campo sCountryCode é o código ISO 3166-1 Alpha 2 (2 caracteres) do país associado ao recipient. Este campo é, na verdade, uma chave estrangeira na tabela de referência do país (NmsCountry), que contém as etiquetas do país e outros dados de código do país. Se o país não for preenchido, o valor &#39;XX&#39; será armazenado (e usado no lugar de um registro de ID zero).

Para obter mais informações sobre a tabela de Recipient, consulte esta [seção](../../configuration/using/about-data-model.md#default-recipient-table).

### NmsGroup {#NmsGroup}

Essa tabela corresponde ao schema **nms:group** .

Ele permite que você crie grupos **estáticos de recipient**. Há uma relação muitas para muitas entre recipient e grupos. Por exemplo, um recipient pode pertencer a vários grupos e um pode conter vários recipient. Os grupos podem ser criados manualmente, por meio de uma importação ou direcionamento de delivery. Os grupos são frequentemente usados como públicos alvos de delivery. Há um índice exclusivo no campo que representa o nome interno do grupo sName. O grupo está vinculado a uma pasta (a chave é iFolderId. For more on this, see [XtkFolder](#XtkFolder)).

### NmsRcpGrpRel {#NmsRcpGrpRel}

A tabela de relacionamento NmsRcpGrpRel contém apenas os dois campos correspondentes aos identificadores das tabelas vinculadas iRecipientId e iGroupId.

### NmsService {#NmsService}

Esta tabela corresponde ao schema **nms:service** .

Os serviços são entidades semelhantes a grupos (agrupamentos de recipient estáticos), exceto que circulam mais informações e permitem o gerenciamento fácil de subscrições e unsubscription por meio de formulários.

Há um índice exclusivo no campo que representa o nome interno do serviço sName. O serviço está vinculado a uma pasta (a chave é iFolderId. For more on this, see [XtkFolder](#XtkFolder)). Por fim, o campo iType especifica o canal do delivery desse serviço (0 para email, 1 para SMS, 2 para telefone, 3 para mala direta e 4 para fax).

### NmsSubscription {#NmsSubscription}

Esta tabela corresponde ao schema **nms:subscrição** .

Ele permite que você gerencie subscrições de recipient para serviços de informação.

### NmsSubHisto {#NmsSubHisto}

Esta tabela corresponde ao schema **nms:subHisto** .

Se as subscrições forem gerenciadas usando formulários da Web ou a interface do aplicativo, todas as assinaturas e unsubscription serão historizadas na tabela NmsSubHisto. O campo iAction especifica a ação (0 para unsubscription e 1 para subscrição) executada na data armazenada no campo tsDate.

### NmsDelivery {#NmsDelivery}

Esta tabela corresponde ao schema **nms:delivery** .

Cada registro nesta tabela representa uma ação **de** delivery ou um **template do delivery**. Ele contém todos os parâmetros necessários para executar delivery (o público alvo, o conteúdo etc.). Os registros de Delivery (difusão) (NmsBroadLog) e os URLs de rastreamento associados (NmsTrackingUrl) são criados durante a fase de análise (consulte abaixo para obter mais detalhes sobre essas tabelas).

Há um índice exclusivo no campo que representa o nome interno do delivery ou cenário sInternalName. O delivery está vinculado a uma pasta de execução (a chave estrangeira é iFolderProcessId. For more on this, see [XtkFolder](#XtkFolder)).

### XtkFolder {#XtkFolder}

Ele contém **todas as pastas na árvore** visíveis na guia **Navegação** do console.

As pastas são digitadas: o valor do campo sModel especifica o tipo de dados que pode ser contido na pasta. Esse campo também permite que o console do cliente exiba os dados corretamente com os formulários correspondentes. Os valores possíveis para esse campo são definidos na navTree.

A árvore é gerenciada pelos campos iParentId e iChildCount. O campo sFullName fornece o caminho completo da pasta na árvore. Finalmente, há um índice exclusivo no campo que representa o nome interno da pasta sName.

## Delivery e rastreamento {#delivery-and-tracking}

Esse conjunto de tabelas está vinculado ao módulo **Delivery** , que permite monitorar delivery e possíveis problemas encontrados quando as mensagens são enviadas. Para obter mais informações, consulte [Monitoramento de delivery](../../delivery/using/monitoring-a-delivery.md). Para obter mais informações sobre o rastreamento, consulte [Rastreamento de mensagens](../../delivery/using/about-message-tracking.md).

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**: Esta tabela corresponde ao schema **nms:wideLogMsg** . É uma extensão da tabela de log de delivery.

## Gestão de campanha {#campaign-management}

Esse conjunto de tabelas está vinculado ao módulo **Marketing campanha** , que permite definir, otimizar, executar e analisar campanhas de comunicação e marketing. Para obter mais informações, consulte [Sobre campanhas](../../campaign/using/designing-marketing-campaigns.md)de marketing.

![](assets/data-model_campaign.png)

* **NmsOperation**: Esta tabela corresponde ao schema **nms:operation** . Ele contém os dados das campanhas de marketing.
* **NmsDeliveryOutline**: Esta tabela corresponde ao schema **nms:deliveryOutline** . Ele contém as propriedades estendidas do delivery (delivery outline).
* **NmsDlvOutlineItem**: Esta tabela corresponde ao schema **nms:dlvOutlineItem** . Ele contém os artigos de um delivery outline.
* **NmsDeliveryCustomization**: Esta tabela corresponde ao schema **nms:deliveryCustomization** . Ele contém os campos de personalização de um delivery.
* **NmsBudget**: Esta tabela corresponde ao schema **nms:budget** . Ele contém os dados de um orçamento em uma campanha, um plano, um programa, uma tarefa e/ou delivery.
* **NmsDocument**: Esta tabela corresponde ao schema **nms:documento** . Ele contém os documentos de marketing da campanha na forma de arquivos (imagens, arquivos excel ou word etc.)
* **XtkWorkflow**: Esta tabela corresponde ao schema **xtk:workflow** . Ele contém direcionamento de campanha.
* **NmsTask**: Esta tabela corresponde ao schema **nms:tarefa** . Contém a definição de uma tarefa de marketing.
* **NmsAsset**: Essa tabela corresponde ao schema **nms:asset** . Ele contém a definição de um recurso de marketing.

## Consistência da comunicação {#communication-consistency}

Esse conjunto de tabelas está vinculado ao módulo **Otimização de campanha** , que permite controlar, filtrar e monitorar o envio de delivery. Para obter mais informações, consulte [Sobre tipologias de campanha](../../campaign/using/about-campaign-typologies.md).

![](assets/data-model_typology.png)

* **NmsTypologyRule**: Essa tabela corresponde ao schema **nms:typologyRule** . Ele contém as regras que se aplicam aos delivery dependendo das tipologias.
* **NmsTypology**: Essa tabela corresponde ao schema **nms:typology** . Ele contém o conjunto de regras a ser aplicado a delivery que correspondem à tipologia.
* **NmsTypologyRuleRel**: Essa tabela corresponde ao schema **nms:typologyRuleRel** . Ele contém as relações entre as tipologias e suas regras.
* **NmsVolumeLine**: Esta tabela corresponde ao schema **nms:volumeLine** . Ele contém o conjunto de linhas de disponibilidade das regras de capacidade.
* **NmsVolumeConsumed**: Esta tabela corresponde ao schema **nms:volumeConsumed** . Contém todas as linhas de consumo das regras de capacidade.

## Gerenciamento de respostas {#response-management}

Esse conjunto de tabelas está vinculado ao módulo **Gestor de resposta** , que permite medir o sucesso e a lucratividade das campanhas de marketing ou apresentações da oferta para todos os canais de comunicação. Para obter mais informações, consulte [Sobre o gerenciador](../../campaign/using/about-response-manager.md)de respostas.

![](assets/data-model_response.png)

### NmsRemaHipótese {#NmsRemaHypothesis}

Esta tabela coincide com o schema **nms:remaHypotese** . Contém a definição da hipótese de medida.

Esta tabela contém informações importantes armazenadas em XML, incluindo:

**Contexto de execução (informações armazenadas em XML)**

O contexto de execução preenche as tabelas e os campos a serem considerados para o cálculo da medição, a saber:
* O schema de armazenamento de log de reação nms:remaMatchRcp.
* O schema da tabela de transações (compra, por exemplo).
* O schema de consulta, que permite definir a tabela de start das condições de hipótese.
* Os links para indivíduos, que permitem identificar o indivíduo com base no schema de consulta.
* A data da transação. Este campo não é obrigatório, mas recomendamos que você o use para restringir o perímetro de cálculo.
* A quantia da transação: é um campo opcional para calcular indicadores de receita automaticamente.

**Perímetro de Hipótese (informações armazenadas em XML)**

O perímetro da hipótese consiste na filtragem da hipótese com base na tabela do schema de consulta.

**Script de sobrecarga de Hipótese (informações armazenadas em XML)**

O script de sobrecarga de hipótese é um código JavaScript que permite sobrecarregar o conteúdo da hipótese durante a execução.

**Indicadores de medição**

Os seguintes indicadores são atualizados automaticamente durante a execução da hipótese:

* Número de reações: **iTransaction**. Número de linhas na tabela de registros de reação.
* Número de contatos: **iContactReact**. Número distinto de contatos direcionados na hipótese.
* Contagem de Grupos de controle: **ProvaReagiu**. Número distinto de contatos de grupo de controle direcionados na hipótese.
* Taxa de resposta contatada: **dContactReacts**. Taxa de resposta dos contatos direcionados na hipótese.
* Taxa de resposta do grupo de controle: **dProofReacts**. Taxa de resposta do grupo de controle da hipótese.
* Receitas totais da população contactada: **dContactReactTotalAmount**. A receita total dos contatos direcionados na hipótese.
* Receita média do grupo de controle: **dContactReactsAvgAmount**. Receita média dos contatos de grupo de controle direcionados na hipótese.
* Total da receita do grupo de controle: **dProofReactsTotalAmount**. A receita total do grupo de controle da hipótese.
* Receita média do grupo de controle: **dProofReactsAvgAmount**. Receita média do grupo de controle hipótese.
* Margem total por contato: **dContactReactTotalMargin**. Margem total por contato direcionado na hipótese.
* Margem média por contato: **dContactReactsAvgMargin**. Margem média por contato direcionado na hipótese.
* Margem total do grupo de controle: **dProofReactsTotalMargin**. Margem total do grupo de controle direcionado na hipótese.
* Margem média de grupo de controle: **dProofReactsAvgMargin**. Margem média do grupo de controle direcionado na hipótese.
* Receitas adicionais: **dAdditionalAmount**. (Receita média do contato - Receita média do grupo de controle) * Número de contatos.
* Margem adicional: **MargemAdicional**. (Margem média de grupo de controle contactada - Margem média de variação) / Número de contatos.
* Custo médio por contato (expressão SQL). Custo calculado do delivery / Número de contatos.
* ROI (expressão SQL). Custo calculado do delivery / margem total do contato.
* ROI efetivo (expressão SQL). Custo calculado do delivery/margem adicional.
* Significância: **Significativo** (expressão SQL). Contém valores de 0 a 3 dependendo da significância da campanha.

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

Essa tabela corresponde ao schema **nms:remaMatchRcp** .

Ele contém um registro representando a reação de um indivíduo a uma determinada hipótese. Esses registros foram criados durante a execução da hipótese.

## Simulação e delivery {#simulation-and-delivery}

Esse conjunto de tabelas está vinculado ao módulo de **Simulação** , que permite testar a distribuição de ofertas pertencentes a uma categoria ou ambiente antes de enviar sua proposta para recipient. Para obter mais informações, consulte [Sobre a simulação](../../interaction/using/about-offers-simulation.md)do oferta.

![](assets/data-model_simulation.png)

* **NmsSimulation**: Esta tabela corresponde ao schema **nms:simulação** . Representa uma simulação para um conjunto de delivery ou ofertas em uma determinada população.
* **NmsDlvSimulationRel**: Esta tabela corresponde ao schema **nms:dlvSimulationRel** . Contém a lista dos delivery considerados na simulação. O escopo da simulação é armazenado em XML.
* **NmsOfferSimulationRel**: Esta tabela corresponde ao schema **nms:offerSimulationRel** . Ele permite que você vincule uma simulação a uma oferta.

## Módulo de interação {#interaction-module}

Esse conjunto de tabelas está vinculado ao módulo **Interação** , que permite responder em tempo real durante uma interação com um determinado contato, tornando-o uma única ou várias ofertas adaptadas. Para obter mais informações, consulte [Interação e gerenciamento](../../interaction/using/interaction-and-offer-management.md)de ofertas.

* **NmsOffer**: Esta tabela corresponde ao schema **nms:oferta** . Contém a definição de cada oferta de marketing.
* **NmsPropositionRcp**: Esta tabela corresponde ao schema **nms:propositionRcp** . Ele contém o log de canais cruzados de proposições de marketing enviadas a cada indivíduo. O registro é criado quando uma proposta é preparada ou efetivamente feita a um indivíduo.
* **NmsOfferSpace**: Esta tabela corresponde ao schema **nms:offerSpace** . Contém a definição dos locais em que são feitas as propostas.
* **NmsOfferContext**: Esta tabela corresponde ao schema **nms:offerContext** . Contém critérios adicionais sobre a aplicabilidade da proposta, bem como a definição da fórmula de cálculo do peso.
* **NmsOfferView**: Esta tabela corresponde ao **nms:offerView**. Ele contém as representações da oferta.
* **NmsOfferCategory**: Esta tabela corresponde a **nms:offerCategory**. Ele contém as categorias ofertas.
* **NmsOfferEnv**: Esta tabela corresponde ao **nms:offerEnv**. Ele contém os ambientes da oferta.

## Módulo do Centro de Mensagens {#message-center-module}

O seguinte conjunto de tabelas está vinculado ao módulo Mensagens **** transacionais (Centro de Mensagens), que permite gerenciar comunicações individuais e únicas enviadas a um usuário e geradas a partir de eventos acionados de sistemas de informações. Para obter mais informações, consulte [Sobre mensagens](../../message-center/using/about-transactional-messaging.md)transacionais.

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

Esta tabela corresponde ao schema **nms:rtEvent** . Ele contém uma definição de eventos em tempo real.

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

Esta tabela corresponde ao schema **nms:batchEvent** . Contém a definição de eventos por lote.

<!--## Microsites Module {#microsites-module}

This set of tables is linked to the **Web applications** functionality, which allows to create and publish dynamic and interactive web applications with data from the database and content adapted to the rights of the connected user. For more on this, see [About web applications](../../web/using/about-web-applications.md).

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: This table matches the **nms:trackingUrl** schema.

* **NmsPurl**: This table matches the **nms:purl** schema.-->

## Módulo NMAC {#nmac-module}

Esse conjunto de tabelas está vinculado ao Canal **do aplicativo** móvel, que permite enviar notificações personalizadas para terminais iOS e Android por meio de aplicativos. Para obter mais informações, consulte [Sobre o canal](../../delivery/using/about-mobile-app-channel.md)do aplicativo móvel.

* **NmsMobileApp**: Esta tabela corresponde ao schema **nms:mobileApp** . Ele contém os aplicativos móveis definidos no Adobe Campaign.
* **Assinatura** NmsApp: Esta tabela corresponde ao schema **nms:appSubscription** . Contém as informações dos assinantes relativas a um ou mais aplicativos.
* **NmsAppSubscriptionRcp**: Esta tabela corresponde ao schema **nms:appSubscriptionRcp** . Ele permite que você vincule visitantes que se inscreveram em um aplicativo à tabela recipient.
* **NmsExcludeLogAppSubRcp**: Esta tabela corresponde ao schema **nms:excludeLogAppSubRcp** .
* **NmsTrackingLogAppSubRcp**: Esta tabela corresponde ao schema **nms:trackingLogAppSubRcp** .
* **NmsBroadLogAppSubRcp**: Esta tabela corresponde ao schema **nms:wideLogAppSubRcp** .

## Módulo de marketing social {#social-marketing-module}

Esse conjunto de tabelas está vinculado ao módulo **Gerenciar redes** sociais, que permite interagir com clientes e prospectos via Facebook e Twitter. Para obter mais informações, consulte [Sobre marketing](../../social/using/about-social-marketing.md)social.

![](assets/data-model_social.png)

* **NmsVisitor**: Esta tabela corresponde ao schema **nms:visitante** . Ele contém informações sobre visitantes.
* **NmsVisitorSub**: Esta tabela corresponde ao **schema nms:visitorSub** . Ele permite que você vincule um visitante aos serviços aos quais eles se inscreveram (Twitter ou Facebook).
* **NmsFriendShipRel**: Esta tabela corresponde ao schema **nms:amizadeRel** . Ele permite que você vincule visitantes com seus amigos no contexto do serviço do Facebook.
* **NmsVisitorInterestRel**: Esta tabela corresponde ao schema **nms:visitorInterestRel** . Permite que você conecte visitantes e seus interesses.
* **NmsInterest**: Esta tabela corresponde ao schema **nms:interest** . Contém a lista de interesses para cada visitante.