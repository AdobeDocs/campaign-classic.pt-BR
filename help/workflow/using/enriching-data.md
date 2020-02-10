---
title: Enriquecimento de dados
seo-title: Enriquecimento de dados
description: Enriquecimento de dados
seo-description: null
page-status-flag: never-activated
uuid: 3f65a8a2-b3e1-4c4c-9653-b8a7c4d7557a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: f87da08f-68b9-4e2b-821f-b3ff20e390f1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Enriquecimento de dados{#enriching-data}

## Sobre enriquecimento de dados {#about-enriching-data}

This use case details possible uses of the **[!UICONTROL Enrichment]** activity in a targeting workflow. Para obter mais informações sobre como usar a **[!UICONTROL Enrichment]** atividade, consulte: [Enriquecimento](../../workflow/using/enrichment.md).

Os contatos do banco de dados de marketing recebem um convite para participar de uma competição por meio de um aplicativo Web. The results of the competition are recovered in the **[!UICONTROL Competition results]** table. This table is linked to the contact table (**[!UICONTROL Recipients]**). A **[!UICONTROL Competition results]** tabela contém os seguintes campos:

* Competition name (@game)
* Trial number (@trial)
* Score (@pontuação)

![](assets/uc1_enrich_1.png)

A contact found in the **[!UICONTROL Recipients]** table can be linked to several lines in the **[!UICONTROL Competition results]** table. A relação entre essas duas tabelas é do tipo 1-n. Aqui está um exemplo dos logs de resultados de um recipient:

![](assets/uc1_enrich_2.png)

O objetivo desse caso de uso é enviar deliveries personalizados às pessoas que faziam parte da competição mais recente, dependendo de suas pontuações mais altas. O recipient com a pontuação mais alta obtém o primeiro prêmio, o recipient com a segunda pontuação mais alta recebe um prêmio de consolação e todos os outros obtêm uma mensagem desejando uma sorte melhor da próxima vez.

Para configurar esse caso de uso, criamos o seguinte workflow para construção do target:

![](assets/uc1_enrich_3.png)

Para criar o workflow, aplique as seguintes etapas:

1. Two **[!UICONTROL Query]** activities and one **[!UICONTROL Intersection]** activity are added to target new subscribers who entered last the competition.
1. A **[!UICONTROL Enrichment]** atividade permite adicionar dados armazenados na **[!UICONTROL Competition results]** tabela. The **[!UICONTROL Score]** field which our delivery personalization will take place on is added to the work table of the workflow.
1. The **[!UICONTROL Split]** type activity enables us to create recipient subsets based on scores.
1. For each subset, a **[!UICONTROL Delivery]** type activity is added.

## Etapa 1: Direcionamento {#step-1--targeting}

A primeira query nos permite selecionar recipients que foram adicionados ao banco de dados nos últimos seis meses.

![](assets/uc1_enrich_4.png)

A segunda query nos permite selecionar os recipients que faziam parte da última competição.

![](assets/uc1_enrich_5.png)

An **[!UICONTROL Intersection]** type activity is then added to target the recipients added to the database within the last six months and who entered the last competition.

## Etapa 2: Enriquecimento {#step-2--enrichment}

In this example, we want to personalize deliveries according to the **[!UICONTROL Score]** field stored in the **[!UICONTROL Competition results]** table. Esta tabela tem um relacionamento de tipo 1-n com a tabela de recipients. The **[!UICONTROL Enrichment]** activity enables us to add data from a table linked to the filtering dimension to the work table of the workflow.

1. Na tela de edição da atividade de enriquecimento, selecione **[!UICONTROL Add data]**, depois **[!UICONTROL Data linked to the filtering dimension]** e clique em **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_6.png)

1. Em seguida, selecione a **[!UICONTROL Data linked to the filtering dimension]** opção, selecione a **[!UICONTROL Competition results]** tabela e clique em **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_7.png)

1. Insira uma ID e um rótulo e selecione a **[!UICONTROL Limit the line count]** opção no **[!UICONTROL Data collected]** campo. In the **[!UICONTROL Lines to retrieve]** field, select &#39;1&#39; as a value. For each recipient, the enrichment activity will add a single line from the **[!UICONTROL Competition results]** table to the work table of the workflow. Clique em **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_8.png)

1. Neste exemplo, devemos recuperar a pontuação mais alta do recipient, mas apenas da última competição. To do this, add a filter to the **[!UICONTROL Competition name]** field to exclude all lines related to previous competitions. Clique em **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_9.png)

1. Go to the **[!UICONTROL Sort]** screen and click the **[!UICONTROL Add]** button, select the **[!UICONTROL Score]** field and check the box in the **[!UICONTROL descending]** column to sort items of the **[!UICONTROL Score]** fields in descending order. Para cada recipient, a atividade de enriquecimento adiciona uma linha que corresponde à pontuação mais alta para o último jogo. Clique em **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_10.png)

1. Na **[!UICONTROL Data to add]** janela, clique duas vezes no **[!UICONTROL Score]** campo. For each recipient, the enrichment activity will add only the **[!UICONTROL Score]** field. Clique em **[!UICONTROL Finish]**.

   ![](assets/uc1_enrich_11.png)

Right-click the inbound transition of the enrichment activity and select **[!UICONTROL Display the target]**. A tabela de trabalho contém os seguintes dados:

![](assets/uc1_enrich_13.png)

O schema vinculado é:

![](assets/uc1_enrich_15.png)

Renovar esta operação na transição de saída da atividade de enriquecimento. Podemos ver que os dados vinculados às pontuações do recipient foram adicionados. A pontuação mais alta de cada recipient foi recuperada.

![](assets/uc1_enrich_12.png)

O schema correspondente também foi enriquecido.

![](assets/uc1_enrich_14.png)

## Etapa 3: Divisão e entrega {#step-3--split-and-delivery}

To sort the recipients based on their scores, a **[!UICONTROL Split]** activity is added after the enrichment.

![](assets/uc1_enrich_18.png)

1. Um subconjunto do primeiro (**Vencedor**) foi definido para incluir o recipient com a pontuação mais alta. Para fazer isso, defina uma limitação do número de registros, aplique uma classificação decrescente à pontuação e limite o número de registros a 1.

   ![](assets/uc1_enrich_16.png)

1. O subconjunto do segundo (**Segundo lugar**) inclui o recipient com a segunda pontuação mais alta. A configuração é igual ao primeiro subconjunto.

   ![](assets/uc1_enrich_17.png)

1. O terceiro subconjunto (**perdedores**) contém todos os outros recipients. Go to the **[!UICONTROL General]** tab and check the **[!UICONTROL Generate complement]** box to target all recipients who did not achieve the two highest scores.

   ![](assets/uc1_enrich_19.png)

1. Add a **[!UICONTROL Delivery]** type activity for each subset, using a different delivery template for each.

   ![](assets/uc1_enrich_20.png)

