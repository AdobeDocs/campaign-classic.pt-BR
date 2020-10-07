---
title: Regras de consistência
seo-title: Regras de consistência
description: Regras de consistência
seo-description: null
page-status-flag: never-activated
uuid: 9b497460-ba42-4bc7-98e0-55c1b4be5e44
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 9bcb5dc1-8cb4-4781-a8cd-8d072ff28b1a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 88%

---


# Regras de consistência{#consistency-rules}

## Sobre as regras de consistência {#about-consistency-rules}

O Adobe Campaign garante comunicações consistentes graças a um conjunto de regras contidas nas tipologias de campanha. Seu objetivo é controlar os deliveries enviados aos recipients, como volume, natureza, relevância etc.

As regras de **Capacidade** podem evitar sobrecarga na plataforma relacionada ao delivery de mensagens. Como exemplo, as ofertas especiais que contêm um link de download não devem ser enviadas para muitas pessoas de uma só vez, para evitar a saturação do servidor; as campanhas por telefone não devem exceder a capacidade de processamento das centrais de atendimento etc. Para obter mais informações, consulte [Controle de capacidade](#controlling-capacity).

## Controlando a capacidade {#controlling-capacity}

Antes de enviar mensagens, você precisa garantir que sua organização tem a capacidade de processar o delivery (infraestrutura física), as respostas que o delivery pode gerar (mensagens de entrada) e o número de chamadas a serem feitas para entrar em contato com assinantes (capacidade de processamento da central de chamadas), por exemplo.

To do this, you need to create **[!UICONTROL Capacity]** typology rules.

No exemplo a seguir, criamos uma regra de tipologia para uma campanha de fidelidade de telefone. Restringimos o número de mensagens a 20 por dia, ou seja, a capacidade diária de processamento de uma central de chamadas. Uma vez que a regra tenha sido aplicada a dois deliveires, poderemos monitorar o consumo por meio de logs.

Para projetar uma nova regra de capacidade, siga as etapas abaixo:

1. No **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** nó, clique em **[!UICONTROL New]**.
1. Select a **[!UICONTROL Capacity]** rule type.

   ![](assets/campaign_opt_create_capacity_01.png)

1. Na guia **[!UICONTROL Capacity]**, crie as linhas de disponibilidade: no nosso exemplo, há períodos durante os quais as chamadas podem ser feitas. Selecione um período de 24 horas e insira 150 na quantidade inicial, o que significa que a central de chamadas é capaz de atender 150 chamadas por dia.

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >As linhas de disponibilidade são somente para fins de informação. Caso precise excluir mensagens quando o limite de capacidade for atingido, consulte [esta seção](#exclude-messages-when-capacity-limit-reached).

1. Associe esta regra a uma tipologia e, em seguida, faça referência à tipologia em seu delivery para aplicar essa regra de capacidade. Para obter mais informações, consulte [esta seção](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery).
1. You can monitor consumption from the rule **[!UICONTROL Consumptions]** and **[!UICONTROL Capacity]** tabs.

   Quando uma regra é usada em um delivery, as colunas **[!UICONTROL Consumed]** e **[!UICONTROL Remaining]** fornecem informações sobre a carga, conforme mostrado abaixo:

   ![](assets/campaign_opt_create_capacity_03.png)

   Para obter mais informações, consulte [esta seção](#monitoring-consumption).

## Definindo a carga máxima {#defining-the-maximum-load}

Para definir a carga máxima, você precisa definir linhas de disponibilidade. Para fazer isso, duas opções estão disponíveis: você pode criar manualmente uma ou mais linhas de disponibilidade (consulte [Adicionar linhas de disponibilidade uma por uma](#adding-availability-lines-one-by-one)) ou criar intervalos de disponibilidade. A frequência desses períodos pode ser automatizada (consulte [Adicionar um conjunto de linhas de disponibilidade](#add-a-set-of-availability-lines)).

### Adicionando linhas de disponibilidade uma por uma {#adding-availability-lines-one-by-one}

To create an availability line, click the **[!UICONTROL Add]** button and select **[!UICONTROL Add an availability line]**. Insira o período de disponibilidade e a carga disponível.

![](assets/campaign_opt_create_capacity_02.png)

Adicione quantas linhas forem necessárias para atender a capacidade de processamento.

### Adicione um conjunto de linhas de disponibilidade {#add-a-set-of-availability-lines}

To define availability periods for a given time, click the **[!UICONTROL Add]** button and select the **[!UICONTROL Add a set of availability lines]** option. Indique uma duração para cada período e o número de períodos a serem criados.

Para automatizar a frequência de criação de página, clique no botão **[!UICONTROL Change]** e defina o cronograma do período.

![](assets/campaign_opt_create_capacity_07.png)

Por exemplo, vamos definir um agendamento para criar períodos de disponibilidade para todos os dias de trabalho com uma taxa de 10 chamadas por hora entre as 9h e as 17h. Para fazer isso, siga as etapas abaixo:

1. Selecione o tipo de periodicidade e os dias e horas durante o qual é válido:

   ![](assets/campaign_opt_create_capacity_08.png)

1. Indique as datas de validade:

   ![](assets/campaign_opt_create_capacity_09.png)

1. Verifique o agendamento antes de aprovar:

   ![](assets/campaign_opt_create_capacity_10.png)

O fluxo de trabalho **[!UICONTROL Forecasting]** cria automaticamente todas as linhas correspondentes.

![](assets/campaign_opt_create_capacity_12.png)

>[!NOTE]
>
>Recomendamos a criação de linhas de disponibilidade por meio de importações de arquivo. Esta guia permite visualizar e verificar linhas de consumo.

## Excluir mensagens quando o limite de capacidade é atingido {#exclude-messages-when-capacity-limit-reached}

As linhas de disponibilidade são somente para fins de informação. Para excluir mensagens em excesso, marque a **[!UICONTROL Exclude from the target messages in excess of capacity]** opção. Isso evita que a capacidade seja excedida. Para a mesma população que no exemplo anterior, o consumo e a capacidade restantes não devem exceder a quantidade inicial:

![](assets/campaign_opt_create_capacity_04.png)

O número de mensagens a serem processadas é dividido uniformemente no intervalo de disponibilidade definido. Isso é particularmente relevante para centrais de chamadas, pois seu número máximo de chamadas por dias é limitado. In the case of email deliveries, the **[!UICONTROL Do not limit instantaneous delivery capacity]** option lets you ignore this availability range and send your emails at the same time.

![](assets/campaign_opt_create_capacity_05.png)

>[!NOTE]
>
>No caso de uma sobrecarga, as mensagens salvas serão selecionadas de acordo com a fórmula definida nas propriedades de delivery.

![](assets/campaign_opt_create_capacity_06.png)

## Monitorando o consumo {#monitoring-consumption}

Por padrão, as regras de capacidade são somente para fins de indicação. Select the **[!UICONTROL Exclude messages in excess of capacity from the target]** option to prevent the defined load from being exceeded. Nesse caso, as mensagens em excesso serão excluídas automaticamente dos deliveries usando essa regra de tipologia.

Para monitorar o consumo, visualize os valores exibidos na coluna **[!UICONTROL Consumed]** da guia **[!UICONTROL Capacity]** na regra de tipologia.

![](assets/campaign_opt_create_capacity_04.png)

Para exibir linhas de consumo, clique na guia **[!UICONTROL Consumptions]** na regra.
