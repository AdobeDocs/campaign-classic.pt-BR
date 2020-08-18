---
title: Criação e gerenciamento de listas
seo-title: Criação e gerenciamento de listas
description: Criação e gerenciamento de listas
seo-description: null
page-status-flag: never-activated
uuid: 17d1a7d0-a728-490e-a820-19f469fddbcd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: 9fc243b2-7b7b-4083-83f6-04c12336492d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9a8c3586482d05648de3bdecfdfabcc094c70dbf
workflow-type: tm+mt
source-wordcount: '695'
ht-degree: 80%

---


# Criação e gerenciamento de listas{#creating-and-managing-lists}

## Sobre listas no Adobe Campaign {#about-lists-in-adobe-campaign}

Uma lista é um conjunto estático de perfis que pode ser visada em ações de entrega ou atualizada durante as operações de importação ou durante a execução de fluxos de trabalho. Por exemplo, uma população extraída do banco de dados por uma consulta pode fornecer uma lista.



Lists are created and managed via the **[!UICONTROL Lists]** link in the **[!UICONTROL Profiles and targets]** tab.

![](assets/s_ncs_user_interface_group_link.png)

Dois tipos de listas estão disponíveis no Adobe Campaign:

* Tipo **[!UICONTROL Group]**: as listas tipo **[!UICONTROL Group]** pertencem a uma lista **estática** de pessoas selecionadas de acordo com critérios específicos. A lista é como uma fotografia de um conjunto de perfis. Ela não é atualizada automaticamente quando perfis são adicionados ao banco de dados.

   For more information on how to create a **[!UICONTROL Group]** type list, refer to this [page](#creating-a-profile-list-from-a-group).

* Tipo **[!UICONTROL List]**: as listas tipo **[!UICONTROL List]** permitem a utilização de fluxos de trabalho para criar e gerenciar listas. Elas são listas específicas resultantes de importações de dados, que podem ser atualizadas por meio da atividade dedicada do fluxo de trabalho **[!UICONTROL List update]**.

   Unlike the **[!UICONTROL Group]** type list, this type list can be automatically updated with a **[!UICONTROL Scheduler]** activity. Note that For an example on how to create **[!UICONTROL List]** type lists, refer to [this page](../../workflow/using/list-update.md).

## Criação de uma lista de perfis com base em um grupo {#creating-a-profile-list-from-a-group}

**[!UICONTROL Group]** listas de tipo criadas por meio do **[!UICONTROL Profiles and targets]** link devem se basear na tabela de perfis padrão do Adobe Campaign (nms:recipient).

>[!NOTE]
>
>Para criar listas contendo outros tipos de dados, é necessário executar um fluxo de trabalho. Por exemplo, consulte a tabela visitante e atualize a lista para criar uma lista de visitantes. Para obter mais informações sobre fluxos de trabalho, consulte [esta seção](../../workflow/using/about-workflows.md).

To create a new **[!UICONTROL Group]** type list, apply the following steps:

1. Click the **[!UICONTROL Create]** button and select **[!UICONTROL New list]**.

   ![](assets/s_ncs_user_new_group.png)

1. Insira as informações na guia **[!UICONTROL Edit]** da janela de criação da lista.

   * Insira o nome da lista no campo **[!UICONTROL Label]** e, se necessário, altere o nome interno.
   * Adicione uma descrição para esta lista.
   * É possível especificar uma data de expiração: quando essa data é atingida, a lista é removida e excluída automaticamente.

      ![](assets/list_expiration_date.png)

1. Na guia **[!UICONTROL Content]**, clique em **[!UICONTROL Add]** para selecionar os perfis que pertencem à lista.

   ![](assets/s_ncs_user_add_group.png)

1. Clique em **[!UICONTROL Save]** para salvar a lista. Ela é então adicionada à visão geral das listas.

É possível criar novos perfis diretamente na janela &#39;add profiles&#39; clicando em **[!UICONTROL Create]**. O perfil será adicionado ao banco de dados.

![](assets/s_ncs_user_new_recipient_from_group.png)

A lista de perfis pode ser configurada como qualquer outra lista. Consulte [Configuração de listas](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

## Vinculação de dados a uma lista {#linking-data-to-a-list}

>[!NOTE]
>
>Linking data to a list can only been done with a **[!UICONTROL Group]** type list.

Os perfis de um conjunto de perfis podem ser filtrados e vinculados a uma lista. As ações de entrega podem então ser enviadas para essa lista, para visar perfis. Para agrupar perfis:

1. Selecione os perfis e clique com o botão direito do mouse.
1. Selecione **[!UICONTROL Actions > Associate selection with a list...]**.

   ![](assets/s_ncs_user_add_selection_to_group.png)

1. Selecione a lista desejada ou crie uma nova lista utilizando o botão **[!UICONTROL Create]** e clique em **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_add_selection_to_group_2.png)

1. Clique no botão **[!UICONTROL Start]**.

   ![](assets/s_ncs_user_add_selection_to_group_3.png)

The **[!UICONTROL Recreate the list]** option deletes the earlier content from the list. Esse modo é otimizado uma vez que nenhuma consulta é necessária para verificar se os perfis já estão vinculados à lista.

If you uncheck the **[!UICONTROL No trace of this job is saved in the database]** option, you can select (or create) the execution folder where the information linked to this process will be stored.

A seção superior da janela permite monitorar a execução. The **[!UICONTROL Stop]** button lets you stop the process. Os contatos já processados são vinculados à lista.

É possível monitorar o processo na guia **[!UICONTROL Lists]** nos perfis relacionados a esta operação:

![](assets/s_ncs_user_add_selection_to_group_4.png)

Também é possível editar a lista usando a página inicial do Adobe Campaign: clique no menu **[!UICONTROL Profiles and Targets > Lists]** e selecione a lista relacionada. A guia **[!UICONTROL Content]** mostra os perfis vinculados a esta lista.

![](assets/s_ncs_user_add_selection_to_group_5.png)

## Remoção de um perfil de uma lista {#removing-a-profile-from-a-list}

Para remover um perfil de uma lista, é possível:

* Editar a lista, selecionar o perfil na guia **[!UICONTROL Content]** e clicar no ícone **[!UICONTROL Delete]**.

   ![](assets/list_remove_a_recipient.png)

* Editar o perfil, clicar na guia **[!UICONTROL List]** e clicar no ícone **[!UICONTROL Delete]**.

   ![](assets/recipient_remove_a_list.png)

## Como excluir uma lista de perfis {#deleting-a-list-of-profiles}

É possível excluir uma ou mais listas da lista de grupos na árvore do Adobe Campaign. Para fazer isso, edite a árvore pelo link **[!UICONTROL Advanced > Explorer]** na página inicial do Adobe Campaign. Selecione os grupos relacionados e clique com o botão direito do mouse. Selecione **[!UICONTROL Delete]**. Uma mensagem de aviso solicita que você confirme a exclusão.

>[!NOTE]
>
>Quando você exclui uma lista, os perfis na lista não são afetados, mas os dados nesses perfis são atualizados.

