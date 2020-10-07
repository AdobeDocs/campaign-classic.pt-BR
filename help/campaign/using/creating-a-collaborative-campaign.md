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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 86%

---


# Criar uma campanha colaborativa{#creating-a-collaborative-campaign-intro}

A entidade central cria campanhas colaborativas de templates de campanha de **Marketing distribuído** . Consulte [esta página](../../campaign/using/about-distributed-marketing.md#collaborative-campaign).

## Criar uma campanha colaborativa {#creating-a-collaborative-campaign}

To configure a collaborative campaign, click the **[!UICONTROL Campaign management > Campaigns]** node, then the **[!UICONTROL New]** icon.

>[!NOTE]
>
>Apart from **[!UICONTROL collaborative campaigns (by campaign)]**, these campaigns can be configured and executed via a web interface.

O processo de configuração de um banco de dados da campanha colaborativa é semelhante ao do template de campanha local. As especificações dos diferentes tipos de campanhas colaborativas são detalhadas abaixo.

### Por formulário {#by-form}

To create a collaborative campaign (by form), the **[!UICONTROL Collaborative campaign (by form)]** template must be selected.

![](assets/mkg_dist_mutual_op_form2.png)

In the **[!UICONTROL Edit]** tab, click the **[!UICONTROL Advanced campaign settings...]** link to access the **Distributed Marketing** tab.

Selecione a interface da Web **By form.** Esse tipo de interface permite criar campos de personalização que serão usados por entidades locais ao solicitar uma campanha. Consulte [Criar uma campanha local (por formulário)](../../campaign/using/examples.md#creating-a-local-campaign--by-form-).

Salve sua campanha. Agora você pode usá-lo na exibição **Campaign packages** no universo do **Campaign**, clicando no botão **[!UICONTROL Create]**.

A visualização **[!UICONTROL Campaign Package]** permite que você use modelos de campanha locais (integrados ou duplicados), bem como campanhas de referência para campanhas colaborativas, com o objetivo de criar campanhas para suas diferentes entidades organizacionais.

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

A entidade central pode exibir todas as campanhas-filho vinculadas a uma **Campanha colaborativa (por campanha)** a partir desse painel (por meio do link **[!UICONTROL List of associated campaigns]**).

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

A distribuição de dados do tipo de **distribuição de entidade local** deve ser criada. O template de distribuição de dados permite limitar o número de registros de uma lista de valores de agrupamento. In **[!UICONTROL Resources > Campaign management > Data distribution]**, click the **[!UICONTROL New]** icon to create a new **[!UICONTROL Data distribution]**. Para obter mais informações sobre distribuição de dados, consulte o guia [Workflows](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-).

![](assets/mkg_dist_data_distribution.png)

Select the **Targeting dimension** and the **[!UICONTROL Distribution field]**. For the **[!UICONTROL Assignment type]**, select **Local entity**.

Na guia **[!UICONTROL Distribution]**, adicione um campo para cada entidade local e especifique o valor.

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

1. Na seção **[!UICONTROL Navigation]** da página **Campaigns**, clique no link **[!UICONTROL Campaign packages]**.
1. Clique no botão **[!UICONTROL Create]**.
1. The section at the top of the window lets you select the **[!UICONTROL New collaborative package (mutualizedEmpty)]** template.
1. Selecione a campanha de referência.
1. Especifique o rótulo, pasta e cronograma de execução do pacote de campanha.

### Datas {#dates}

As datas de início e término definem o período de visibilidade da campanha na lista de pacotes de campanha.

Para **campanhas colaborativas**, a entidade central deve especificar o prazo de registro e personalização.

>[!NOTE]
>
>O **[!UICONTROL Personalization deadline]** permite que a entidade central escolha um prazo pelo qual as entidades locais devem entregar os documentos (planilhas, imagens) a serem usados para configurar a campanha. Essa não é uma opção obrigatória. O não cumprimento desta data não afetará a implementação da campanha.

![](assets/s_advuser_mkg_dist_create_mutual_entry.png)

### Público-alvo {#audience}

A entidade central deve especificar as entidades locais envolvidas por campanha assim que a campanha colaborativa for criada.

![](assets/s_advuser_mkg_dist_create_mutual_entry2.png)

>[!CAUTION]
>
>**[!UICONTROL Simple, by form and by campaign collaborative campaign kits]** não pode ser aprovado, a menos que as entidades Locais relevantes tenham sido especificadas.

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

Para obter mais informações, consulte a seção [Approval process](../../campaign/using/creating-a-local-campaign.md#approval-process).

## Aprovar um pedido {#approving-an-order}

O processo de aprovação de um pedido de pacote de campanha colaborativa é igual ao processo da campanha local. Consulte [esta seção](../../campaign/using/creating-a-local-campaign.md#approving-an-order).
