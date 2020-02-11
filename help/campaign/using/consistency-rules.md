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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Regras de consistência{#consistency-rules}

## Sobre as regras de consistência {#about-consistency-rules}

O Adobe Campaign garante comunicações consistentes graças a um conjunto de regras contidas nas tipologias de campanha. Seu objetivo é controlar os deliveries enviados aos recipients, como volume, natureza, relevância etc.

As regras de **Capacidade** podem evitar sobrecarga na plataforma relacionada ao delivery de mensagens. Por exemplo, ofertas especiais que contenham um link de download não devem ser enviadas para muitas pessoas ao mesmo tempo, para evitar a saturação do servidor; as campanhas telefônicas não devem exceder a capacidade de processamento das centrais telefônicas, etc. For more on this, refer to [Controlling capacity](#controlling-capacity).

## Controlando a capacidade {#controlling-capacity}

Antes de enviar mensagens, você precisa garantir que sua organização tem a capacidade de processar o delivery (infraestrutura física), as respostas que o delivery pode gerar (mensagens de entrada) e o número de chamadas a serem feitas para entrar em contato com assinantes (capacidade de processamento da central de chamadas), por exemplo.

To do this, you need to create **[!UICONTROL Capacity]** typology rules.

No exemplo a seguir, criamos uma regra de tipologia para uma campanha de fidelidade de telefone. Restringimos o número de mensagens a 20 por dia, ou seja, a capacidade diária de processamento de uma central de chamadas. Uma vez que a regra tenha sido aplicada a dois deliveires, poderemos monitorar o consumo por meio de logs.

Para projetar uma nova regra de capacidade, siga as etapas abaixo:

1. No **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** nó, clique em **[!UICONTROL New]**.
1. Selecione um tipo de **[!UICONTROL Capacity]** regra.

   ![](assets/campaign_opt_create_capacity_01.png)

1. In the **[!UICONTROL Capacity]** tab, create the availability lines: in our example, these are time periods during which calls can be made. Selecione um período de 24 horas e insira 150 na quantidade inicial, o que significa que a central de chamadas é capaz de atender 150 chamadas por dia.

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >As linhas de disponibilidade são somente para fins de informação. Caso precise excluir mensagens quando o limite de capacidade for atingido, consulte [esta seção](#exclude-messages-when-capacity-limit-reached).

1. Associe esta regra a uma tipologia e, em seguida, faça referência à tipologia em seu delivery para aplicar essa regra de capacidade. Para obter mais informações, consulte [esta seção](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery).
1. You can monitor consumption from the rule **[!UICONTROL Consumptions]** and **[!UICONTROL Capacity]** tabs.

   When a rule is used in a delivery, the **[!UICONTROL Consumed]** and **[!UICONTROL Remaining]** columns provide information on the load, as shown below:

   ![](assets/campaign_opt_create_capacity_03.png)

   Para obter mais informações, consulte [esta seção](#monitoring-consumption).

## Definindo a carga máxima {#defining-the-maximum-load}

Para definir a carga máxima, você precisa definir linhas de disponibilidade. To do this, two options are available: you can manually create one or more availability lines (refer to [Adding availability lines one by one](#adding-availability-lines-one-by-one)) or create availability ranges. A frequência desses períodos de tempo pode ser automatizada (consulte [Adicionar um conjunto de linhas](#add-a-set-of-availability-lines)de disponibilidade).

### Adicionando linhas de disponibilidade uma por uma {#adding-availability-lines-one-by-one}

Para criar uma linha de disponibilidade, clique no **[!UICONTROL Add]** botão e selecione **[!UICONTROL Add an availability line]**. Insira o período de disponibilidade e a carga disponível.

![](assets/campaign_opt_create_capacity_02.png)

Adicione quantas linhas forem necessárias para atender a capacidade de processamento.

### Adicione um conjunto de linhas de disponibilidade {#add-a-set-of-availability-lines}

Para definir períodos de disponibilidade para um determinado horário, clique no **[!UICONTROL Add]** botão e selecione a **[!UICONTROL Add a set of availability lines]** opção. Indique uma duração para cada período e o número de períodos a serem criados.

To automate the frequency of page creation, click the **[!UICONTROL Change]** button and define time period scheduling.

![](assets/campaign_opt_create_capacity_07.png)

Por exemplo, vamos definir um agendamento para criar períodos de disponibilidade para todos os dias de trabalho com uma taxa de 10 chamadas por hora entre as 9h e as 17h. Para fazer isso, siga as etapas abaixo:

1. Selecione o tipo de periodicidade e os dias e horas durante o qual é válido:

   ![](assets/campaign_opt_create_capacity_08.png)

1. Indique as datas de validade:

   ![](assets/campaign_opt_create_capacity_09.png)

1. Verifique o agendamento antes de aprovar:

   ![](assets/campaign_opt_create_capacity_10.png)

The **[!UICONTROL Forecasting]** workflow automatically creates all matching lines.

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

Por padrão, as regras de capacidade são somente para fins de indicação. Selecione a **[!UICONTROL Exclude messages in excess of capacity from the target]** opção para impedir que a carga definida seja excedida. Nesse caso, as mensagens em excesso serão excluídas automaticamente dos deliveries usando essa regra de tipologia.

To monitor consumptions, view the values displayed in the **[!UICONTROL Consumed]** column of the **[!UICONTROL Capacity]** tab in the typology rule.

![](assets/campaign_opt_create_capacity_04.png)

To view consumption lines, click the **[!UICONTROL Consumptions]** tab in the rule.
