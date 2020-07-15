---
title: Atualizar dados
seo-title: Atualizar dados
description: Atualizar dados
seo-description: null
page-status-flag: never-activated
uuid: 5f3ab7c8-175a-4b06-a50c-edc97b226e3c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: c94ce5b7-aa8a-4ea2-845d-68c9c7dc2a7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 56212b320d5077f9b66952e7c11eb8bdcea9e3b4
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 84%

---


# Atualizar dados{#update-data}

Uma atividade do tipo **Update data** realiza uma atualização em massa dos campos no banco de dados.

## Tipo de operação {#operation-type}

O campo **[!UICONTROL Operation type]** permite escolher o processo que deve ser executado nos dados no banco de dados:

* **[!UICONTROL Insert or update]**: adicione dados ou atualize-os se já tiverem sido adicionados.
* **[!UICONTROL Insert]**: adicione apenas dados.
* **[!UICONTROL Update]**: atualizar apenas dados.
* **[!UICONTROL Update and merge collections]**: atualize os dados e escolha um registro primário, em seguida, vincule os elementos vinculados aos duplicados neste registro primário. As duplicatas podem ser excluídas sem criar elementos anexados órfãos.
* **[!UICONTROL Delete]**: excluir dados.

![](assets/s_advuser_update_data_1.png)

O campo **[!UICONTROL Batch size]** permite selecionar o número de elementos de transição de entrada a serem atualizados. Por exemplo, se declarado 500, os primeiros 500 registros serão atualizados.

## Identificação de registro {#record-identification}

Especifica como identificar os registros no banco de dados:

* If data entries relate to an existing targeting dimension, select the **[!UICONTROL By directly using the targeting dimension]** option and select it in the **[!UICONTROL Updated dimension]** field.

   É possível exibir os campos da dimensão selecionada usando o botão de lupa **[!UICONTROL Edit this link]**.

* Caso contrário, especifique um ou mais links que permitirão a identificação dos dados no banco de dados ou uso direto das chaves de reconciliação.

![](assets/s_advuser_update_data_2.png)

## Seleção dos campos a serem atualizados {#selecting-the-fields-to-be-updated}

Use the **[!UICONTROL Automatically associate fields with the same name]** option in order for Adobe Campaign to automatically identify the fields to be updated.

![](assets/s_advuser_update_data_3b.png)

Também é possível usar o ícone **[!UICONTROL Insert]** para selecionar manualmente os campos do banco de dados que devem ser atualizados.

![](assets/s_advuser_update_data_3.png)

Selecione todos os campos a serem atualizados e, se necessário, adicione condições dependendo da atualização. To do this, use the **[!UICONTROL Taken into account if]** column. As condições são aplicadas uma após a outra mantendo a ordem na lista. Use as setas à direita para alterar a ordem das atualizações.

É possível usar o mesmo campo de destino várias vezes.

Em uma operação **[!UICONTROL Insert or update]**, é possível selecionar a campanha que deve ser aplicada individualmente ou em cada campo. Para fazer isso, selecione o valor desejado na coluna **[!UICONTROL Operation]**.

![](assets/s_advuser_update_data_5.png)

The **[!UICONTROL modifiedDate]**, **[!UICONTROL modifiedBy]**, **[!UICONTROL createdDate]** and **[!UICONTROL createdBy]** fields are updated automatically during data updates, unless their management mode is configured specifically in the field update table.

A atualização de registro é executada somente para registros contendo pelo menos uma diferença. Se os valores forem iguais, nenhuma atualização será executada.

O link **[!UICONTROL Advanced parameters]** permite especificar as opções adicionais para lidar com a atualização de dados, assim como gerenciar os duplicados. Também é possível:

* **[!UICONTROL Disable automatic key management]**.
* **[!UICONTROL Disable audit]**.
* **[!UICONTROL Empty the destination value if the source value is empty (NULL)]**. Essa opção é selecionada automaticamente por padrão.
* **[!UICONTROL Update all columns with matching names]**.
* Specify conditions that consider source elements using an expression in the **[!UICONTROL Enabled if]** field.
* Especifica condições que consideram duplicatas usando uma expressão. If you check the **[!UICONTROL Ignore records which concern the same target]** option, only the first in the list of expressions will be considered.

**[!UICONTROL Generate an outbound transition]**

Cria uma transição de saída que será ativada no final da execução. A atualização normalmente sinaliza o final de um workflow para construção do target e, portanto, a opção não é ativada por padrão.

**[!UICONTROL Generate an outbound transition for the rejects]**

Cria uma transição de saída contendo registros que não foram processados corretamente após a atualização (por exemplo, se houver uma duplicata). A atualização geralmente marca o final de um workflow para construção do target e, portanto, a opção não é ativada por padrão.

## Atualização e mescla de coleções {#updating-and-merging-collections}

Atualizar dados e mesclar coleções permite atualizar os dados contidos em um registro usando dados de um ou vários registros secundários, com o objetivo de manter apenas um se desejar. Essas atualizações são gerenciadas por um conjunto de regras.

>[!NOTE]
>
>Essa opção também permite processar referências a registros secundários de tabelas de trabalho do workflow (targetWorkflow), deliverys (targetDelivery) e listas (targetList). Se precisar, esses links aparecem na lista onde os campos e coleções são selecionados.

1. Selecione a **[!UICONTROL Update and merge collections]** operação.

   ![](assets/update_and_merge_collections1.png)

1. Selecione a ordem de prioridade dos links. Isso permite identificar o registro principal. Os links disponíveis variam de acordo com a transição de entrada.

   ![](assets/update_and_merge_collections2.png)

1. Selecione as coleções a serem movidas para o registro primário e os campos a serem atualizados.

   Insira as regras que se aplicam a eles assim que um ou vários registros secundários são identificados. Para fazer isso, é possível usar o Construtor de expressões. Para obter mais informações, consulte esta [seção](../../platform/using/defining-filter-conditions.md#building-expressions). Por exemplo, ao especificar que é o valor atualizado mais recentemente de todos os registros diferentes que devem ser mantidos.

   Em seguida, insira as condições a serem consideradas na regra.

   Finalmente, especifique o tipo de atualização para realizar. Por exemplo, é possível optar por excluir os registros secundários após atualizar os dados.

   É possível, por exemplo, configurar a mesclagem de coleções contendo dados heterogêneos como a lista de assinaturas de um recipient. Usando regras, também é possível criar novos históricos de subscrições de registros secundários ou até mover a lista de subscrições de um registro secundário para um registro primário.

1. Especifique a ordem que os registros secundários precisam ser processados, selecionando **[!UICONTROL Advanced parameters]** > **[!UICONTROL Duplicates]**.

   ![](assets/update_and_merge_collections3.png)

Os dados de registros secundários são associados ao registro principal se as regras definidas forem aplicáveis. De acordo com o tipo de atualização selecionada, os registros secundários podem ser excluídos.

## Exemplo: Atualizar os dados após um enriquecimento {#example--update-data-following-an-enrichment}

A seção do caso de uso [Etapa 2: Gravação de dados enriquecidos na seção da tabela &#39;Purchases&#39;](../../workflow/using/creating-a-summary-list.md#step-2--writing-enriched-data-to-the--purchases--table) que detalha a criação de uma lista de recapitulação e oferece um exemplo de atualização de dados após uma atividade de enriquecimento.

## Parâmetros de entrada {#input-parameters}

* tableName
* schema

Cada evento de entrada deve especificar um target definido por esses parâmetros.
