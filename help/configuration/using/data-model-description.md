---
title: Descrição do modelo de dados do Adobe Campaign Classic
description: Este documento descreve o modelo de dados do Adobe Campaign Classic.
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
source-git-commit: 828c95aaa4b1d0d9507129edb164ddf978c363c1

---


# Descrição do modelo de dados da campanha{#data-model-description}

O Adobe Campaign vem com um modelo de dados predefinido. Esta seção fornece alguns detalhes sobre as tabelas incorporadas do modelo de dados do Adobe Campaign e suas interações.

Para acessar a descrição de cada tabela, vá para **[!UICONTROL Admin > Configuration > Data schemas]**, selecione um recurso da lista e clique na **[!UICONTROL Documentation]** guia.

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>A estrutura física e lógica dos dados transportados no aplicativo é descrita em XML. Ele obedece a uma gramática específica do Adobe Campaign, chamada de esquema. Para obter mais informações sobre os esquemas do Adobe Campaign, leia esta [seção](../../configuration/using/about-schema-reference.md).

## Descrição dos quadros principais {#description-main-tables}

O Adobe Campaign depende de um banco de dados relacional que contém tabelas vinculadas.

O diagrama a seguir mostra as junções entre as principais tabelas de negócios do modelo de dados do Adobe Campaign com os campos principais de cada um.

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

O modelo de dados predefinido do Adobe Campaign inclui as seguintes tabelas principais.

### NmsRecipient {#NmsRecipient}

Essa tabela corresponde ao esquema **nms:receipt** .

É a tabela padrão usada para os **destinatários das entregas**. Por conseguinte, contém as informações necessárias para as entregas através dos vários canais:

* sEmail: endereço de email.
* iEmailFormat: formato preferencial para emails (1 para Texto, 2 para HTML e 0 se não estiver definido).
* sAddress1, sAddress2, sAddress3, sAddress4, sZipCode, sCity são usados para criar o endereço postal (em conformidade com o padrão AFNOR XPZ 10-011 de maio de 1997).
* sPhone, sMobilePhone, sFax contêm os números de telefone, telefone celular e fax, respectivamente.
* iBlackList é o sinalizador de opção de não participação padrão usado para os perfis (1 significa &quot;não inscrito&quot;, 0 caso contrário).

O campo iFolderId é a chave estrangeira que vincula o destinatário à sua pasta de execução. For more on this, see [XtkFolder](#XtkFolder).

O campo sCountryCode é o código ISO 3166-1 Alpha 2 (2 caracteres) do país associado ao destinatário. Este campo é, na verdade, uma chave estrangeira na tabela de referência do país (NmsCountry), que contém as etiquetas do país e outros dados de código do país. Se o país não for preenchido, o valor &#39;XX&#39; será armazenado (e usado no lugar de um registro de ID zero).

Para obter mais informações sobre a tabela Destinatário, consulte esta [seção](../../configuration/using/about-data-model.md#default-recipient-table).

### NmsGroup {#NmsGroup}

Essa tabela corresponde ao esquema **nms:group** .

Ele permite que você crie grupos **estáticos de destinatários**. Há uma relação muitas para muitas entre destinatários e grupos. Por exemplo, um destinatário pode pertencer a vários grupos e um pode conter vários destinatários. Os grupos podem ser criados manualmente, por meio de uma importação ou direcionamento de entrega. Os grupos são frequentemente usados como alvos de entrega. Há um índice exclusivo no campo que representa o nome interno do grupo sName. O grupo está vinculado a uma pasta (a chave é iFolderId. For more on this, see [XtkFolder](#XtkFolder)).

### NmsRcpGrpRel {#NmsRcpGrpRel}

A tabela de relacionamento NmsRcpGrpRel contém apenas os dois campos correspondentes aos identificadores das tabelas vinculadas iRecipientId e iGroupId.

### NmsService {#NmsService}

Esta tabela corresponde ao esquema **nms:service** .

Os serviços são entidades semelhantes a grupos (agrupamentos de destinatários estáticos), exceto que circulam mais informações e permitem o gerenciamento fácil de assinaturas e cancelamentos de assinaturas por meio de formulários.

Há um índice exclusivo no campo que representa o nome interno do serviço sName. O serviço está vinculado a uma pasta (a chave é iFolderId. For more on this, see [XtkFolder](#XtkFolder)). Por fim, o campo iType especifica o canal de entrega desse serviço (0 para email, 1 para SMS, 2 para telefone, 3 para mala direta e 4 para fax).

### NmsSubscription {#NmsSubscription}

Esta tabela corresponde ao esquema **nms:subscription** .

Ele permite que você gerencie assinaturas de destinatários para serviços de informações.

### NmsSubHisto {#NmsSubHisto}

Essa tabela corresponde ao esquema **nms:subHisto** .

Se as assinaturas forem gerenciadas usando formulários da Web ou a interface do aplicativo, todas as assinaturas e desassinaturas serão historizadas na tabela NmsSubHisto. O campo iAction especifica a ação (0 para cancelamento de assinatura e 1 para assinatura) executada na data armazenada no campo tsDate.

### NmsDelivery {#NmsDelivery}

Esta tabela corresponde ao esquema **nms:delivery** .

Cada registro nesta tabela representa uma ação **de** entrega ou um modelo **de** entrega. Ele contém todos os parâmetros necessários para executar entregas (o destino, o conteúdo etc.). Os registros de entrega (difusão) (NmsBroadLog) e os URLs de rastreamento associados (NmsTrackingUrl) são criados durante a fase de análise (consulte abaixo para obter mais detalhes sobre essas tabelas).

Há um índice exclusivo no campo que representa o nome interno da entrega ou do cenário sInternalName. A entrega está vinculada a uma pasta de execução (a chave estrangeira é iFolderProcessId. For more on this, see [XtkFolder](#XtkFolder)).

### XtkFolder {#XtkFolder}

Ele contém **todas as pastas na árvore** visíveis na guia **Navegação** do console.

As pastas são digitadas: o valor do campo sModel especifica o tipo de dados que pode ser contido na pasta. Esse campo também permite que o console do cliente exiba os dados corretamente com os formulários correspondentes. Os valores possíveis para esse campo são definidos na navTree.

A árvore é gerenciada pelos campos iParentId e iChildCount. O campo sFullName fornece o caminho completo da pasta na árvore. Finalmente, há um índice exclusivo no campo que representa o nome interno da pasta sName.

## Entrega e rastreamento {#delivery-and-tracking}

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**: Esta tabela corresponde ao esquema **nms:wideLogMsg** . É uma extensão da tabela de log de entrega.

## Gerenciamento de campanhas {#campaign-management}

![](assets/data-model_campaign.png)

* **NmsOperation**: Esta tabela corresponde ao esquema **nms:operation** . Ele contém os dados de campanhas de marketing.
* **NmsDeliveryOutline**: Essa tabela corresponde ao esquema **nms:deliveryOutline** . Ele contém as propriedades estendidas da entrega (outline de entrega).
* **NmsDlvOutlineItem**: Esta tabela corresponde ao esquema **nms:dlvOutlineItem** . Ele contém os artigos de um contorno de entrega.
* **NmsDeliveryCustomization**: Esta tabela corresponde ao esquema **nms:deliveryCustomization** . Ele contém os campos de personalização de uma entrega.
* **NmsBudget**: Essa tabela corresponde ao esquema **nms:budget** . Contém os dados de um orçamento de uma campanha, um plano, um programa, uma tarefa e/ou entregas.
* **NmsDocument**: Essa tabela corresponde ao esquema **nms:document** . Ele contém os documentos de marketing da campanha na forma de arquivos (imagens, arquivos do Excel ou Word etc.)
* **XtkWorkflow**: Esta tabela corresponde ao esquema **xtk:workflow** . Ele contém direcionamento de campanha.
* **NmsTask**: Esta tabela corresponde ao esquema **nms:task** . Ele contém a definição de uma tarefa de marketing.
* **NmsAsset**: Essa tabela corresponde ao esquema **nms:asset** . Ele contém a definição de um recurso de marketing.

## Consistência da comunicação {#communication-consistency}

![](assets/data-model_typology.png)

* **NmsTypologyRule**: Essa tabela corresponde ao esquema **nms:typologyRule** . Contém as regras que se aplicam às entregas, dependendo das tipologias.
* **NmsTypology**: Essa tabela corresponde ao esquema **nms:typology** . Ele contém o conjunto de regras a ser aplicado às entregas que correspondem à tipologia.
* **NmsTypologyRuleRel**: Essa tabela corresponde ao esquema **nms:typologyRuleRel** . Ele contém as relações entre as tipologias e suas regras.
* **NmsVolumeLine**: Esta tabela corresponde ao esquema **nms:volumeLine** . Ele contém o conjunto de linhas de disponibilidade das regras de capacidade.
* **NmsVolumeConsumed**: Esta tabela corresponde ao esquema **nms:volumeConsumed** . Contém todas as linhas de consumo das regras de capacidade.

## Gerenciamento de respostas {#response-management}

![](assets/data-model_response.png)

### NmsRemaHipótese {#NmsRemaHypothesis}

Esta tabela coincide com o esquema **nms:remaHypotese** . Contém a definição da hipótese de medição.

Esta tabela contém informações importantes armazenadas em XML, incluindo:

**Contexto de execução (informações armazenadas em XML)**

O contexto de execução preenche as tabelas e os campos a serem considerados para o cálculo da medição, a saber:
* O esquema de armazenamento de log de reação nms:remaMatchRcp.
* O esquema da tabela de transações (compra, por exemplo).
* O esquema de consulta, que permite definir a tabela inicial das condições de hipótese.
* Os links para indivíduos, que permitem identificar o indivíduo com base no esquema de consulta.
* A data da transação. Este campo não é obrigatório, mas recomendamos que você o use para restringir o perímetro de cálculo.
* A quantia da transação: é um campo opcional para calcular indicadores de receita automaticamente.

**Perímetro de hipótese (informações armazenadas em XML)**

O perímetro da hipótese consiste na filtragem da hipótese com base na tabela do esquema de consulta.

**Script de sobrecarga de hipótese (informações armazenadas em XML)**

O script de sobrecarga de hipótese é um código JavaScript que permite sobrecarregar o conteúdo da hipótese durante a execução.

**Indicadores de medição**

Os seguintes indicadores são atualizados automaticamente durante a execução da hipótese:

* Número de reações: **iTransaction**. Número de linhas na tabela de registros de reação.
* Número de contatos: **iContactReact**. Número distinto de contatos direcionados na hipótese.
* Contagem de grupos de controle: **ProvaReagiu**. Número distinto de contatos do grupo de controle direcionado na hipótese.
* Taxa de resposta contatada: **dContactReacts**. Taxa de resposta dos contatos direcionados na hipótese.
* Taxa de resposta do grupo de controlo: **dProofReacts**. Taxa de resposta do grupo de controle de hipótese.
* Receitas totais da população contactada: **dContactReactTotalAmount**. Total da receita dos contatos direcionados na hipótese.
* Receita média do grupo de controle: **dContactReactsAvgAmount**. A receita média dos contatos do grupo de controle direcionado na hipótese.
* Total da receita do grupo de controle: **dProofReactsTotalAmount**. A receita total do grupo de controle de hipótese.
* Receita média do grupo de controle: **dProofReactsAvgAmount**. Receita média do grupo de controle de hipótese.
* Margem total por contato: **dContactReactTotalMargin**. Margem total por contato visada na hipótese.
* Margem média por contato: **dContactReactsAvgMargin**. Margem média por contato visada na hipótese.
* Total da margem do grupo de controlo: **dProofReactsTotalMargin**. Margem total do grupo de controlo visado na hipótese.
* Margem média do grupo de controlo: **dProofReactsAvgMargin**. Margem média do grupo de controlo visado na hipótese.
* Receitas adicionais: **dAdditionalAmount**. (Receita média do grupo contactado - Receita média do grupo de controlo) * Número de contatos.
* Margem adicional: **MargemAdicional**. (Margem média do grupo contactado - Margem média do grupo de controlo) / Número de pessoas contactadas.
* Custo médio por contato (expressão SQL). Custo calculado da entrega/Número de contatos.
* ROI (expressão SQL). Custo calculado da entrega / margem total do contatado.
* ROI efetivo (expressão SQL). Custo calculado da entrega/margem adicional.
* Significância: **Significativo** (expressão SQL). Contém valores de 0 a 3 dependendo da significância da campanha.

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

Essa tabela corresponde ao esquema **nms:remaMatchRcp** .

Contém um registro representando a reação de um indivíduo a uma determinada hipótese. Esses registros foram criados durante a execução da hipótese.

## Simulação e entrega {#simulation-and-delivery}

![](assets/data-model_simulation.png)

* **NmsSimulation**: Essa tabela corresponde ao esquema **nms:simulation** . Representa uma simulação para um conjunto de entregas ou ofertas em uma determinada população.
* **NmsDlvSimulationRel**: Esta tabela corresponde ao esquema **nms:dlvSimulationRel** . Contém a lista de entregas consideradas na simulação. O escopo da simulação é armazenado em XML.
* **NmsOfferSimulationRel**: Esta tabela corresponde ao esquema **nms:offerSimulationRel** . Ele permite que você vincule uma simulação a uma oferta.

## Módulo de interação {#interaction-module}

* **NmsOffer**: Esta tabela corresponde ao esquema **nms:offer** . Ele contém a definição de cada oferta de marketing.
* **NmsPropositionRcp**: Essa tabela corresponde ao esquema **nms:propositionRcp** . Ele contém o log entre canais das proposições de marketing enviadas a cada indivíduo. O registro é criado quando uma proposta é preparada ou efetivamente feita a um indivíduo.
* **NmsOfferSpace**: Esta tabela corresponde ao esquema **nms:offerSpace** . Contém a definição dos locais em que são feitas as propostas.
* **NmsOfferContext**: Essa tabela corresponde ao esquema **nms:offerContext** . Contém critérios adicionais sobre a aplicabilidade da proposta, bem como a definição da fórmula de cálculo do peso.
* **NmsOfferView**: Esta tabela corresponde ao **nms:offerView**. Ele contém as representações da oferta.
* **NmsOfferCategory**: Esta tabela corresponde a **nms:offerCategory**. Ele contém as categorias da oferta.
* **NmsOfferEnv**: Esta tabela corresponde ao **nms:offerEnv**. Ele contém os ambientes de oferta.

## Módulo do Centro de Mensagens {#message-center-module}

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

Essa tabela corresponde ao esquema **nms:rtEvent** . Contém uma definição de eventos em tempo real.

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

Essa tabela corresponde ao esquema **nms:batchEvent** . Contém a definição de eventos por lote.

## Módulo de microsites {#microsites-module}

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: Essa tabela corresponde ao esquema **nms:trackingUrl** .

* **NmsPurl**: Essa tabela corresponde ao esquema **nms:purl** .

## Módulo NMAC {#nmac-module}

* **NmsMobileApp**: Esta tabela corresponde ao esquema **nms:mobileApp** . Ele contém os aplicativos móveis definidos no Adobe Campaign.
* **Assinatura** NmsApp: Esta tabela corresponde ao esquema **nms:appSubscription** . Contém as informações dos assinantes relativas a um ou mais aplicativos.
* **NmsAppSubscriptionRcp**: Esta tabela corresponde ao esquema **nms:appSubscriptionRcp** . Ela permite que você vincule visitantes que se inscreveram em um aplicativo à tabela de destinatários.
* **NmsExcludeLogAppSubRcp**: Esta tabela corresponde ao esquema **nms:excludeLogAppSubRcp** .
* **NmsTrackingLogAppSubRcp**: Esta tabela corresponde ao esquema **nms:trackingLogAppSubRcp** .
* **NmsBroadLogAppSubRcp**: Esta tabela corresponde ao esquema **nms:wideLogAppSubRcp** .

## Módulo de marketing social {#social-marketing-module}

![](assets/data-model_social.png)

* **NmsVisitor**: Essa tabela corresponde ao esquema **nms:visitor** . Ele contém informações sobre os visitantes.
* **NmsVisitorSub**: Essa tabela corresponde ao **esquema nms:visitorSub** . Ela permite que você vincule um visitante aos serviços aos quais ele se inscreveu (Twitter ou Facebook).
* **NmsFriendShipRel**: Esta tabela corresponde ao esquema **nms:amizadeRel** . Ela permite que você vincule visitantes a seus amigos no contexto do serviço do Facebook.
* **NmsVisitorInterestRel**: Essa tabela corresponde ao esquema **nms:visitorInterestRel** . Permite que você vincule os visitantes e seus interesses.
* **NmsInterest**: Esta tabela corresponde ao esquema **nms:interest** . Ele contém a lista de interesses para cada visitante.