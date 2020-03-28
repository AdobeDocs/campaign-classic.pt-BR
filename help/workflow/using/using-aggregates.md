---
title: Uso de agregações
seo-title: Uso de agregações
description: Uso de agregações
seo-description: null
page-status-flag: never-activated
uuid: 70556745-56b2-4f22-bbc5-7f8106fb0d4a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 9ca649b4-2226-4cfe-bae1-4632c421975b
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Uso de agregações{#using-aggregates}

Esse caso de uso detalha como identificar automaticamente os últimos recipients adicionados ao banco de dados.

Usando o processo a seguir, a data de criação dos recipients no banco de dados é comparada com a última data conhecida em que um recipient foi criado usando um agregado. Todos os recipients criados no mesmo dia também serão selecionados.

Para executar um filtro de tipo **Creation date = max (Creation date)** nos recipients, execute um workflow para seguir estas etapas:

1. Colete recipients do banco de dados usando uma query básica. Para obter mais informações, consulte [Criação de query](../../workflow/using/query.md#creating-a-query).
1. Calcule a última data conhecida que um recipient foi criado usando o resultado gerado pela função de agregação **max (Creation date)**.
1. Vincule cada recipient ao resultado da função de agregação no mesmo schema.
1. Filtre recipients usando o agregado através do esquema editado.

![](assets/datamanagement_usecase_1.png)

## Etapa 1: Cálculo do resultado agregado {#step-1--calculating-the-aggregate-result}

1. Criação de queries Aqui, o objetivo é calcular a última data de criação conhecida de todos os recipients no banco de dados. A query portanto não contém um filtro.
1. Selecione **[!UICONTROL Add data]**.
1. Nas janelas abertas, selecione **[!UICONTROL Data linked to the filtering dimension]** e então, **[!UICONTROL Filtering dimension data]**.
1. Na janela **[!UICONTROL Data to add]**, adicione uma coluna que calcula o valor máximo do campo **Creation date** na tabela de recipients. É possível usar o editor de expressão ou inserir **max(@created)** diretamente em um campo na coluna **[!UICONTROL Expression]**. Clique no botão **[!UICONTROL Finish]**.

   ![](assets/datamanagement_usecase_2.png)

1. Clique em **[!UICONTROL Edit additional data]** e depois em **[!UICONTROL Advanced parameters...]**. Marque a opção **[!UICONTROL Disable automatic adding of the primary keys of the targeting dimension]**.

   Essa opção garante que todos os recipients não sejam exibidos como resultado e que os dados adicionados explicitamente não sejam mantidos. Nesse caso, ele se refere à última data em que um recipient foi criado.

   Deixe a opção **[!UICONTROL Remove duplicate rows (DISTINCT)]** selecionada.

## Etapa 2: Vincular os recipients e o resultado da função de agregação {#step-2--linking-the-recipients-and-the-aggregation-function-result}

Para vincular a query com os recipients à query que realiza o cálculo da função de agregação, é necessário usar uma atividade de edição de schema.

1. Defina a query de recipients como um conjunto principal.
1. Na guia **[!UICONTROL Links]**, adicione um novo link e insira as informações na janela que aparece da seguinte maneira:

   * Selecione o schema temporário relacionado ao agregado. Os dados desse schema serão adicionados aos membros do conjunto principal.
   * Selecione **[!UICONTROL Use a simple join]** para vincular o resultado agregado a cada recipient do conjunto principal.
   * Finalmente, especifique que o link é um **[!UICONTROL Type 11 simple link]**.
   ![](assets/datamanagement_usecase_3.png)

Portanto, o resultado de agregação é vinculado a cada recipient.

## Etapa 3: Filtrar recipients usando o agregado. {#step-3--filtering-recipients-using-the-aggregate-}

Depois que o link tiver sido estabelecido, o resultado agregado e os recipients farão parte do mesmo schema temporário. Portanto, é possível criar um filtro no schema para comparar a data de criação dos recipients e a última data de criação conhecida, representada pela função de agregação. Esse filtro é realizado usando uma atividade Split.

1. Na guia **[!UICONTROL General]**, selecione **Recipients** como a dimensão do target e **Edit schema** como a dimensão do filtro (para filtrar na atividade de schema de transição de entrada).
1. Na guia **[!UICONTROL subsets]**, selecione **[!UICONTROL Add a filtering condition on the inbound population]** e clique em **[!UICONTROL Edit...]**.
1. Usando o editor de expressão, adicione um critério de igualdade entre a data de criação dos recipients e a data de criação calculada pelo agregado.

   Os campos de tipo de data no banco de dados geralmente são salvos em milissegundos. Portanto, é necessário estender esses itens para um dia inteiro para evitar a recuperação dos recipients criados apenas com os mesmos milissegundos.

   Para fazer isso, use a função **ToDate**, disponível no editor de expressão, que converte datas e horas em datas simples.

   As expressões a serem usadas para os critérios são:

   * **[!UICONTROL Expressão]**: `toDate([target/@created])`.
   * **[!UICONTROL Value]**: `toDate([datemax/expr####])` onde expr#### está relacionado ao agregado especificado na query de função de agregação.
   ![](assets/datamanagement_usecase_4.png)

O resultado da atividade split refere-se aos recipients criados no mesmo dia da última data de criação conhecida.

É possível então adicionar outras atividades, como uma atualização de lista ou uma delivery para enriquecer seu workflow.
