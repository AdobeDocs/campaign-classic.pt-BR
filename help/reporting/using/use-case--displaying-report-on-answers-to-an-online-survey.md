---
title: '"Caso de uso: exibição do relatório sobre as respostas de uma pesquisa on-line"'
seo-title: '"Caso de uso: exibição do relatório sobre as respostas de uma pesquisa on-line"'
description: '"Caso de uso: exibição do relatório sobre as respostas de uma pesquisa on-line"'
seo-description: null
page-status-flag: never-activated
uuid: 2c0a5b7d-c606-4bcb-9600-8f89e6fce32a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
discoiquuid: 5404a227-6cfb-463b-9a56-af46a022eb38
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Caso de uso: exibição do relatório sobre as respostas de uma pesquisa on-line{#use-case-displaying-report-on-answers-to-an-online-survey}

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

## Etapa 1 - Criação da coleta de dados e do workflow de armazenamento {#step-1---creating-the-data-collection-and-storage-workflow}

Para coletar as respostas da pesquisa, siga as etapas abaixo:

1. Crie um fluxo de trabalho e insira uma **[!UICONTROL Answers to a survey]** atividade. Para obter mais informações sobre o uso dessa atividade, consulte [esta seção](../../web/using/publish--track-and-use-collected-data.md#using-the-collected-data).
1. Edite a atividade e selecione a pesquisa cujas respostas deseja analisar.
1. Ative a **[!UICONTROL Select all the answer data]** opção para coletar todas as informações.

   ![](assets/reporting_usecase_1_01.png)

1. Selecione as colunas a serem extraídas (neste caso: selecione: todos os campos arquivados. Esses são os campos que contêm as respostas.

   ![](assets/reporting_usecase_1_02.png)

1. Once the answer collection box is configured, position a **[!UICONTROL List update]** type activity to save the data.

   ![](assets/reporting_usecase_1_04.png)

   In this activity, specify the list to be updated and un-check the **[!UICONTROL Purge and re-use the list if it exists (otherwise add to the list)]** option: answers are added to the existing table. Essa opção permitirá fazer referência à lista em um cubo. O schema vinculado à lista não será recriado em cada atualização, o que garante a integridade do cubo que usa essa lista.

   ![](assets/reporting_usecase_1_03.png)

1. Inicie o workflow para confirmar sua configuração.

   ![](assets/reporting_usecase_1_05.png)

   A lista especificada é criada e inclui o schema das respostas da pesquisa.

1. Adicione um programador para automatizar a coleta diária das respostas e a atualização da lista.

   As atividades **[!UICONTROL List update]** e **[!UICONTROL Scheduler]** as atividades são descritas em .

## Etapa 2 - Criação do cubo, suas medidas e seus indicadores {#step-2---creating-the-cube--its-measures-and-its-indicators}

É possível então criar o cubo e configurar suas medidas: elas serão usados para criar os indicadores que serão mostrados no relatório. For more on creating and configuring cubes, refer to [About cubes](../../reporting/using/about-cubes.md).

Neste exemplo, o cubo se baseia nos dados da lista alimentados pelo workflow criado anteriormente.

![](assets/reporting_usecase_2_01.png)

Defina as dimensões e as medidas a serem exibidas no relatório. Aqui, queremos exibir a data do contrato e o país do entrevistado.

![](assets/reporting_usecase_2_02.png)

The **[!UICONTROL Preview]** tab lets you control the rendering of the report.

## Etapa 3 - Criação do relatório e configuração do layout de dados dentro da tabela {#step-3---creating-the-report-and-configuring-the-data-layout-within-the-table}

Em seguida, é possível criar um relatório com base nesse cubo e processar os dados e informações.

![](assets/reporting_usecase_3_01.png)

Adapte as informações a serem exibidas com base nas suas necessidades.

![](assets/reporting_usecase_3_02.png)

