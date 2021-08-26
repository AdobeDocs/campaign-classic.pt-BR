---
product: campaign
title: Criar uma campanha colaborativa
description: Criar uma campanha colaborativa
audience: campaign
content-type: reference
topic-tags: distributed-marketing
exl-id: 17313fe5-ad42-45ca-a35a-1e7aa89380ef
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 100%

---

# Criar uma campanha colaborativa{#creating-a-collaborative-campaign-intro}

![](../../assets/v7-only.svg)

A entidade central cria campanhas colaborativas de templates de campanha de **Marketing distribuído** . Consulte [esta página](about-distributed-marketing.md#collaborative-campaign).

## Criar uma campanha colaborativa {#creating-a-collaborative-campaign}

Para configurar uma campanha colaborativa, clique no nó **[!UICONTROL Campaign management > Campaigns]** e, em seguida, no ícone **[!UICONTROL New]**.

>[!NOTE]
>
>Além de **[!UICONTROL collaborative campaigns (by campaign)]**, essas campanhas podem ser configuradas e executadas por meio de uma interface da web.

O processo de configuração de um banco de dados da campanha colaborativa é semelhante ao do template de campanha local. As especificações dos diferentes tipos de campanhas colaborativas são detalhadas abaixo.

### Por formulário {#by-form}

Para criar uma campanha colaborativa (por formulário), o modelo **[!UICONTROL Collaborative campaign (by form)]** deve ser selecionado.

![](assets/mkg_dist_mutual_op_form2.png)

Na guia **[!UICONTROL Edit]**, clique no link **[!UICONTROL Advanced campaign settings...]** para acessar a guia **Marketing distribuído**.

Selecione a interface da web **By form**. Esse tipo de interface permite criar campos de personalização que serão usados por entidades locais ao solicitar uma campanha. Consulte [Criar uma campanha local (por formulário)](examples.md#creating-a-local-campaign--by-form-).

Salve sua campanha. Agora você pode usá-lo na visualização **Pacotes do Campaign** na guia **Campaign** clicando no botão **[!UICONTROL Create]**.

A visualização **[!UICONTROL Campaign Package]** permite que você use modelos de campanha locais (integrados ou duplicados), bem como campanhas de referência para campanhas colaborativas, com o objetivo de criar campanhas para suas diferentes entidades organizacionais.

![](assets/mkg_dist_mutual_op_form1b.png)

### Por campanha {#by-campaign}

Para criar uma campanha colaborativa (por campanha), o modelo **[!UICONTROL Collaborative campaign (by campaign) (opCollaborativeByCampaign)]** deve ser selecionado.

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

Para criar uma campanha colaborativa (por aprovação de público alvo), o modelo **[!UICONTROL Collaborative campaign (by target approval)]** deve ser selecionado.

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>Nesse modo, a entidade central não precisa especificar as entidades locais.

O workflow da campanha deve integrar a atividade do tipo de **aprovação Local.** Os parâmetros de atividade são os seguintes:

* **[!UICONTROL Action to perform]** : Notificação de aprovação de target.
* **[!UICONTROL Distribution context]** : Explícito.
* **[!UICONTROL Data distribution]** : Distribuição de entidade local.

A distribuição de dados do tipo de **distribuição de entidade local** deve ser criada. O template de distribuição de dados permite limitar o número de registros de uma lista de valores de agrupamento. Em **[!UICONTROL Resources > Campaign management > Data distribution]**, clique no ícone **[!UICONTROL New]** para criar uma nova **[!UICONTROL Data distribution]**. Para obter mais informações sobre distribuição de dados, consulte o guia [Workflows](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-).

![](assets/mkg_dist_data_distribution.png)

Selecione a **Targeting dimension** e o **[!UICONTROL Distribution field]**. Para o **[!UICONTROL Assignment type]**, selecione **Local entity**.

Na guia **[!UICONTROL Distribution]**, adicione um campo para cada entidade local e especifique o valor.

![](assets/mkg_dist_data_distribution2.png)

Você pode adicionar um segundo **Target approval** após a atividade tipo de **Delivery** para configurar um relatório nele.

Na mensagem de notificação de criação de campanha, a entidade local recebe uma lista de contatos que foi predefinida pelos parâmetros de entidade central.

![](assets/mkg_dist_mutual_op_by_valid1.png)

A entidade local pode excluir determinados contatos com base no conteúdo da campanha.

![](assets/mkg_dist_mutual_op_by_valid2.png)

### Simples {#simple}

Para criar uma campanha colaborativa simples, o modelo **[!UICONTROL Collaborative campaign (simple)]** deve ser selecionado.

## Criar um pacote de campanha colaborativa {#creating-a-collaborative-campaign-package}

Para disponibilizar uma campanha para entidades locais, a entidade central deve criar um pacote de campanha.

Siga as etapas abaixo:

1. Na seção **[!UICONTROL Navigation]** da página **Campaigns**, clique no link **[!UICONTROL Campaign packages]**.
1. Clique no botão **[!UICONTROL Create]**.
1. A seção na parte superior da janela permite selecionar o modelo **[!UICONTROL New collaborative package (mutualizedEmpty)]**.
1. Selecione a campanha de referência.
1. Especifique o rótulo, a pasta e a programação de execução do pacote de campanha.

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
>**[!UICONTROL Simple, by form and by campaign collaborative campaign kits]** não pode ser aprovado a menos que as entidades locais relevantes tenham sido especificadas.

### Modos de aprovação {#approval-modes}

Para **campanhas colaborativas**, é possível especificar o modo de aprovação do pedido.

![](assets/mkg_dist_edit_kit1.png)

No modo manual, a entidade local precisa se inscrever na campanha para participar.

No modo automático, a entidade local é pré-inscrita na campanha. Ela pode cancelar a inscrição na campanha ou modificar seus parâmetros sem precisar de aprovação da entidade central.

![](assets/mkg_dist_edit_kit2.png)

### Notificações {#notifications}

A configuração de notificações é idêntica às notificações de uma entidade local. Consulte [esta seção](creating-a-local-campaign.md#notifications).

## Solicitar uma campanha {#ordering-a-campaign}

Quando uma campanha colaborativa é adicionada à lista de pacotes de campanha, as entidades locais pertencentes ao público definido pela entidade central são notificadas (as **campanhas colaborativas (por aprovação de alvo)** não têm um público predefinido). A mensagem enviada contém um link que permite se registrar na campanha, conforme mostrado abaixo:

![](assets/mkg_dist_mutual_op_notification.png)

Essa mensagem também permite que entidades locais visualizem a descrição inserida pelo operador central que criou o pacote, bem como documentos vinculados à campanha. Esses documentos não pertencem à própria campanha, embora forneçam informações adicionais sobre ela.

Uma vez que os operadores locais tenham feito logon via interface da Web, eles podem inserir informações personalizadas na campanha colaborativa que desejam solicitar:

![](assets/mkg_dist_mutual_op_command.png)

Após uma entidade local ter concluído seu registro, entidades centrais são notificados por e-mail para aprovar sua solicitação.

![](assets/mkg_dist_mutual_op_valid_command.png)

Para obter mais informações, consulte a seção [Approval process](creating-a-local-campaign.md#approval-process).

## Aprovar um pedido {#approving-an-order}

O processo de aprovação de um pedido de pacote de campanha colaborativa é igual ao processo da campanha local. Consulte [esta seção](creating-a-local-campaign.md#approving-an-order).
