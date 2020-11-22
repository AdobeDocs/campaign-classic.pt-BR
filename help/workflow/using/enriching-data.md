---
solution: Campaign Classic
product: campaign
title: Enriquecimento de dados
description: Saiba mais sobre a atividade do fluxo de trabalho do Enriquecimento
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 99%

---


# Enriquecimento de dados{#enriching-data}

## Sobre enriquecimento de dados {#about-enriching-data}

Este caso de uso detalha possíveis usos da atividade **[!UICONTROL Enrichment]** em um fluxo de trabalho de direcionamento. Para obter mais informações sobre como usar a atividade **[!UICONTROL Enrichment]**, consulte [Enriquecimento](../../workflow/using/enrichment.md).

Um caso de uso sobre como enriquecer um delivery de email com datas personalizadas também está disponível [nesta seção](../../workflow/using/email-enrichment-with-custom-date-fields.md).

Os contatos do banco de dados de marketing recebem um convite para participar de uma competição por meio de um aplicativo Web. Os resultados da competição são recuperados na tabela **[!UICONTROL Competition results]**. Esta tabela está vinculada à tabela de contatos (**[!UICONTROL Recipients]**). A tabela **[!UICONTROL Competition results]** contém os seguintes campos:

* Competition name (@game)
* Trial number (@trial)
* Score (@pontuação)

![](assets/uc1_enrich_1.png)

Um contato encontrado na tabela **[!UICONTROL Recipients]** pode ser vinculado a várias linhas na tabela **[!UICONTROL Competition results]**. A relação entre essas duas tabelas é do tipo 1-n. Aqui está um exemplo dos logs de resultados de um recipient:

![](assets/uc1_enrich_2.png)

O objetivo desse caso de uso é enviar deliveries personalizados às pessoas que faziam parte da competição mais recente, dependendo de suas pontuações mais altas. O recipient com a pontuação mais alta obtém o primeiro prêmio, o recipient com a segunda pontuação mais alta recebe um prêmio de consolação e todos os outros obtêm uma mensagem desejando uma sorte melhor da próxima vez.

Para configurar esse caso de uso, criamos o seguinte workflow para construção do target:

![](assets/uc1_enrich_3.png)

Para criar o workflow, aplique as seguintes etapas:

1. Duas atividades **[!UICONTROL Query]** e uma atividade **[!UICONTROL Intersection]** são adicionadas para direcionar novos assinantes que entraram por último na competição.
1. A atividade **[!UICONTROL Enrichment]** permite adicionar dados armazenados na tabela **[!UICONTROL Competition results]**. O campo **[!UICONTROL Score]**, onde a personalização de delivery ocorrerá, é adicionado à tabela de trabalho do fluxo de trabalho.
1. A atividade do tipo **[!UICONTROL Split]** permite criar subconjuntos de recipients com base em pontuações.
1. Para cada subconjunto, uma atividade tipo **[!UICONTROL Delivery]** é adicionada.

## Etapa 1 - Direcionamento {#step-1--targeting}

A primeira query nos permite selecionar recipients que foram adicionados ao banco de dados nos últimos seis meses.

![](assets/uc1_enrich_4.png)

A segunda query nos permite selecionar os recipients que faziam parte da última competição.

![](assets/uc1_enrich_5.png)

Em seguida, uma atividade tipo **[!UICONTROL Intersection]** é adicionada para direcionar os recipients incluídos no banco de dados nos últimos seis meses e que entraram na última competição.

## Etapa 2 - Enriquecimento {#step-2--enrichment}

Neste exemplo, queremos personalizar os deliveries de acordo com o campo **[!UICONTROL Score]** armazenado na tabela **[!UICONTROL Competition results]**. Esta tabela tem um relacionamento de tipo 1-n com a tabela de recipients. A atividade **[!UICONTROL Enrichment]** permite adicionar dados de uma tabela vinculada à dimensão do filtro à tabela de trabalho do fluxo de trabalho.

1. Na tela de edição da atividade de enriquecimento, selecione **[!UICONTROL Add data]**, então **[!UICONTROL Data linked to the filtering dimension]** e clique em **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_6.png)

1. Em seguida, selecione a opção **[!UICONTROL Data linked to the filtering dimension]**, selecione a tabela **[!UICONTROL Competition results]** e clique em **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_7.png)

1. Digite um ID e um rótulo e selecione a opção **[!UICONTROL Limit the line count]** no campo **[!UICONTROL Data collected]**. No campo **[!UICONTROL Lines to retrieve]**, selecione &#39;1&#39; como um valor. A atividade de enriquecimento adicionará uma única linha da tabela **[!UICONTROL Competition results]** à tabela de trabalho do fluxo de trabalho para cada recipient. Clique em **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_8.png)

1. Neste exemplo, devemos recuperar a pontuação mais alta do recipient, mas apenas da última competição. Para fazer isso, adicione um filtro ao campo **[!UICONTROL Competition name]** para excluir todas as linhas relacionadas às competições anteriores. Clique em **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_9.png)

1. Vá para a tela **[!UICONTROL Sort]** e clique no botão **[!UICONTROL Add]**, selecione o campo **[!UICONTROL Score]** e marque a caixa na coluna **[!UICONTROL descending]** para classificar os itens dos campos **[!UICONTROL Score]** em ordem decrescente. Para cada recipient, a atividade de enriquecimento adiciona uma linha que corresponde à pontuação mais alta para o último jogo. Clique em **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_10.png)

1. Na janela **[!UICONTROL Data to add]**, clique duas vezes no campo **[!UICONTROL Score]**. Para cada recipient, a atividade de enriquecimento adicionará somente o campo **[!UICONTROL Score]**. Clique em **[!UICONTROL Finish]**.

   ![](assets/uc1_enrich_11.png)

Clique com o botão direito do mouse na transição de entrada da atividade de enriquecimento e selecione **[!UICONTROL Display the target]**. A tabela de trabalho contém os seguintes dados:

![](assets/uc1_enrich_13.png)

O schema vinculado é:

![](assets/uc1_enrich_15.png)

Renovar esta operação na transição de saída da atividade de enriquecimento. Podemos ver que os dados vinculados às pontuações do recipient foram adicionados. A pontuação mais alta de cada recipient foi recuperada.

![](assets/uc1_enrich_12.png)

O schema correspondente também foi enriquecido.

![](assets/uc1_enrich_14.png)

## Etapa 3: Split e delivery {#step-3--split-and-delivery}

Para classificar os recipients com base em suas pontuações, uma atividade **[!UICONTROL Split]** é adicionada após o enriquecimento.

![](assets/uc1_enrich_18.png)

1. Um subconjunto do primeiro (**Vencedor**) foi definido para incluir o recipient com a pontuação mais alta. Para fazer isso, defina uma limitação do número de registros, aplique uma classificação decrescente à pontuação e limite o número de registros a 1.

   ![](assets/uc1_enrich_16.png)

1. O subconjunto do segundo (**Segundo lugar**) inclui o recipient com a segunda pontuação mais alta. A configuração é igual ao primeiro subconjunto.

   ![](assets/uc1_enrich_17.png)

1. O terceiro subconjunto (**perdedores**) contém todos os outros recipients. Acesse a guia **[!UICONTROL General]** e marque a caixa **[!UICONTROL Generate complement]** para direcionar todos os recipients que não atingiram as duas pontuações mais altas.

   ![](assets/uc1_enrich_19.png)

1. Adicione uma atividade do tipo **[!UICONTROL Delivery]** para cada subconjunto, usando um template de delivery diferente para cada um.

   ![](assets/uc1_enrich_20.png)

