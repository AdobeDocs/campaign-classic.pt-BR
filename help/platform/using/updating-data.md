---
title: Atualização dos dados
seo-title: Atualização dos dados
description: Atualização dos dados
seo-description: null
page-status-flag: never-activated
uuid: 3a192934-215a-4a0a-a141-956b5c229f5b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: 1e196989-b8c1-473a-89c9-bbeb68b98419
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 98c880e1218f179b8b804d52690135a2f28520a0
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 89%

---


# Atualização dos dados{#updating-data}

Os dados vinculados ao perfil de um destinatário podem ser atualizados manualmente ou automaticamente.

## Configuração de uma atualização automática {#setting-up-an-automatic-update}

Uma atualização automática pode ser configurada por meio de um fluxo de trabalho. Para obter mais informações, consulte [esta seção](../../workflow/using/update-data.md).

## Como executar uma atualização em massa {#performing-a-mass-update}

Para executar atualizações manuais, clique com o botão direito do mouse nos destinatários selecionados para usar o menu de atalho **[!UICONTROL Actions]** ou use o ícone **[!UICONTROL Actions]**.

![](assets/s_ncs_user_action_icon.png)

Há dois tipos de atualizações: atualização em massa para um conjunto de destinatários e mesclagem de dados entre dois perfis. Para cada ação, um assistente permite configurar a atualização.

### Atualização em massa {#mass-update}

Para atualização em massa, use **[!UICONTROL Action > Mass update of selected lines...]**. O assistente ajuda a configurar e executar a atualização.

A primeira etapa do assistente é especificar os campos que serão atualizados.

A seção à esquerda do assistente exibe a lista de campos disponíveis. Utilize o campo **[!UICONTROL Find]** para executar uma pesquisa nesses campos. Pressione a tecla **Enter** para navegar na lista. Os nomes de campos correspondentes à sua entrada aparecem em negrito, conforme mostrado abaixo.

Clique duas vezes nos campos a serem atualizados para exibi-los na seção à direita do assistente.

![](assets/s_ncs_user_update_wizard01_1.png)

Caso ocorra um erro, use o botão **[!UICONTROL Delete]** para excluir um campo da lista de campos a serem atualizados.

Selecione ou insira os valores para aplicar aos perfis a serem atualizados.

![](assets/s_ncs_user_update_wizard01_12.png)

Clique em **[!UICONTROL Distribution of values]** para exibir a distribuição de valores do campo selecionado para os destinatários presentes na pasta atual (não apenas os destinatários afetados pela atualização).

![](assets/s_ncs_user_update_wizard01_2.png)

É possível definir filtros para exibir a distribuição de valores nessa janela ou modificar a pasta atual para exibir a distribuição de valores em outra pasta. Estas são ações somente leitura. Elas não afetam a configuração da atualização que está sendo definida.

![](assets/s_ncs_user_update_wizard01_3.png)

Feche esta janela e clique em **[!UICONTROL Next]** para exibir a segunda etapa do assistente de atualização. Nesta etapa, clique em **[!UICONTROL Start]** para iniciar a atualização.

![](assets/s_ncs_user_update_wizard01_4.png)

As informações relativas à execução da atualização são exibidas na seção superior do assistente.

**[!UICONTROL Stop]** permite cancelar a atualização, mas alguns registros podem ter sido atualizados, por isso, parar o processo não cancela essas atualizações. A barra de progresso mostra o avanço da operação.

### Mesclar dados {#merge-data}

Select **[!UICONTROL Merge selected lines...]** to launch the merging of two recipient profiles. Os perfis a serem mesclados devem ser selecionados antes de escolher esta opção. A mesclagem é configurada e iniciada usando um assistente.

O assistente exibe os valores a serem recuperados para cada campo preenchido em um ou outro perfil de origem. Se um ou mais campos nos perfis a serem mesclados tiverem valores diferentes, eles serão exibidos na seção **[!UICONTROL List of conflicts]** É possível então selecionar o perfil padrão usando os botões de opção abaixo da lista, como no exemplo a seguir:

![](assets/s_ncs_user_merge_wizard01_1.png)

Clique em **[!UICONTROL Compute]** para exibir o resultado da sua escolha.

![](assets/s_ncs_user_merge_wizard01_2.png)

Verifique as colunas **[!UICONTROL Result]** das duas seções da janela e clique em **[!UICONTROL Finish]** para executar a mesclagem.

## Exportação de dados {#exporting-data}

O conteúdo de uma lista pode ser exportado. Para configurar e executar a exportação:

1. Selecione os registros para exportar.
1. Right-click and select **[!UICONTROL Export...]**.

   ![](assets/s_ncs_user_export_list.png)

1. Em seguida, selecione os dados a serem extraídos. Por padrão, todas as colunas exibidas são adicionadas às colunas de saída.

   ![](assets/s_ncs_user_export_list_start.png)

   Para obter mais informações sobre como configurar o assistente de configuração, consulte [Assistente de exportação](../../platform/using/exporting-data.md#export-wizard).

## Como assinar um serviço {#subscribing-to-a-service}

Na maioria dos casos, os destinatários assinam um boletim informativo por meio de uma página dedicada, conforme explicado [nesta seção](../../delivery/using/managing-subscriptions.md). No entanto, os perfis dos destinatários filtrados podem assinar manualmente um serviço (boletim informativo ou Serviço Viral). Para fazer isso:

1. Selecione os destinatários que deseja assinar e clique com o botão direito do mouse.
1. Selecione **[!UICONTROL Actions > Subscribe selection to a service]**.

   ![](assets/s_ncs_user_selection_subscribe_service.png)

1. Selecione o serviço desejado e clique em **[!UICONTROL Next]**:

   ![](assets/s_ncs_user_selection_subscribe_service_2.png)

   >[!NOTE]
   >
   >Este editor permite a você criar um novo serviço: clique no botão **[!UICONTROL Create]**.

1. Você pode **[!UICONTROL Send a confirmation message]** aos recipient. O conteúdo desta mensagem pode ser configurado no cenário de assinatura vinculado ao serviço selecionado.
1. Clique no botão **[!UICONTROL Start]** para executar o processo de assinatura.

   ![](assets/s_ncs_user_selection_subscribe_service_3.png)

A seção superior da janela permite monitorar o processo de execução. The **[!UICONTROL Stop]** button lets you stop the process. No entanto, os destinatários já processados serão inscritos.

If you uncheck the **[!UICONTROL Do not keep a trace of this job in the database]** option, you can select (or create) the execution folder where the information on this process will be stored.

To check on the process, go to the **[!UICONTROL Subscriptions]** tab on the profiles of the recipients concerned by this operation, or to the **[!UICONTROL Subscriptions]** tab accessed via the **[!UICONTROL Profiles and Targets > Services and Subscriptions]** node.

![](assets/s_ncs_user_selection_subscribe_service_4.png)

>[!NOTE]
>
>Para mais informações sobre criar e configurar serviços de informações, consulte [esta página](../../delivery/using/managing-subscriptions.md).

