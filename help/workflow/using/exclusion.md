---
title: Exclusão
seo-title: Exclusão
description: Exclusão
seo-description: null
page-status-flag: never-activated
uuid: e4f54a0b-2fec-4415-986b-83c8928ed174
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: acab51f3-686b-4d2b-bb02-8fbfae36b1ba
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Exclusão{#exclusion}

Uma atividade do tipo **Exclusão** cria um target com base em um target principal do qual um ou mais target são extraídos.

Para configurar essa atividade, insira seu rótulo e selecione o conjunto principal de recipients: o público do conjunto principal permite construir o resultado. Os perfis compartilhados pelo conjunto principal e pelo menos uma das atividades de entrada serão excluídos.

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>Para obter mais informações sobre como configurar e usar a atividade de exclusão, consulte [Excluir uma população (Exclusão)](../../workflow/using/targeting-data.md#excluding-a-population--exclusion-).

Check the **[!UICONTROL Generate complement]** option if you wish to exploit the remaining population. O complemento conterá o público principal de entrada menos o público de saída. Uma transição de output adicional será adicionada à atividade, da seguinte maneira:

![](assets/s_user_segmentation_exclu_compl.png)

## Exemplos de exclusão {#exclusion-examples}

O exemplo a seguir busca compilar uma lista de recipients com idade entre 18 e 30 anos, enquanto exclui os moradores de Paris.

1. Insert and open an **[!UICONTROL Exclusion]** -type activity following two queries. O primeiro query destina-se aos recipients que moram em Paris. O segundo query destina-se aos com idade de 18 a 30 anos.
1. Insira o conjunto principal. Aqui, o conjunto principal é o query de **18-30 anos.** Os elementos pertencentes ao segundo conjunto serão excluídos do resultado final.
1. Check the **[!UICONTROL Generate complement]** option if you wish to exploit the data that remains after the exclusion. Nesse caso, o complemento é composto por recipients com idade entre 18 e 30 anos que vivem em Paris.
1. Aprove a configuração de exclusão e depois insira uma atividade de lista de atualização no resultado. Você também pode inserir uma atualização de lista adicional no complemento onde for necessário.
1. Execute o workflow Neste exemplo, o resultado é composto por recipients com idade entre 18 e 30 anos, mas esses que moram em Paris são excluídos e enviados ao complemento.

   ![](assets/exclusion_example.png)

The blacklist importation example uses an **Exclusion**-type activity which can be found in [Read list](../../workflow/using/read-list.md).

## Parâmetros de entrada {#input-parameters}

* tableName
* schema

Cada evento de entrada deve especificar um target definido por esses parâmetros.

## Parâmetros de output {#output-parameters}

* tableName
* schema
* recCount

Esse conjunto de três valores identifica o target resultante da exclusão. **[!UICONTROL tableName]** é o nome da tabela que registra os identificadores de metas, **[!UICONTROL schema]** é o esquema da população (normalmente nms:customer) e **[!UICONTROL recCount]** é o número de elementos na tabela.

A transição associada ao complemento tem os mesmos parâmetros.
