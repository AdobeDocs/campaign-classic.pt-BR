---
title: Atualizar lista
seo-title: Atualizar lista
description: Atualizar lista
seo-description: null
page-status-flag: never-activated
uuid: 1446f115-3f64-4b95-8e04-6426ab1b8dab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: ca2cd5bf-78a2-4e43-955d-206f4474d1e0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b1a961822224ab0a9551f51942a5f94cf201c8ee
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 75%

---


# Atualizar lista{#list-update}

Uma atividade **List update** armazena a população especificada na transição em uma lista de recipients.

![](assets/s_user_segmentation_update_group.png)

A lista pode ser selecionada na lista de grupos existentes.

Ele também pode ser criado usando as opções **[!UICONTROL Create the list if necessary (Computed name)]** e **[!UICONTROL Create the list if necessary (Computed Folder and Name)]** . Essas opções permitem selecionar o rótulo de sua escolha para criar uma lista e, posteriormente, a pasta na qual ela será salva. O rótulo também pode ser gerado automaticamente inserindo campos dinâmicos ou um script. Os diferentes campos dinâmicos estão disponíveis no menu pop-up à direita do rótulo.

![](assets/s_user_segmentation_update_list_calc.png)

If the list already exists, recipients will be added to the existing content, unless you check the **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** option. Nesse caso, o conteúdo da lista é excluído antes da atualização.

If you want the created or updated list to use a table other than the recipient table then check the **[!UICONTROL Create or use a list with its own table]** option.

Para usar a opção, as tabelas específicas devem ter sido configuradas em sua instância do Adobe Campaign.

Geralmente, salvar um target em uma lista marca o final de um workflow. Por padrão, a atividade **[!UICONTROL List update]** não tem uma transição de saída. Check the **[!UICONTROL Generate an outbound transition]** option to add one.

## Exemplo: List update {#example--list-update}

No exemplo a seguir, a atividade de atualização da lista segue uma query direcionada a homens com mais de 30 anos vivendo na França. A lista será inicialmente criada a partir dos resultados da query. Ela será atualizada sempre que for iniciada a partir do workflow. Ela pode, por exemplo, ser usada regularmente para ofertas promocionais direcionadas em campanhas.

1. Adicione um **[!UICONTROL list update activity]** diretamente após uma consulta, depois abra-a para editá-la.

   Para obter mais informações sobre como criar uma consulta em um workflow, consulte [Query](../../workflow/using/query.md).

1. É possível selecionar um rótulo para a atividade.
1. Select the **[!UICONTROL Create the list if necessary (Calculated name)]** option to show that the list will be created once the first workflow has been executed, then updated with the following executions.
1. Selecione a pasta na qual deseja salvar a lista.
1. Insira um rótulo para a lista. É possível inserir campos dinâmicos para gerar automaticamente o nome a partir da lista. Neste exemplo, a lista tem o mesmo nome que a query para identificar facilmente seu conteúdo.
1. Leave the **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** option checked to delete recipients that do not match the targeting criteria and to insert the new ones into the list.
1. Deixe a **[!UICONTROL Create or use a list with its own table]** opção também marcada.
1. Leave the **[!UICONTROL Generate an outbound transition]** option unchecked.
1. Clique em **[!UICONTROL Ok]** e inicie o workflow.

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   A lista de recipients correspondentes é então criada ou atualizada.

Para obter mais informações, consulte o vídeo [Creating a list of recipients](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html).

## Parâmetros de entrada {#input-parameters}

* tableName
* schema

Identifica a população a ser salva no grupo.

## Parâmetros de output {#output-parameters}

* groupId: Identificador de grupo.
