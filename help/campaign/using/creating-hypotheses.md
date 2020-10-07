---
title: Criar hipóteses
seo-title: Criar hipóteses
description: Criar hipóteses
seo-description: null
page-status-flag: never-activated
uuid: 48b74772-473f-4fbc-a228-ce8e35a7b9ba
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: 0f73de0e-e589-4e39-9895-209dad75db75
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 89%

---


# Criar hipóteses{#creating-hypotheses}

Há várias possibilidades para criar/vincular hipóteses a uma oferta de campanha ou delivery:

* Na pasta **[!UICONTROL Measurement hypotheses]**, criando uma nova hipótese com base em um template existente e vinculando-a a um delivery existente.
* Via the **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** tab in a campaign.
* Com a opção **[!UICONTROL Measurement]** de um delivery criado de uma campanha.

A hipótese só poderá ser calculada depois que a campanha de marketing tiver sido iniciada e os recipients tiverem recebido o delivery. Se a hipótese for baseada em uma apresentação da oferta, a última necessidade deverá ser apresentada e ainda estar ativa. A oferta e o delivery são criados por meio da pasta **[!UICONTROL Measurement hypotheses]** e se baseiam em um template de hipótese. No entanto, é possível fazer referência a uma hipótese diretamente no delivery ou na campanha antes do início dela. Nesse caso, a hipótese é calculada automaticamente no momento em que a campanha de marketing se inicia, com base nas configurações de execução (para mais informações, consulte [Configurações de execução do template de hipótese](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)).

## Criar uma hipótese em tempo real {#creating-a-hypothesis-on-the-fly-on-a-delivery}

Para criar uma hipótese em um delivery existente, aplique o seguinte processo:

>[!NOTE]
>
>Esta operação é possível somente para envios pendentes.

1. In the Adobe Campaign tree, go to **[!UICONTROL Campaign management > Measurement hypotheses]**.
1. Clique no botão **[!UICONTROL New]** ou clique com o botão direito na lista de hipóteses e selecione **[!UICONTROL New]** na lista suspensa.

   ![](assets/response_hypothesis_instance_creation_002.png)

1. Na janela da hipótese, selecione um template criado anteriormente (consulte [Templates de hipóteses](../../campaign/using/hypothesis-templates.md)).

   ![](assets/response_hypothesis_instance_creation_003.png)

   É exibido na tela o contexto da hipótese como definido no template selecionado.

   >[!NOTE]
   >
   >As configurações definidas no template e invisíveis nesta etapa também são mantidas na memória e reatribuído à hipótese em andamento.

   ![](assets/response_hypothesis_instance_creation_004.png)

1. Selecione o delivery para o qual deseja criar uma hipótese.

   ![](assets/response_hypothesis_instance_creation_005.png)

1. You can personalize your hypothesis by editing the **[!UICONTROL General]**, **[!UICONTROL Transactions]** and **[!UICONTROL Scope]** tabs. Para obter mais informações, consulte [Criação de um template de hipótese](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model).
1. Comece a hipótese clicando em **[!UICONTROL Start]**.

   Um workflow é criado automaticamente para executar a mensuração. O nome é definido automaticamente de acordo com a configuração da hipótese.

   >[!CAUTION]
   >
   >You can access this if you have checked the **[!UICONTROL Keep execution workflow]** box.\
   >Essa opção deve ser ativada somente para fins de depuração, caso ocorra um erro durante a execução da hipótese. Workflows generated automatically are saved in the **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Objects created automatically]** > **[!UICONTROL Campaign workflows]** folder in the Adobe Campaign explorer.
   > 
   >Além disso, os workflows gerados automaticamente não devem ser modificados. Qualquer modificação eventual em outro lugar é desconsiderada para cálculos posteriores.
   >
   >Se essa opção está marcada, exclua o workflow após a execução.

   ![](assets/response_hypothesis_instance_creation_006.png)

   Quando o cálculo é concluído, os indicadores de mensuração são atualizados automaticamente.

   ![](assets/response_hypothesis_instance_creation_007.png)

1. Se necessário, altere as configurações e reinicie a hipótese.

## Referenciar uma hipótese em um delivery de campanha {#referencing-a-hypothesis-in-a-campaign-delivery}

É possível fazer referência a uma hipótese em uma campanha de marketing antes de ela ser iniciada. Nesse caso, a hipótese será iniciada automaticamente quando o delivery for enviado, com base nas configurações de execução definidas no template da hipótese. Para criar uma hipótese em um delivery, aplique o seguinte processo:

1. Dependendo das suas necessidades, você pode criar um ou mais templates do tipo **[!UICONTROL Delivery]**, conforme descrito em [Criação de um template de hipótese](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)
1. Criar uma campanha de marketing e os workflows para construção do target.
1. In the delivery window, click the **[!UICONTROL Delivery measurement]** icon.
1. Selecione o template da hipótese (a query configurada no template é exibida na janela de hipótese).

   A hipótese será calculada automaticamente quando a campanha for concluída com base nas datas configuradas no template (consulte [Configurações de execução do template de hipótese](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)).

   ![](assets/response_hypothesis_instance_creation_008.png)

## Adicionar uma hipótese padrão aos envios para uma campanha {#adding-a-default-hypothesis-to-deliveries-for-a-campaign}

Você pode fazer referência diretamente a uma hipótese no nível da campanha. Nesse caso, a hipótese será vinculada automaticamente a todos os envios criados na campanha. Para fazer isso:

1. Acesse a guia **[!UICONTROL Edit]** da campanha.
1. In the measurement section, click the **[!UICONTROL Default hypotheses]** tab.

   ![](assets/response_hypothesis_instance_creation_010.png)

1. Clique em **[!UICONTROL Add]** e selecione um template de hipótese.

   ![](assets/response_hypothesis_instance_creation_011.png)

   Agora uma hipótese baseada nesse template é referenciada por padrão em cada novo delivery da campanha.

   ![](assets/response_hypothesis_instance_creation_012.png)

Os resultados da hipótese podem ser exibidos nas guias **[!UICONTROL General]** e **[!UICONTROL Reactions]** (consulte [Rastreamento de hipótese](../../campaign/using/hypothesis-tracking.md))

Para obter mais informações, consulte [Exemplo: criação de uma hipótese vinculada a um delivery](#example--creating-a-hypothesis-linked-to-a-delivery).

## Criação de uma hipótese em uma oferta {#creating-a-hypothesis-on-an-offer}

Criar uma hipótese em uma apresentação da oferta é semelhante à criação em um delivery de forma instantânea. A hipótese pode ser executada desde que a oferta esteja ativa. O período de cálculo é baseado na data da apresentação da oferta. Quando a hipótese permite vincular um recipient a uma compra, o status da apresentação da oferta que provavelmente será aceita pode ser alterado automaticamente (para mais informações, consulte [Transações](../../campaign/using/hypothesis-templates.md#transactions)).

1. Crie um ou mais templates do tipo **[!UICONTROL Offer]**, conforme descrito em [Criação de um template de hipótese](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model).
1. Vá para o nó **[!UICONTROL Campaign management > Measurement hypotheses]**
1. Create an **[!UICONTROL Offers]** type hypothesis by selecting the model created previously.

   ![](assets/response_hypothesis_instance_offer_001.png)

   A query criada no modelo aparece na janela.

   ![](assets/response_hypothesis_instance_offer_003.png)

1. Escolha a oferta para a qual deseja criar uma hipótese.

   ![](assets/response_hypothesis_instance_offer_004.png)

1. Refine a query, se necessário.
1. Clique em **[!UICONTROL Start]** para executar a hipótese.
1. Os resultados da hipótese podem ser visualizados nas guias **[!UICONTROL General]** e **[!UICONTROL Reactions]** (consulte [Rastreamento de hipótese](../../campaign/using/hypothesis-tracking.md)).

   As hipóteses feitas em uma oferta são referenciadas na guia **[!UICONTROL Measurement]**.

   ![](assets/response_hypothesis_instance_offer_007.png)

   Se a opção **[!UICONTROL Update offer proposition status]** foi habilitada no template da hipótese, o status da apresentação da oferta é alterado automaticamente, fornecendo feedback sobre o impacto da campanha (para mais informações, consulte [Transações](../../campaign/using/hypothesis-templates.md#transactions)).

## Exemplo: criar uma hipótese vinculada a um delivery {#example--creating-a-hypothesis-linked-to-a-delivery}

Neste exemplo, é criada uma hipótese vinculada a um delivery. Essa hipótese será baseada no template criado anteriormente (consulte [Exemplo: criação de um template de hipótese em um delivery](../../campaign/using/hypothesis-templates.md#example--creating-a-hypothesis-template-on-a-delivery)). Em seguida, refine a query herdada do modelo para fazer uma hipótese em um artigo específico da tabela de compras.

1. Criar uma campanha e um delivery (Para obter mais informações, consulte [Criação de uma campanha](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   Nesse exemplo há um delivery do tipo mala direta.

1. Configurar um endereço de origem: o template de hipótese criado anteriormente foi configurado para levar um grupo de controle em consideração nos resultados da reação.

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >Para obter mais informações, consulte [Definição de um grupo de controle](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

1. Abra o **[!UICONTROL Direct mail delivery]** e clique no **[!UICONTROL Delivery measurement]** ícone e, em seguida, clique em **[!UICONTROL Add]**.

   ![](assets/response_hypothesis_delivery_example_002.png)

1. Escolha na lista suspensa o template de hipótese criado anteriormente.

   ![](assets/response_hypothesis_delivery_example_004.png)

   A query criada no modelo é exibida.

   ![](assets/response_hypothesis_delivery_example_005.png)

1. Click **[!UICONTROL Edit query...]** and refine the query by entering the product that the hypothesis will concern.

   ![](assets/response_hypothesis_delivery_example_006.png)

   You can check that the hypothesis is linked to the delivery in the **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** tab of the campaign.

   ![](assets/response_hypothesis_delivery_example_008.png)

1. Inicie o workflow para construção do target e execute as verificações necessárias até a conclusão da campanha (para mais informações, consulte [Iniciar um delivery](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)).

   ![](assets/response_hypothesis_delivery_example_009.png)

1. Na árvore do Adobe Campaign, acesse o nó **[!UICONTROL Campaign management > Measurement hypotheses]** para verificar os indicadores calculados pela hipótese.

   ![](assets/response_hypothesis_delivery_example_010.png)

