---
product: campaign
title: Exclusão
description: Saiba mais sobre a atividade de fluxo de trabalho de exclusão
feature: Workflows, Targeting Activity
hide: true
exl-id: f4fe97d9-6571-4aa5-8022-b0af9d5a6a13
TQID: 'https://experienceleague.adobe.com/ievtR8K-XJLaluRuUfCMqOcCCgaT8-euRj949bPVS30'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: ff84ab2f-a7c2-4ced-a3c8-5113f4348d99
    internal-label: Targeting Activity
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 100%
---
# Exclusão{#exclusion}



Uma atividade do tipo **Exclusão** cria um target com base em um target principal do qual um ou mais target são extraídos.

Para configurar essa atividade, insira seu rótulo e selecione o conjunto principal de destinatários: a população do conjunto principal permite construir o resultado. Os perfis compartilhados pelo conjunto principal e pelo menos uma das atividades de entrada serão excluídos.

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>Para obter mais informações sobre como configurar e usar a atividade de exclusão, consulte [Excluir uma população (Exclusão)](targeting-data.md#excluding-a-population--exclusion-).

Marque a opção **[!UICONTROL Generate complement]** se desejar explorar a população restante. O complemento conterá a população principal de entrada menos a população de saída. Uma transição de output adicional será adicionada à atividade, da seguinte maneira:

![](assets/s_user_segmentation_exclu_compl.png)

## Exemplos de exclusão {#exclusion-examples}

O exemplo a seguir busca compilar uma lista de destinatários com idade entre 18 e 30 anos e excluir os moradores de Paris.

1. Insira e abra uma atividade do tipo **[!UICONTROL Exclusion]** seguida de dois queries. A primeira consulta destina-se aos destinatários que moram em Paris. A segunda consulta destina-se aos com idade de 18 a 30 anos.
1. Insira o conjunto principal. Aqui, o conjunto principal é a consulta de **18-30 anos.** Os elementos pertencentes ao segundo conjunto serão excluídos do resultado final.
1. Marque a opção **[!UICONTROL Generate complement]** se quiser explorar os dados restantes após a exclusão. Nesse caso, o complemento é composto por destinatários com idade entre 18 e 30 anos que vivem em Paris.
1. Aprove a configuração de exclusão e depois insira uma atividade de lista de atualização no resultado. Você também pode inserir uma atualização de lista adicional no complemento onde for necessário.
1. Execute o fluxo de trabalho Neste exemplo, o resultado é composto por destinatários com idade entre 18 e 30 anos, mas esses que moram em Paris são excluídos e enviados ao complemento.

   ![](assets/exclusion_example.png)

## Parâmetros de entrada {#input-parameters}

* tableName
* esquema

Cada evento de entrada deve especificar um target definido por esses parâmetros.

## Parâmetros de saída {#output-parameters}

* tableName
* esquema
* recCount

Esse conjunto de três valores identifica o target resultante da exclusão. **[!UICONTROL tableName]** é o nome da tabela que registra os identificadores de público-alvo, **[!UICONTROL schema]** é o esquema da população (normalmente, nms:recipient) e **[!UICONTROL recCount]** é o número de elementos na tabela.

A transição associada ao complemento tem os mesmos parâmetros.
