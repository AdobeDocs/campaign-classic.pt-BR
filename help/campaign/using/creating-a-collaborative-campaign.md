---
title: Criar uma campanha colaborativa
seo-title: Criar uma campanha colaborativa
description: Criar uma campanha colaborativa
seo-description: null
page-status-flag: never-activated
uuid: 13d8ff65-1480-422a-85b6-40b553a3c151
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 01d8be92-7312-4386-b5f5-651af31308f7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# Criar uma campanha colaborativa{#creating-a-collaborative-campaign-intro}

A entidade central cria campanhas colaborativas de templates de campanha de **Marketing distribuído** . Consulte [esta página](../../campaign/using/about-distributed-marketing.md#collaborative-campaign).

## Criar uma campanha colaborativa {#creating-a-collaborative-campaign}

Para configurar uma campanha colaborativa, clique no **[!UICONTROL Campaign management > Campaigns]** nó e no **[!UICONTROL New]** ícone.

>[!NOTE]
>
>Apart from **[!UICONTROL collaborative campaigns (by campaign)]**, these campaigns can be configured and executed via a web interface.

O processo de configuração de um banco de dados da campanha colaborativa é semelhante ao do template de campanha local. As especificações dos diferentes tipos de campanhas colaborativas são detalhadas abaixo.

### Por formulário {#by-form}

To create a collaborative campaign (by form), the **[!UICONTROL Collaborative campaign (by form)]** template must be selected.

![](assets/mkg_dist_mutual_op_form2.png)

In the **[!UICONTROL Edit]** tab, click the **[!UICONTROL Advanced campaign settings...]** link to access the **Distributed Marketing** tab.

Selecione a interface da Web **By form.** Esse tipo de interface permite criar campos de personalização que serão usados por entidades locais ao solicitar uma campanha. Consulte [Criação de uma campanha local (por formulário)](../../campaign/using/examples.md#creating-a-local-campaign--by-form-).

Salve sua campanha. You can now use it from the **Campaign packages** view in the **Campaign** universe, by clicking the **[!UICONTROL Create]** button.

The **[!UICONTROL Campaign Package]** view allows you to use local campaign templates (out-of-the-box or duplicated), as well as reference campaigns for collaborative campaigns, with the aim of creating campaigns for your different organizational entities.

![](assets/mkg_dist_mutual_op_form1b.png)

### Por campanha {#by-campaign}

To create a collaborative campaign (by campaign), the **[!UICONTROL Collaborative campaign (by campaign) (opCollaborativeByCampaign)]** template must be selected.

![](assets/mkg_dist_mutual_op_by_op2.png)

Ao solicitar a campanha, a entidade local pode concluir os critérios predefinidos pela entidade central e avaliar a campanha antes de solicitá-la.

Uma vez que um pedido de **Campanha colaborativa (por campanha)** é aprovado pela entidade central, uma campanha filho é criada para a entidade local. Após disponível para ela, a entidade local pode modificar:

* o workflow da campanha,
* regras de tipologia,
* e campos de personalização.

A entidade local executa a campanha filho. A entidade central executa a campanha pai.

The central entity can view all child campaigns linked with a **Collaborative campaign (by campaign)** from this dashboard (via the **[!UICONTROL List of associated campaigns]** link).

![](assets/mkg_dist_mutual_op_by_op.png)

### Por aprovação de target {#by-target-approval}

To create a collaborative campaign (by target approval), the **[!UICONTROL Collaborative campaign (by target approval)]** template must be selected.

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>Nesse modo, a entidade central não precisa especificar as entidades locais.

O workflow da campanha deve integrar a atividade do tipo de **aprovação Local.** Os parâmetros de atividade são os seguintes:

* **[!UICONTROL Action to perform]** : Notificação de aprovação de target.
* **[!UICONTROL Distribution context]** : Explícito.
* **[!UICONTROL Data distribution]** : Distribuição de entidade local.

A distribuição de dados do tipo de **distribuição de entidade local** deve ser criada. O template de distribuição de dados permite limitar o número de registros de uma lista de valores de agrupamento. Em **[!UICONTROL Resources > Campaign management > Data distribution]**, clique no **[!UICONTROL New]** ícone para criar um novo **[!UICONTROL Data distribution]**. Para obter mais informações sobre distribuição de dados, consulte o guia [Workflows](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-).

![](assets/mkg_dist_data_distribution.png)

Select the **Targeting dimension** and the **[!UICONTROL Distribution field]**. Para o **[!UICONTROL Assignment type]**, selecione Entidade **local**.

In the **[!UICONTROL Distribution]** tab, add a field for each local entity and specify the value.

![](assets/mkg_dist_data_distribution2.png)

Você pode adicionar um segundo **Target approval** após a atividade tipo de **Delivery** para configurar um relatório nele.

Na mensagem de notificação de criação de campanha, a entidade local recebe uma lista de contatos que foi predefinida pelos parâmetros de entidade central.

![](assets/mkg_dist_mutual_op_by_valid1.png)

A entidade local pode excluir determinados contatos com base no conteúdo da campanha.

![](assets/mkg_dist_mutual_op_by_valid2.png)

### Simples {#simple}

To create a simple collaborative campaign, the **[!UICONTROL Collaborative campaign (simple)]** template must be selected.

## Criar um pacote de campanha colaborativa {#creating-a-collaborative-campaign-package}

Para disponibilizar uma campanha para entidades locais, a entidade central deve criar um pacote de campanha.

Siga as etapas abaixo:

1. Na **[!UICONTROL Navigation]** seção da página **Campanhas** , clique no **[!UICONTROL Campaign packages]** link.
1. Clique no botão **[!UICONTROL Create]**.
1. The section at the top of the window lets you select the **[!UICONTROL New collaborative package (mutualizedEmpty)]** template.
1. Selecione a campanha de referência.
1. Especifique o rótulo, pasta e cronograma de execução do pacote de campanha.

### Datas {#dates}

As datas de início e término definem o período de visibilidade da campanha na lista de pacotes de campanha.

Para **campanhas colaborativas**, a entidade central deve especificar o prazo de registro e personalização.

>[!NOTE]
>
>The **[!UICONTROL Personalization deadline]** allows the central entity to choose a deadline by which the local entities must have delivered the documents (spreadsheets, images) to be used to configure the campaign. Essa não é uma opção obrigatória. O não cumprimento desta data não afetará a implementação da campanha.

![](assets/s_advuser_mkg_dist_create_mutual_entry.png)

### Audience {#audience}

A entidade central deve especificar as entidades locais envolvidas por campanha assim que a campanha colaborativa for criada.

![](assets/s_advuser_mkg_dist_create_mutual_entry2.png)

>[!CAUTION]
>
>**[!UICONTROL Simple, by form and by campaign collaborative campaign kits]** não pode ser aprovado, a menos que as entidades locais relevantes tenham sido especificadas.

### Modos de aprovação {#approval-modes}

Para **campanhas colaborativas**, é possível especificar o modo de aprovação do pedido.

![](assets/mkg_dist_edit_kit1.png)

No modo manual, a entidade local precisa se inscrever na campanha para participar.

No modo automático, a entidade local é pré-inscrita na campanha. Ela pode cancelar a inscrição na campanha ou modificar seus parâmetros sem precisar de aprovação da entidade central.

![](assets/mkg_dist_edit_kit2.png)

### Notificações {#notifications}

A configuração de notificações é idêntica às notificações de uma entidade local. Consulte [esta seção](../../campaign/using/creating-a-local-campaign.md#notifications).

## Solicitar uma campanha {#ordering-a-campaign}

Quando uma campanha colaborativa é adicionada à lista de pacotes de campanha, as entidades locais pertencentes ao público definido pela entidade central são notificadas (as **campanhas colaborativas (por aprovação de alvo)** não têm um público predefinido). A mensagem enviada contém um link que permite se registrar na campanha, conforme mostrado abaixo:

![](assets/mkg_dist_mutual_op_notification.png)

Essa mensagem também permite que entidades locais visualizem a descrição inserida pelo operador central que criou o pacote, bem como documentos vinculados à campanha. Esses documentos não pertencem à própria campanha, embora forneçam informações adicionais sobre ela.

Uma vez que os operadores locais tenham feito logon via interface da Web, eles podem inserir informações personalizadas na campanha colaborativa que desejam solicitar:

![](assets/mkg_dist_mutual_op_command.png)

Após uma entidade local ter concluído seu registro, entidades centrais são notificados por e-mail para aprovar sua solicitação.

![](assets/mkg_dist_mutual_op_valid_command.png)

For more on this, refer to the [Approval process](../../campaign/using/creating-a-local-campaign.md#approval-process) section.

## Aprovar um pedido {#approving-an-order}

O processo de aprovação de um pedido de pacote de campanha colaborativa é igual ao processo da campanha local. Consulte [esta seção](../../campaign/using/creating-a-local-campaign.md#approving-an-order).
