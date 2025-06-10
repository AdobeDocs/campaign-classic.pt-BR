---
product: campaign
title: Gerenciar acesso às pastas do Campaign
description: Saiba como conceder acesso às pastas do Campaign e criar visualizações
badge: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
feature: Application Settings, Permissions
role: User, Admin
level: Beginner
exl-id: 0ba8a3d0-36d7-42f3-b281-0255e49b5fa3
source-git-commit: 6e83067cef2b08b5bee37610bfef515714756ada
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 93%

---

# Gerenciar o acesso a pastas{#folder-access-management}



Cada pasta da árvore de navegação do Explorer tem direitos de acesso de leitura, gravação e exclusão atribuídos a ela. Para acessar um arquivo, um operador ou grupo de operadores deve ter pelo menos acesso de leitura a ele.

>[!NOTE]
>
>Para saber mais sobre permissões em pastas, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}.


## Pastas e visualizações {#folders-and-views}

### O que é uma pasta {#about-folders}

Pastas são nós na árvore do Adobe Campaign. Esses nós são criados clicando com o botão direito do mouse na árvore, por meio do menu **[!UICONTROL Add new folder]**. Por padrão, o primeiro menu permite adicionar a pasta correspondente ao contexto atual.

![](assets/s_ncs_user_add_folder_in_tree.png)

Você pode personalizar a árvore de navegação do Explorer. Saiba mais sobre as etapas de configuração e as práticas recomendadas [nesta seção](adobe-campaign-workspace.md).

### O que é uma visualização {#about-views}

Além disso, você pode criar visualizações para restringir o acesso aos dados e organizar o conteúdo da árvore para atender aos seus requisitos. É possível atribuir direitos às visualizações.

Uma visualização é uma pasta que exibe os registros fisicamente armazenados em uma ou mais pastas do mesmo tipo. Por exemplo, se você criar uma pasta do Campaing que seja uma visualização, ela exibirá todas as campanhas presentes no banco de dados por padrão, independente de sua origem. Esses dados podem ser filtrados.

Quando você converte uma pasta em uma visualização, todos os dados correspondentes ao tipo de pasta presentes no banco de dados são exibidos na visualização, independentemente da pasta em que são salvos. É possível filtrar para restringir a lista de dados exibidos.

>[!IMPORTANT]
>
>As visualizações contêm dados e fornecem acesso a eles, mas os dados não são armazenados fisicamente na pasta de visualização. O operador deve ter os direitos apropriados para a ação desejada nas pastas da fonte de dados (acesso de leitura no mínimo).
>
>Para conceder acesso a uma visualização sem conceder acesso à pasta de origem, basta não conceder acesso de leitura no nó pai da pasta de origem.

Para distinguir visualizações de pastas, o nome de cada visualização é exibido em uma cor diferente (ciano escuro).

![](assets/s_ncs_user_view_name_color.png)

### Adicionar pastas e criar visualizações {#adding-folders-and-creating-views}

>[!IMPORTANT]
>
>As pastas prontas para uso não devem ser marcadas como visualização.


No exemplo abaixo, criaremos novas pastas para exibir dados específicos:

1. Crie uma nova pasta do tipo **[!UICONTROL Deliveries]** e a nomeie como **Deliveries France**.
1. Clique com o botão direito do mouse nessa pasta e selecione **[!UICONTROL Properties...]**.

   ![Captura de tela mostrando um clique com o botão direito nas propriedades](assets/s_ncs_user_add_folder_exple.png)

1. Na guia **[!UICONTROL Restriction]**, selecione **[!UICONTROL This folder is a view]**. Todas as entregas no banco de dados serão exibidos.

   ![Tela mostrando a caixa de exibição que está sendo marcada](assets/s_ncs_user_add_folder_exple01.png)

1. Defina os critérios do filtro de entrega no editor de query na seção intermediária da janela: as campanhas correspondentes ao filtro definido serão exibidas.

   >[!NOTE]
   >
   >O editor de query é apresentado [nesta seção](../../platform/using/about-queries-in-campaign.md).

   Com as seguintes condições de filtro:

![Captura de tela mostrando as diferentes condições de filtro](assets/s_ncs_user_add_folder_exple00.png)

As seguintes entregas serão exibidas na visualização:

![](assets/s_ncs_user_add_folder_exple02.png)

>[!NOTE]
>
>Ao gerenciar os eventos de [mensagens transacionais](../../message-center/using/about-transactional-messaging.md), as pastas **[!UICONTROL Real time events]** ou **[!UICONTROL Batch events]** não devem ser definidas como visualizações nas instâncias de execução, pois isso pode levar a problemas de direito de acesso. Para obter mais informações sobre a coleção do evento, consulte [esta seção](../../message-center/using/about-event-processing.md#event-collection).

<!--
## Permissions on a folder

### Edit permissions on a folder {#edit-permissions-on-a-folder}

To edit permissions on a specific folder of the tree, follow the steps below:

1. Right-click on the folder and select **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_folder_properties.png)

1. Click the **[!UICONTROL Security]** tab to view authorizations on this folder.

   ![](assets/s_ncs_user_folder_properties_security.png)

### Modify permissions {#modify-permissions}

To modify permissions, you can:

* **Replace a group or an operator**. To do this, click one of the groups (or operators) with rights to the folder, and select a new group (or a new operator) from the drop-down list:

  ![](assets/s_ncs_user_folder_properties_security02.png)

* **Authorize a group or an operator**. To do this, click the **[!UICONTROL Add]** button and select the group or operator to which you want to assign authorizations for this folder.
* **Forbid a group or an operator**. To do this, click **[!UICONTROL Delete]** and select the group or operator from which you want to remove authorization for this folder.
* **Select the rights assigned to a group or an operator**. To do this, click the group or operator concerned, then select the access rights you want to grant and deselect the others.

  ![](assets/s_ncs_user_folder_properties_security03.png)

### Propagate permissions {#propagate-permissions}

You can propagate authorizations and access rights. To do this, select the **[!UICONTROL Propagate]** option in the folder properties.

The authorizations defined in this window will then be applied to all the sub-folders of the current node. You can then overload these authorizations for each of the sub-folders.

>[!NOTE]
>
>Clearing this option for a folder does not automatically clear it for the sub-folders. You must clear it explicitly for each of the sub-folders.

### Grant access to all operators {#grant-access-to-all-operators}

In the **[!UICONTROL Security]** tab, if the **[!UICONTROL System folder]** option is selected, all operators will have access to this data, regardless of their rights. If this option is cleared, you must explicitly add the operator (or their group) to the list of authorizations in order for them to have access.

![](assets/s_ncs_user_folder_properties_security03b.png)
-->