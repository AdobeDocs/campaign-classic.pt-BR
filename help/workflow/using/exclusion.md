---
product: campaign
title: Exclusão
description: Saiba mais sobre a atividade de workflow de exclusão
feature: Workflows, Targeting Activity
exl-id: f4fe97d9-6571-4aa5-8022-b0af9d5a6a13
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 100%

---

# Exclusão{#exclusion}

![](../../assets/common.svg)

Uma atividade do tipo **Exclusão** cria um target com base em um target principal do qual um ou mais target são extraídos.

Para configurar essa atividade, insira seu rótulo e selecione o conjunto principal de recipients: o público do conjunto principal permite construir o resultado. Os perfis compartilhados pelo conjunto principal e pelo menos uma das atividades de entrada serão excluídos.

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>Para obter mais informações sobre como configurar e usar a atividade de exclusão, consulte [Excluir uma população (Exclusão)](targeting-data.md#excluding-a-population--exclusion-).

Marque a opção **[!UICONTROL Generate complement]** se desejar explorar a população restante. O complemento conterá o público principal de entrada menos o público de saída. Uma transição de output adicional será adicionada à atividade, da seguinte maneira:

![](assets/s_user_segmentation_exclu_compl.png)

## Exemplos de exclusão {#exclusion-examples}

O exemplo a seguir busca compilar uma lista de recipients com idade entre 18 e 30 anos e excluir os moradores de Paris.

1. Insira e abra uma atividade do tipo **[!UICONTROL Exclusion]** seguida de dois queries. O primeiro query destina-se aos recipients que moram em Paris. O segundo query destina-se aos com idade de 18 a 30 anos.
1. Insira o conjunto principal. Aqui, o conjunto principal é o query de **18-30 anos.** Os elementos pertencentes ao segundo conjunto serão excluídos do resultado final.
1. Marque a opção **[!UICONTROL Generate complement]** se quiser explorar os dados restantes após a exclusão. Nesse caso, o complemento é composto por recipients com idade entre 18 e 30 anos que vivem em Paris.
1. Aprove a configuração de exclusão e depois insira uma atividade de lista de atualização no resultado. Você também pode inserir uma atualização de lista adicional no complemento onde for necessário.
1. Execute o workflow Neste exemplo, o resultado é composto por recipients com idade entre 18 e 30 anos, mas esses que moram em Paris são excluídos e enviados ao complemento.

   ![](assets/exclusion_example.png)

## Parâmetros de entrada {#input-parameters}

* tableName
* schema

Cada evento de entrada deve especificar um target definido por esses parâmetros.

## Parâmetros de saída {#output-parameters}

* tableName
* schema
* recCount

Esse conjunto de três valores identifica o target resultante da exclusão. **[!UICONTROL tableName]** é o nome da tabela que registra os identificadores de target, **[!UICONTROL schema]** é o schema do público (normalmente nms:recipient) e **[!UICONTROL recCount]** é o número de elementos na tabela.

A transição associada ao complemento tem os mesmos parâmetros.
