---
title: Criar uma campanha local
seo-title: Criar uma campanha local
description: Criar uma campanha local
seo-description: null
page-status-flag: never-activated
uuid: 86e78d9e-26cb-4aea-b8ce-5e52ae352b48
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: bd057441-8524-49e6-b5d5-fbd0ec5bca85
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e97183256ef6d3f2068dd0fbc8eb3c3f32e0bae0
workflow-type: tm+mt
source-wordcount: '1573'
ht-degree: 81%

---


# Criar uma campanha local{#creating-a-local-campaign}

A local campaign is an instance created from a template referenced in the list of **[!UICONTROL campaign packages]** with a **specific execution schedule**. Seu objetivo é atender a uma comunicação local usando um template de campanha que foi criado e configurado pela entidade central. Os principais estágios para a implementação de uma operação local são:

**Para a entidade central**

1. Criar um template de campanha local.
1. Criar um pacote de campanha a partir de um template.
1. Publicar um pacote de campanha
1. Aprovar pedidos

**Para a entidade local**

1. Solicitar a campanha
1. Executar campanhas

## Criar um template de campanha local {#creating-a-local-campaign-template}

Para criar um pacote de campanha, primeiro crie o **modelo de campanha** por meio do nó **[!UICONTROL Resources > Templates]**.

To create a new local template, duplicate the default **[!UICONTROL Local campaign (opLocal)]** template.

![](assets/mkg_dist_local_op_creation.png)

Nomeie seu template de campanha e preencha os campos disponíveis.

![](assets/mkg_dist_local_op_creation1.png)

In the campaign window, click the **[!UICONTROL Edit]** tab, then click the **[!UICONTROL Advanced campaign settings...]** link.

![](assets/mkt_distr_4.png)

### Interface da Web {#web-interface}

Na guia **Marketing distribuído**, você pode escolher o tipo de interface da Web e especificar os valores e parâmetros padrões a serem inseridos quando uma entidade local colocar um pedido.

A interface da Web corresponde a um formulário a ser preenchido pela entidade local ao solicitar a campanha.

Selecione o tipo de interface da Web a ser aplicada às campanhas criadas a partir do template:

![](assets/mkt_distr_1.png)

Há quatro tipos de interfaces da Web disponíveis:

* **[!UICONTROL By brief]** : A entidade Local deve fornecer uma descrição em que descreve as configurações da campanha. Uma vez aprovada o pedido, a entidade central configura e executa a campanha como um todo.

   ![](assets/mkt_distr_6.png)

* **[!UICONTROL By form]** : a entidade local tem acesso a um formulário da Web onde, dependendo do template usado, podem editar o conteúdo, o alvo, o tamanho máximo, bem como datas de criação e extração usando campos de personalização. A entidade local pode avaliar o target e pré-visualizar o conteúdo desse formulário Web.

   ![](assets/mkt_distr_8.png)

   The form offered is specified in a Web application that must be selected in a drop-down list from the **[!UICONTROL Web Interface]** field in the template&#39;s **[!UICONTROL Advanced campaign settings...]** link. Consulte [Criar uma campanha local (por formulário)](../../campaign/using/examples.md#creating-a-local-campaign--by-form-).

   >[!NOTE]
   >
   >A aplicação Web usada neste exemplo é um exemplo. É necessário criar um aplicativo Web específico para poder usar um formulário. Consulte a [API](../../configuration/using/about-web-services.md).

   ![](assets/mkt_distr_7.png)

* **[!UICONTROL By external form]** : A entidade Local tem acesso aos parâmetros de campanha em sua extranet (não Adobe Campaign). Esses parâmetros são idênticos aos de uma **campanha local (por formulário)**.
* **[!UICONTROL Pre-set]** : A campanha de pedidos de entidade Local usando o formulário padrão, sem localizá-lo.

   ![](assets/mkt_distr_5.png)

### Default values {#default-values}

Select the **[!UICONTROL Default values]** to be completed by local entities. Por exemplo:

* contato e datas de extração,
* características do target (segmento de idade, etc.).

![](assets/mkg_dist_local_op_creation2.png)

Complete the **[!UICONTROL Parent marketing program]** and **[!UICONTROL Charge]** fields.

![](assets/mkg_dist_local_op_creation3.png)

### Aprovações {#approvals}

From the **[!UICONTROL Advanced parameters for campaign entry]** link, you can specify the maximum number of reviewers.

![](assets/s_advuser_mkg_dist_add_valid_op1.png)

Os revisores serão inseridos pela entidade local ao solicitar a campanha.

![](assets/mkt_distr_5.png)

Se você não deseja nomear revisores para uma campanha, insira 0.

### Documentos {#documents}

Você pode permitir que operadores de entidades locais vinculem documentos (arquivos de texto, planilhas, imagens, descrições de campanha etc.) à campanha local ao criar o pedido. The **[!UICONTROL Advanced parameters for campaign entry...]** link lets you restrict the number of documents. To do this, simply enter the maximum number allowed in the **[!UICONTROL Number of documents]** field.

![](assets/s_advuser_mkg_dist_local_docs.png)

Ao solicitar um pacote de campanha, o formulário sugere vincular quantos documentos forem indicados no campo correspondente no template.

![](assets/s_advuser_mkg_dist_add_docs.png)

Para não exibir um campo para fazer upload de documento, digite **[!UICONTROL 0]** no campo **[!UICONTROL Number of documents]**.

>[!NOTE]
>
>O **[!UICONTROL Advanced parameters for campaign entry]** pode ser desativado verificando-se **[!UICONTROL Do not display the page used to enter the campaign parameters]**.

![](assets/s_advuser_mkg_dist_disable_op_parameters.png)

### Workflow {#workflow}

In the **[!UICONTROL Targeting and workflows]** tab, create the campaign workflow that collects the **[!UICONTROL Default values]** specified in the **[!UICONTROL Advanced campaign settings...]** and creates the deliveries.

![](assets/mkg_dist_local_op_creation4b.png)

Double click the **[!UICONTROL Query]** activity to configure it according to the specified **[!UICONTROL Default values]**.

![](assets/mkt_dist_local_campaign_localize_query.png)

### Delivery {#delivery}

In the **[!UICONTROL Audit]** tab, click the **[!UICONTROL Detail...]** icon to view the **[!UICONTROL Scheduling]** for the selected delivery.

![](assets/mkg_dist_local_op_creation4c.png)

O ícone **[!UICONTROL Scheduling]** permite configurar o contato da entrega e a data de execução.

![](assets/mkg_dist_local_op_creation4d.png)

Se necessário, configure o tamanho máximo do delivery:

![](assets/mkg_dist_local_op_creation4e.png)

Localize o HTML do seu delivery. For example, in **[!UICONTROL Delivery > Current order > Additional fields]**, use the **[!UICONTROL Age segment]** field to locate the delivery according to the age of the target.

![](assets/mkt_dist_local_campaign_localize_html.png)

Salve seu template de campanha. Agora é possível usá-lo na exibição **Campaign packages** no universo **Campaigns**, clicando no botão **[!UICONTROL Create]**.

![](assets/mkt_distr_9.png)

>[!NOTE]
>
>Os modelos de campanha e a configuração geral estão detalhados em [Campaign templates](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

## Criação do pacote de campanha {#creating-the-campaign-package}

Para que o template de campanha fique disponível para entidades locais, ele precisa ser adicionado à lista. Para fazer isso, a agência central precisa criar um novo pacote.

Siga as etapas abaixo:

1. In the **[!UICONTROL Navigation]** section on the **Campaigns** page, click the **[!UICONTROL Campaign packages]** link.
1. Clique no botão **[!UICONTROL Create]**.

   ![](assets/mkg_dist_add_an_entry.png)

1. A seção acima da janela permite selecionar o template do pacote de campanha especificado [anteriormente](#creating-a-local-campaign-template) .

   By default, the **[!UICONTROL New local campaign package (localEmpty)]** template is used for local campaigns.

1. Especifique o rótulo, pasta e cronograma de execução do pacote de campanha.

### Datas {#dates}

As datas de início e término definem o período de visibilidade da campanha na lista de pacotes de campanha.

A data de disponibilidade é a data em que a campanha fica disponível para entidades locais (para solicitar).

>[!CAUTION]
>
>Se uma entidade local não reservar a campanha antes do prazo, ela não poderá usá-la.

Essas informações são encontradas na mensagem de notificação enviada para agências locais, conforme mostrado abaixo:

![](assets/s_advuser_mkg_dist_local_notif.png)

### Público-alvo {#audience}

For a local campaign, the central entity can specify the local entities involved by checking the **[!UICONTROL Limit the package to a set of local entities]**.

![](assets/s_advuser_mkg_dist_create_mutual_entry3.png)

### Configurações adicionais {#additional-settings}

Depois que o pacote é salvo, a entidade central pode editá-la na guia **[!UICONTROL Edit]**.

![](assets/mkg_dist_edit_kit.png)

A partir da guia **[!UICONTROL General]**, a entidade central pode:

* configure the campaign package reviewer(s) from the **[!UICONTROL Approval parameters...]** link,
* revisar o cronograma de execução,
* adicionar ou excluir entidades locais.

>[!NOTE]
>
>Por padrão, cada entidade pode solicitar uma **campanha local** apenas uma vez.
>   
>Marque a opção **[!UICONTROL Enable multiple creation]** para permitir que várias campanhas locais sejam criadas a partir do pacote de campanha.

![](assets/mkg_dist_local_op_multi_crea.png)

### Notificações {#notifications}

Quando uma campanha se torna disponível ou quando o prazo de registro é atingido, uma mensagem é enviada aos operadores do grupo de notificação local. Para obter mais informações, consulte [Entidades organizacionais](../../campaign/using/about-distributed-marketing.md#organizational-entities).

## Solicitar uma campanha {#ordering-a-campaign}

Os pacotes de campanha ficam acessíveis às entidades locais quando aprovados e quando seu período de implementação começou. As entidades locais recebem um e-mail informando que um novo pacote de campanha está disponível (assim que a data de disponibilidade é atingida).

>[!NOTE]
>
>Se algumas entidades locais foram especificadas ao criar o pacote de campanha, elas serão as únicas a receberem uma notificação. Se nenhuma entidade local tiver sido especificada, todas as entidades locais receberão uma notificação.

![](assets/mkg_dist_local_op_notification.png)

Para usar uma campanha oferecida pela entidade central, a entidade local deve solicitá-la.

Para solicitar uma campanha:

1. Clique em **[!UICONTROL Order campaign]** na mensagem de notificação ou no botão correspondente no Adobe Campaign.

   Digite sua ID e senha para solicitar a campanha. A interface é composta de um conjunto de páginas definidas em uma aplicação Web.

   >[!NOTE]
   >
   >As aplicações Web são detalhadas no guia [funcionalidades da Web](../../web/using/about-web-applications.md).

1. Insira as informações necessárias na primeira página (rótulo do pedido e comentário) e clique em **[!UICONTROL Next]**.

   ![](assets/mkg_dist_subscribe_step1.png)

1. Complete os parâmetros disponíveis e aprove o pedido.

1. Uma notificação é enviada ao gerente da entidade organizacional à qual a entidade local pertence, para aprovar esse pedido.

   ![](assets/mkg_dist_subscribe_step3.png)

1. As informações são retornadas às entidades locais e centrais. Embora entidades locais possam exibir apenas seus próprios pedidos, a entidade central pode visualizar todos os pedidos por qualquer entidade local, conforme mostrado abaixo:

   ![](assets/mkg_dist_subscribe_central_view.png)

   Os operadores podem exibir detalhes do pedido:

   ![](assets/mkg_dist_local_op_catalog_detail_1.png)

   A guia **[!UICONTROL Edit]** contém as informações inseridas pela entidade local ao solicitar a campanha.

   ![](assets/mkg_dist_local_op_catalog_detail_1b.png)

1. O pedido deve ser aprovado pela entidade central para ser finalizado.

   ![](assets/mkg_dist_local_op_catalog_detail_3.png)

   Para obter mais informações, consulte a seção [Approval process](#approval-process).

1. O operador local é, então, notificado de que a campanha está disponível: a disponibilidade da campanha pode ser encontrada na lista de pacotes de campanha no universo **Campaigns.** A campanha pode ser usada. Para obter mais informações, consulte [Como acessar campanhas](../../campaign/using/accessing-campaigns.md).

   The **[!UICONTROL Start targeting with order approval]** option lets the local entity run the campaign as soon as the order has been approved.

   ![](assets/mkg_dist_local_op_catalog_use.png)

## Aprovar um pedido {#approving-an-order}

Para confirmar um pedido de campanha, a entidade central deve aprová-lo.

A visão geral dos **[!UICONTROL Campaign orders]**, acessada por meio do universo **Campaigns**, permite a visualização do status dos pedidos de campanha e a aprovação deles.

>[!NOTE]
>
>As entidades locais podem fazer alterações no pedido até que ele seja aprovado.

### Processo de aprovação {#approval-process}

#### Notificação por e-mail {#email-notification}

Quando uma campanha é solicitada por uma entidade local, seus revisores são notificados por e-mail, conforme mostrado abaixo:

![](assets/mkg_dist_valid_notif_email.png)

>[!NOTE]
>
>A seleção de revisores é apresentada na seção [Revisores](#reviewers). Eles podem aceitar ou rejeitar o pedido.

![](assets/mkg_dist_command_valid_web.png)

#### Aprovar via console do Adobe Campaign {#approving-via-the-adobe-campaign-console}

O pedido também pode ser aprovado por meio do console, na visão geral do pedido de campanha. To approve an order, select it and click **[!UICONTROL Approve the order]**.

![](assets/mkg_dist_local_order_valid.png)

>[!NOTE]
>
>A campanha ainda pode ser editada e reconfigurada até a data de disponibilidade da campanha. As entidades locais também podem rejeitar a campanha clicando no botão **[!UICONTROL Cancel]**.

#### Criação de uma campanha {#creating-a-campaign}

Uma vez aprovado o pedido de campanha, ele pode ser configurado e executado pela entidade local.

![](assets/mkg_dist_mutual_op_created.png)

Para obter mais informações, consulte [Como acessar campanhas](../../campaign/using/accessing-campaigns.md).

### Recusar uma aprovação {#rejecting-an-approval}

O operador encarregado da aprovação pode rejeitar um pedido ou um pacote de campanha.

![](assets/mkg_dist_do_not_valid.png)

Se o revisor rejeitar um pedido, a notificação relevante será automaticamente enviada às entidades locais relacionadas: ela exibirá o comentário inserido pelo operador que rejeitou a aprovação.

As informações são exibidas na lista da página de pacotes de campanha ou na página do pedido da campanha.. Se tiverem acesso ao console do Adobe Campaign, entidades locais serão informadas dessa rejeição.

![](assets/mkg_dist_do_not_valid_view.png)

Eles podem exibir o comentário relacionado do pacote de campanha na guia **[!UICONTROL Edit]**.

![](assets/mkg_dist_do_not_valid_tab.png)

### Revisores {#reviewers}

Toda vez que uma aprovação é necessária, os revisores são notificados por e-mail.

Para cada entidade local, os revisores são selecionados para aprovação de pedido de campanha e aprovação de campanha. Para obter mais informações sobre a seleção de revisores locais, consulte [Entidades organizacionais](../../campaign/using/about-distributed-marketing.md#organizational-entities).

>[!NOTE]
>
>Para que essa seleção seja possível, a aprovação de pedidos ainda não deve estar ativa.

### Cancelar um pedido {#canceling-an-order}

A agência central pode cancelar um pedido por meio do uso do botão **[!UICONTROL Delete]**, localizado no painel de pedidos.

![](assets/mkg_dist_local_op_cancel.png)

This cancels the campaign in the **[!UICONTROL Campaign orders]** view.
