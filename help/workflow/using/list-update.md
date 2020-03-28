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
translation-type: ht
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Atualizar lista{#list-update}

Uma atividade **List update** armazena a população especificada na transição em uma lista de recipients.

![](assets/s_user_segmentation_update_group.png)

A lista pode ser selecionada na lista de grupos existentes.

Também pode ser criada usando as opções **[!UICONTROL Create the list if necessary (Computed name)]** e **[!UICONTROL Create the list if necessary (Computed Folder and Name)]**. Essas opções permitem selecionar o rótulo de sua escolha para criar uma lista e, posteriormente, a pasta na qual ela será salva. O rótulo também pode ser gerado automaticamente inserindo campos dinâmicos ou um script. Os diferentes campos dinâmicos estão disponíveis no menu pop-up à direita do rótulo.

![](assets/s_user_segmentation_update_list_calc.png)

Se a lista já existir, os recipients serão adicionados ao conteúdo existente, a não ser que a opção **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** esteja habilitada. Nesse caso, o conteúdo da lista é excluído antes da atualização.

Se desejar que a lista criada ou atualizada use uma tabela diferente da tabela recipient, marque a opção **[!UICONTROL Create or use a list with its own table]**.

Para usar a opção, as tabelas específicas devem ter sido configuradas em sua instância do Adobe Campaign.

Geralmente, salvar um target em uma lista marca o final de um workflow. Por padrão, a atividade **[!UICONTROL List update]** não tem uma transição de saída. Marque a opção **[!UICONTROL Generate an outbound transition]** para adicionar uma.

## Exemplo: List update {#example--list-update}

No exemplo a seguir, a atividade de atualização da lista segue uma query direcionada a homens com mais de 30 anos vivendo na França. A lista será inicialmente criada a partir dos resultados da query. Ela será atualizada sempre que for iniciada a partir do workflow. Ela pode, por exemplo, ser usada regularmente para ofertas promocionais direcionadas em campanhas.

1. Adicione um **[!UICONTROL list update activity]** diretamente após uma consulta, depois abra-a para editá-la.

   Para obter mais informações sobre como criar uma consulta em um workflow, consulte [Query](../../workflow/using/query.md).

1. É possível selecionar um rótulo para a atividade.
1. Selecione a opção **[!UICONTROL Create the list if necessary (Calculated name)]** para mostrar que a lista será criada quando o primeiro workflow tiver sido executado, e então atualizada com as execuções seguintes.
1. Selecione a pasta na qual deseja salvar a lista.
1. Insira um rótulo para a lista. É possível inserir campos dinâmicos para gerar automaticamente o nome a partir da lista. Neste exemplo, a lista tem o mesmo nome que a query para identificar facilmente seu conteúdo.
1. Deixe a opção **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** marcada para excluir recipients que não correspondem aos critérios do target e para inserir os novos recipients na lista.
1. Deixe também a opção **[!UICONTROL Create or use a list with its own table]** marcada.
1. Deixe a opção **[!UICONTROL Generate an outbound transition]** desmarcada.
1. Clique em **[!UICONTROL Ok]** e inicie o workflow.

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   A lista de recipients correspondentes é então criada ou atualizada.

Para obter mais informações, consulte o vídeo [Creating a list of recipients](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html).

## Parâmetros de entrada {#input-parameters}

* tableName
* schema

Identifica a população a ser salva no grupo.

## Parâmetros de output {#output-parameters}

* groupId

Identificador de grupo.
