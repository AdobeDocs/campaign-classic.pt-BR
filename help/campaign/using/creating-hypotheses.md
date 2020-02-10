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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Criar hipóteses{#creating-hypotheses}

Há várias possibilidades para criar/vincular hipóteses a uma oferta de campanha ou delivery:

* Via the **[!UICONTROL Measurement hypotheses]** folder by creating a new hypothesis based on an existing template and linking it to an existing delivery.
* Por meio da guia **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** em uma campanha.
* Via the **[!UICONTROL Measurement]** option of a delivery created from a campaign.

A hipótese só poderá ser calculada depois que a campanha de marketing tiver sido iniciada e os recipients tiverem recebido o delivery. Se a hipótese for baseada em uma apresentação da oferta, a última necessidade deverá ser apresentada e ainda estar ativa. Offer and delivery hypotheses are created via the **[!UICONTROL Measurement hypotheses]** folder and are based on a hypothesis template. No entanto, é possível fazer referência a uma hipótese diretamente no delivery ou na campanha antes do início dela. In this case, the hypotheses will be calculated automatically once the marketing campaign is launched, based on execution settings (for more on this, refer to [Hypothesis template execution settings](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)).

## Criar uma hipótese em tempo real {#creating-a-hypothesis-on-the-fly-on-a-delivery}

Para criar uma hipótese em um delivery existente, aplique o seguinte processo:

>[!NOTE]
>
>Esta operação é possível somente para envios pendentes.

1. Na árvore do Adobe Campaign, vá para **[!UICONTROL Campaign management > Measurement hypotheses]**.
1. Click the **[!UICONTROL New]** button or right-click on the list of hypotheses and select **[!UICONTROL New]** in the drop-down list.

   ![](assets/response_hypothesis_instance_creation_002.png)

1. In the hypothesis window, select a previously created template (refer to [Hypothesis templates](../../campaign/using/hypothesis-templates.md)).

   ![](assets/response_hypothesis_instance_creation_003.png)

   É exibido na tela o contexto da hipótese como definido no template selecionado.

   >[!NOTE]
   >
   >As configurações definidas no template e invisíveis nesta etapa também são mantidas na memória e reatribuído à hipótese em andamento.

   ![](assets/response_hypothesis_instance_creation_004.png)

1. Selecione o delivery para o qual deseja criar uma hipótese.

   ![](assets/response_hypothesis_instance_creation_005.png)

1. Você pode personalizar sua hipótese editando as guias **[!UICONTROL General]**, **[!UICONTROL Transactions]** e **[!UICONTROL Scope]** . Para obter mais informações, consulte [Criação de um modelo](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)de hipótese.
1. Start the hypothesis by clicking **[!UICONTROL Start]**.

   Um workflow é criado automaticamente para executar a mensuração. O nome é definido automaticamente de acordo com a configuração da hipótese.

   >[!CAUTION]
   >
   >You can access this if you have checked the **[!UICONTROL Keep execution workflow]** box.\
   >Essa opção deve ser ativada somente para fins de depuração, caso ocorra um erro durante a execução da hipótese. Os fluxos de trabalho gerados automaticamente são salvos na pasta **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Objects created automatically]** > **[!UICONTROL Campaign workflows]** no Adobe Campaign explorer.
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

1. Dependendo das suas necessidades, você pode criar um ou mais modelos de **[!UICONTROL Delivery]** tipo, conforme descrito em [Criação de um modelo de hipótese](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)
1. Criar uma campanha de marketing e os workflows para construção do target.
1. In the delivery window, click the **[!UICONTROL Delivery measurement]** icon.
1. Selecione o template da hipótese (a query configurada no template é exibida na janela de hipótese).

   The hypothesis will be calculated automatically once the campaign is finished, based on the dates configured in the model (refer to [Hypothesis template execution settings](../../campaign/using/hypothesis-templates.md#hypothesis-template-execution-settings)).

   ![](assets/response_hypothesis_instance_creation_008.png)

## Adicionar uma hipótese padrão aos envios para uma campanha {#adding-a-default-hypothesis-to-deliveries-for-a-campaign}

Você pode fazer referência diretamente a uma hipótese no nível da campanha. Nesse caso, a hipótese será vinculada automaticamente a todos os envios criados na campanha. Para fazer isso:

1. Go to the **[!UICONTROL Edit]** tab of the campaign.
1. In the measurement section, click the **[!UICONTROL Default hypotheses]** tab.

   ![](assets/response_hypothesis_instance_creation_010.png)

1. Click **[!UICONTROL Add]** and select a hypothesis template.

   ![](assets/response_hypothesis_instance_creation_011.png)

   Agora uma hipótese baseada nesse template é referenciada por padrão em cada novo delivery da campanha.

   ![](assets/response_hypothesis_instance_creation_012.png)

Os resultados da hipótese podem ser visualizados nas guias **[!UICONTROL General]** e **[!UICONTROL Reactions]** da hipótese (consulte Rastreamento [da](../../campaign/using/hypothesis-tracking.md)hipótese)

Para obter mais informações, consulte [Exemplo: criação de uma hipótese vinculada a uma entrega](#example--creating-a-hypothesis-linked-to-a-delivery).

## Criação de uma hipótese em uma oferta {#creating-a-hypothesis-on-an-offer}

Criar uma hipótese em uma apresentação da oferta é semelhante à criação em um delivery de forma instantânea. A hipótese pode ser executada desde que a oferta esteja ativa. O período de cálculo é baseado na data da apresentação da oferta. When the hypothesis lets you link a recipient to a purchase, the status of the offer proposition likely to be accepted can be changed automatically (for more on this, refer to [Transactions](../../campaign/using/hypothesis-templates.md#transactions)).

1. Crie um ou mais modelos de **[!UICONTROL Offer]** tipo conforme descrito em [Criação de um modelo](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)de hipótese.
1. Vá para o **[!UICONTROL Campaign management > Measurement hypotheses]** nó.
1. Create an **[!UICONTROL Offers]** type hypothesis by selecting the model created previously.

   ![](assets/response_hypothesis_instance_offer_001.png)

   A query criada no modelo aparece na janela.

   ![](assets/response_hypothesis_instance_offer_003.png)

1. Escolha a oferta para a qual deseja criar uma hipótese.

   ![](assets/response_hypothesis_instance_offer_004.png)

1. Refine a query, se necessário.
1. Click **[!UICONTROL Start]** to run the hypothesis.
1. Os resultados da hipótese podem ser visualizados em suas guias **[!UICONTROL General]** e **[!UICONTROL Reactions]** guias (consulte Rastreamento de [hipótese](../../campaign/using/hypothesis-tracking.md)).

   Hypotheses made on an offer are referenced in the **[!UICONTROL Measurement]** tab.

   ![](assets/response_hypothesis_instance_offer_007.png)

   If the **[!UICONTROL Update offer proposition status]** option was enabled in the hypothesis template, the status of the offer proposition is changed automatically, thereby providing feedback on the impact of the campaign (for more on this, refer to [Transactions](../../campaign/using/hypothesis-templates.md#transactions)).

## Exemplo: criar uma hipótese vinculada a um delivery {#example--creating-a-hypothesis-linked-to-a-delivery}

Neste exemplo, é criada uma hipótese vinculada a um delivery. Essa hipótese será baseada no modelo criado anteriormente (consulte [Exemplo: criação de um modelo de hipótese em uma entrega](../../campaign/using/hypothesis-templates.md#example--creating-a-hypothesis-template-on-a-delivery)). Em seguida, refine a query herdada do modelo para fazer uma hipótese em um artigo específico da tabela de compras.

1. Create a campaign and a delivery (For more on this, refer to [Creating a campaign](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   Nesse exemplo há um delivery do tipo mala direta.

1. Configurar um endereço de origem: o template de hipótese criado anteriormente foi configurado para levar um grupo de controle em consideração nos resultados da reação.

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >Para obter mais informações, consulte [Definição de um grupo](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)de controle.

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

1. Launch your targeting workflow and run the necessary checks until the campaign is finished (for more on this, refer to [Starting a delivery](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)).

   ![](assets/response_hypothesis_delivery_example_009.png)

1. In the Adobe Campaign tree, go to the **[!UICONTROL Campaign management > Measurement hypotheses]** node to check the indicators calculated by the hypothesis.

   ![](assets/response_hypothesis_delivery_example_010.png)

