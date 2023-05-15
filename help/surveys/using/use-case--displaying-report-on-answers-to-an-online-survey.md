---
product: campaign
title: "Caso de uso: exibição do relatório sobre as respostas de uma pesquisa on-line"
description: "Caso de uso: exibição do relatório sobre as respostas de uma pesquisa on-line"
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Surveys
exl-id: 6be12518-86d1-4a13-bbc2-b2ec5141b505
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 100%

---

# Caso de uso: exibição do relatório sobre as respostas de uma pesquisa online{#use-case-displaying-report-on-answers-to-an-online-survey}



As respostas às pesquisas do Adobe Campaign podem ser coletadas e analisadas usando relatórios dedicados.

No exemplo a seguir, queremos coletar respostas de uma pesquisa on-line e exibi-las em uma tabela dinâmica

Siga as etapas abaixo:

1. Criação de um workflow para recuperar as respostas à pesquisa e armazená-las em uma lista.
1. Criação de um cubo usando os dados na lista.
1. Criação de um relatório com a tabela dinâmica e visualização da análise das respostas.

Antes de começar neste caso de uso, é preciso ter acesso a uma pesquisa e um conjunto de respostas para analisar.

>[!NOTE]
>
>Esse caso de uso só poderá ser implementado se tiver adquirido a opção **Survey Manager.** Verifique o contrato de licença.

## Etapa 1 — criação da coleção de dados e do fluxo de trabalho de armazenamento {#step-1---creating-the-data-collection-and-storage-workflow}

Para coletar as respostas da pesquisa, siga as etapas abaixo:

1. Crie um workflow e coloque uma atividade **[!UICONTROL Answers to a survey]**. Para obter mais informações sobre o uso dessa atividade, consulte [esta seção](../../surveys/using/publish--track-and-use-collected-data.md#using-the-collected-data).
1. Edite a atividade e selecione a pesquisa cujas respostas deseja analisar.
1. Habilite a opção **[!UICONTROL Select all the answer data]** para coletar todas as informações.

   ![](assets/reporting_usecase_1_01.png)

1. Selecione as colunas a serem extraídas (neste caso: selecione: todos os campos arquivados. Esses são os campos que contêm as respostas.

   ![](assets/reporting_usecase_1_02.png)

1. Depois que a caixa de coleção de resposta estiver configurada, posicione uma atividade do tipo **[!UICONTROL List update]** para salvar os dados.

   ![](assets/reporting_usecase_1_04.png)

   Nesta atividade, especifique a lista que deve ser atualizada e desmarque a opção **[!UICONTROL Purge and re-use the list if it exists (otherwise add to the list)]**: as respostas são adicionadas à tabela existente. Essa opção permitirá fazer referência à lista em um cubo. O schema vinculado à lista não será recriado em cada atualização, o que garante a integridade do cubo que usa essa lista.

   ![](assets/reporting_usecase_1_03.png)

1. Inicie o workflow para confirmar sua configuração.

   ![](assets/reporting_usecase_1_05.png)

   A lista especificada é criada e inclui o schema das respostas da pesquisa.

1. Adicione um programador para automatizar a coleta diária das respostas e a atualização da lista.

   As atividades **[!UICONTROL List update]** e **[!UICONTROL Scheduler]** estão detalhadas em .

## Etapa 2 — criação do cubo, suas medidas e seus indicadores {#step-2---creating-the-cube--its-measures-and-its-indicators}

É possível então criar o cubo e configurar suas medidas: elas serão usados para criar os indicadores que serão mostrados no relatório. Para obter mais informações sobre a criação e configuração de cubos, consulte [Sobre os cubos](../../reporting/using/ac-cubes.md).

Neste exemplo, o cubo se baseia nos dados da lista alimentados pelo workflow criado anteriormente.

![](assets/reporting_usecase_2_01.png)

Defina as dimensões e as medidas a serem exibidas no relatório. Aqui, queremos exibir a data do contrato e o país do entrevistado.

![](assets/reporting_usecase_2_02.png)

A guia **[!UICONTROL Preview]** permite controlar a renderização do relatório.

## Etapa 3 — criação do relatório e configuração do layout de dados na tabela {#step-3---creating-the-report-and-configuring-the-data-layout-within-the-table}

Em seguida, é possível criar um relatório com base nesse cubo e processar os dados e informações.

![](assets/reporting_usecase_3_01.png)

Adapte as informações a serem exibidas com base nas suas necessidades.

![](assets/reporting_usecase_3_02.png)
