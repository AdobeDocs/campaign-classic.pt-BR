---
solution: Campaign Classic
product: campaign
title: Criação e gerenciamento de listas
description: Saiba como criar e gerenciar o lista
audience: platform
content-type: reference
topic-tags: profile-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 99%

---


# Criação e gerenciamento de listas{#creating-and-managing-lists}

## Sobre listas no Adobe Campaign {#about-lists-in-adobe-campaign}

Uma lista é um conjunto estático de perfis que pode ser direcionada em ações de delivery ou atualizada durante as operações de importação ou durante a execução de workflows. Por exemplo, uma população extraída do banco de dados por uma consulta pode fornecer uma lista.

As listas são criadas e gerenciadas pelo link **[!UICONTROL Lists]** na guia **[!UICONTROL Profiles and targets]**.

![](assets/s_ncs_user_interface_group_link.png)

Dois tipos de listas estão disponíveis no Adobe Campaign:

* Tipo **[!UICONTROL Group]**: as listas do tipo **[!UICONTROL Group]** pertencem a uma lista **estática** de pessoas selecionadas de acordo com critérios específicos. A lista é como uma fotografia de um conjunto de perfis. Ela não é atualizada automaticamente quando perfis são adicionados ao banco de dados.

   Para obter mais informações sobre como criar uma lista do tipo **[!UICONTROL Group]**, consulte esta [página](#creating-a-profile-list-from-a-group).

* Tipo **[!UICONTROL List]**: as listas do tipo **[!UICONTROL List]** permitem a utilização de fluxos de trabalho para criar e gerenciar listas. São listas específicas resultantes de importações de dados, que podem ser atualizadas por meio da atividade específica **[!UICONTROL List update]** do workflow.

   Diferentemente da lista do tipo **[!UICONTROL Group]**, essas listas podem ser atualizadas automaticamente com uma atividade **[!UICONTROL Scheduler]** Para ver um exemplo de como criar listas do tipo **[!UICONTROL List]**, consulte [esta página](../../workflow/using/list-update.md).

![](assets/do-not-localize/how-to-video.png) [Descubra este recurso no vídeo](#create-list-video)

## Criação de uma lista de perfis com base em um grupo {#creating-a-profile-list-from-a-group}

As listas do tipo **[!UICONTROL Group]** criadas por meio do link **[!UICONTROL Profiles and targets]** devem ser baseadas na tabela de perfil padrão do Adobe Campaign (nms:recipient).

>[!NOTE]
>
>Para criar listas contendo outros tipos de dados, é necessário executar um workflow. Por exemplo, consulte a tabela visitante e atualize a lista para criar uma lista de visitantes. Para obter mais informações sobre fluxos de trabalho, consulte [esta seção](../../workflow/using/about-workflows.md).

Para criar uma nova lista do tipo **[!UICONTROL Group]**, siga as seguintes etapas:

1. Clique no botão **[!UICONTROL Create]** e selecione **[!UICONTROL New list]**.

   ![](assets/s_ncs_user_new_group.png)

1. Insira as informações na guia **[!UICONTROL Edit]** da janela de criação da lista.

   * Insira o nome da lista no campo **[!UICONTROL Label]** e, se necessário, altere o nome interno.
   * Adicione uma descrição para esta lista.
   * É possível especificar uma data de expiração: quando essa data é atingida, a lista é removida e excluída automaticamente.

      ![](assets/list_expiration_date.png)

1. Na guia **[!UICONTROL Content]**, clique em **[!UICONTROL Add]** para selecionar os perfis que pertencem à lista.

   ![](assets/s_ncs_user_add_group.png)

1. Clique em **[!UICONTROL Save]** para salvar a lista. Ela é então adicionada à visão geral das listas.

É possível criar novos perfis diretamente na janela “add profiles” clicando em **[!UICONTROL Create]**. O perfil será adicionado ao banco de dados.

![](assets/s_ncs_user_new_recipient_from_group.png)

A lista de perfis pode ser configurada como qualquer outra lista. Consulte [Configuração de listas](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

## Vinculação de dados a uma lista {#linking-data-to-a-list}

>[!NOTE]
>
>A vinculação de dados a uma lista só pode ser feita com uma lista do tipo **[!UICONTROL Group]**.

Os perfis de um conjunto de perfis podem ser filtrados e vinculados a uma lista. As ações de delivery podem então ser enviadas para essa lista, para direcionar perfis. Para agrupar perfis:

1. Selecione os perfis e clique com o botão direito do mouse.
1. Selecione **[!UICONTROL Actions > Associate selection with a list...]**.

   ![](assets/s_ncs_user_add_selection_to_group.png)

1. Selecione a lista desejada ou crie uma nova lista utilizando o botão **[!UICONTROL Create]** e clique em **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_add_selection_to_group_2.png)

1. Clique no botão **[!UICONTROL Start]**.

   ![](assets/s_ncs_user_add_selection_to_group_3.png)

A opção **[!UICONTROL Recreate the list]** exclui o conteúdo anterior da lista. Esse modo é otimizado uma vez que nenhuma consulta é necessária para verificar se os perfis já estão vinculados à lista.

Se você desmarcar a opção **[!UICONTROL No trace of this job is saved in the database]**, será possível selecionar (ou criar) a pasta de execução onde as informações vinculadas a esse processo serão armazenadas.

A seção superior da janela permite monitorar a execução. O botão **[!UICONTROL Stop]** permite interromper o processo. Os contatos já processados são vinculados à lista.

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

## Como criar uma lista de recipients {#create-list-video}

Uma lista é um conjunto estático de recipients que pode ser focada em ações de delivery ou atualizada durante as operações de importação ou durante a execução de fluxos de trabalho. Uma lista de recipients também é chamada de público-alvo.

Aprenda a criar um público-alvo configurando uma lista de recipients do Explorer.

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

## Como criar uma lista de recipients com um workflow {#create-list-in-a-wf-video}

Aprenda a criar um workflow para direcionar os recipients e como torná-lo recorrente antes de usar a lista em um público-alvo de email.

>[!VIDEO](https://video.tv.adobe.com/v/25603?quality=12)
