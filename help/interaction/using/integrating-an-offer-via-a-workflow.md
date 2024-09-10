---
product: campaign
title: Integração de uma oferta via workflow
description: Integração de uma oferta via workflow
feature: Interaction, Offers, Workflows
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
exl-id: 33d318f3-1eb4-4c74-8c20-8b9f0442c7c3
source-git-commit: de9ff0b50d819038c97e8515ddb7d6cfeb4547a1
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 100%

---

# Integração de uma oferta via workflow{#integrating-an-offer-via-a-workflow}



Fora da atividade de entrega, várias atividades de workflows permitem definir a forma como as ofertas são apresentadas:

* Descrição da entrega
* Enriquecimento
* Mecanismo de oferta
* Ofertas por célula

## Delivery outline {#delivery-outline}

A atividade Descrição da entrega, disponível nos workflows da campanha, permite apresentar ofertas mencionadas em uma descrição da entrega na campanha atual em andamento.

1. Em um workflow, adicione uma atividade de descrição da entrega antes de adicionar uma atividade de entrega.
1. Na atividade de descrição da entrega, especifique a descrição que deseja usar.

   Para obter mais informações sobre especificação de descrição da entrega, consulte o guia [Campaign - MRM](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. Preencha os campos disponíveis de acordo com sua entrega.
1. Há dois casos possíveis:

   * Se desejar chamar o mecanismo de oferta, marque a caixa **[!UICONTROL Restrict the number of propositions selected]**. Especifique o espaço de oferta e o número de propostas que serão apresentadas na entrega.

     Os pesos da oferta e as regras de qualificação serão considerados pelo mecanismo de oferta.

   * Se não marcar a caixa, todas as ofertas na descrição da entrega serão apresentadas sem chamar o mecanismo de oferta.

   >[!NOTE]
   >
   >A pré-visualização leva em conta o número de ofertas especificadas na entrega. Ao executar um workflow, é o número especificado na descrição da entrega que é levada em conta.

   ![](assets/int_compo_offre_wf1.png)

## Enriquecimento {#enrichment}

A atividade de enriquecimento permite adicionar ofertas ou links para ofertas de destinatários de entrega.

>[!NOTE]
>
>Para obter mais informações sobre a atividade de enriquecimento, consulte a documentação dedicada no [Guia de workflows](../../workflow/using/enrichment.md).

Por exemplo, é possível enriquecer os dados de uma query de destinatário antes de uma entrega.

![](assets/int_enrichment_offer1.png)

Há dois métodos para especificar apresentações de oferta.

* Especificação de oferta ou de chamada de motor de oferta.
* Fazendo referência a um link para uma oferta.

### Especificação de oferta ou de chamada para o mecanismo de oferta {#specifying-an-offer-or-a-call-to-the-offer-engine}

Após configurar seu query (consulte o [Guia de workflows](../../workflow/using/query.md)):

1. Adicione e abra uma atividade de enriquecimento.
1. Na guia **[!UICONTROL Enrichment]**, selecione **[!UICONTROL Add data]**.
1. Selecione **[!UICONTROL An offer proposition]** nos tipos de dados para adicionar.

   ![](assets/int_enrichment_offer2.png)

1. Especifique um identificador e um rótulo para a proposta que será adicionada.
1. Especifique a seleção da oferta. Há duas opções possíveis para isso:

   * **[!UICONTROL Search for the best offer in a category]**: marque esta opção e especifique os parâmetros de chamada do mecanismo de oferta (espaços de oferta, categoria ou tema(s), data de contato, número de ofertas a serem mantidas). O mecanismo calculará automaticamente as ofertas para adicionar de acordo com esses parâmetros. Recomendamos completar o campo **[!UICONTROL Category]** ou o campo **[!UICONTROL Theme]**, em vez de ambos ao mesmo tempo.

     ![](assets/int_enrichment_offer3.png)

   * **[!UICONTROL A predefined offer]** : marque esta opção e especifique um espaço de ofertas, uma oferta específica e uma data de contato para configurar diretamente a oferta que deseja adicionar, sem chamar o mecanismo de oferta.

     ![](assets/int_enrichment_offer4.png)

1. Em seguida, configure uma atividade de entrega que corresponda ao canal escolhido. Para obter mais informações, consulte a seção [Inserção de uma apresentação de oferta em uma entrega](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery).

   >[!NOTE]
   >
   >O número de propostas disponíveis para pré-visualizar depende da configuração executada na atividade de enriquecimento, ao invés de qualquer configuração possível executada diretamente na entrega.

### Referenciar um link para uma oferta {#referencing-a-link-to-an-offer}

Também é possível referenciar um link para uma oferta em uma atividade de enriquecimento.

Para fazer isso, realize o seguinte processo:

1. Selecione **[!UICONTROL Add data]** na guia **[!UICONTROL Enrichment]** da atividade.
1. Na janela onde você escolhe o tipo de dados a serem adicionados, selecione **[!UICONTROL A link]**.
1. Selecione o tipo de link que deseja estabelecer, assim como seu target. Nesse caso, o target é o schema de oferta.

   ![](assets/int_enrichment_link1.png)

1. Especifique a ligação entre os dados da tabela de entrada na atividade de enriquecimento (aqui a tabela de destinatários) e a tabela de ofertas. Por exemplo, é possível vincular um código de oferta a um destinatário.

   ![](assets/int_enrichment_link2.png)

1. Em seguida, configure uma atividade de entrega que corresponda ao canal escolhido. Para obter mais informações, consulte a seção [Inserção de uma apresentação de oferta em uma entrega](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery).

   >[!NOTE]
   >
   >O número de propostas disponíveis para a pré-visualização depende da configuração realizada na entrega.

### Armazenamento de classificações e pesos de ofertas {#storing-offer-rankings-and-weights}

Por padrão, quando uma atividade de **enriquecimento** é usada para entrega de ofertas, suas classificações e seus pesos não são armazenados na tabela de propostas.

>[!NOTE]
>
>Lembre-se que a atividade **[!UICONTROL Offer engine]** armazena essas informações por padrão.

No entanto, é possível armazenar essas informações da seguinte maneira:

1. Crie uma chamada para o mecanismo de oferta em uma atividade de enriquecimento feita após uma query e antes de uma atividade de entrega. Consulte a seção [Especificação de uma oferta ou de uma chamada para o mecanismo de oferta](../../interaction/using/integrating-an-offer-via-a-workflow.md#specifying-an-offer-or-a-call-to-the-offer-engine). 
1. Na janela principal da atividade, selecione **[!UICONTROL Edit additional data...]**.

   ![](assets/ita_enrichment_rankweight_1.png)

1. Adicione as colunas **[!UICONTROL @rank]** para a classificação e **[!UICONTROL @weight]** para o peso da oferta.

   ![](assets/ita_enrichment_rankweight_2.png)

1. Confirme sua adição e salve seu workflow.

A entrega armazena automaticamente a classificação e o peso das ofertas. Essas informações estão visíveis na guia **[!UICONTROL Offers]** da entrega.

## Mecanismo de oferta {#offer-engine}

A atividade de **[!UICONTROL Offer engine]** também permite especificar uma chamada para o mecanismo de oferta antes da entrega.

Essa atividade funciona de acordo com o mesmo princípio que a atividade de enriquecimento com uma chamada de mecanismo, enriquecendo os dados da população de entrada com uma oferta calculada pelo mecanismo, antes de uma entrega.

![](assets/int_offerengine_activity2.png)

Após configurar seu query (consulte o [Guia de workflows](../../workflow/using/query.md)):

1. Adicione e abra uma atividade de **[!UICONTROL Offer engine]**.
1. Preencha os vários campos disponíveis para especificar a chamada para oferecer parâmetros de mecanismo (espaço de oferta, categoria ou tema(s), data de contato, número de ofertas a serem mantidas). O mecanismo calculará automaticamente as ofertas para adicionar de acordo com esses parâmetros.

   >[!NOTE]
   >
   >Aviso: se você usar essa atividade, somente as apresentações de oferta usadas na entrega serão armazenadas.

   ![](assets/int_offerengine_activity1.png)

1. Em seguida, configure uma atividade de entrega que corresponda ao canal escolhido. Para obter mais informações, consulte a seção [Inserção de uma apresentação de oferta em uma entrega](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery).

## Ofertas por célula {#offers-by-cell}

A atividade **[!UICONTROL Offers by cell]** permite distribuir a população de entrada (de uma consulta, por exemplo) em vários segmentos e especificar uma oferta a ser apresentada para cada um desses segmentos.

Para fazer isso, realize o seguinte processo:

1. Adicione a atividade **[!UICONTROL Offers by cell]** após especificar a população do target e, em seguida, a abra.
1. Na guia **[!UICONTROL General]**, selecione o espaço de ofertas no qual deseja apresentar as ofertas.
1. Na guia **[!UICONTROL Cells]**, especifique os diferentes subconjuntos usando o botão **[!UICONTROL Add]**:

   * Especifique a população de subconjunto usando o filtro disponível e as regras de limitação.
   * Em seguida, selecione a oferta que deseja apresentar ao subconjunto. As ofertas disponíveis são aquelas elegíveis no ambiente de oferta que foi selecionado na etapa anterior.

     ![](assets/int_offer_per_cell1.png)

1. Em seguida, configure uma atividade de entrega que corresponda ao canal escolhido. Para obter mais informações, consulte a seção [Inserção de uma apresentação de oferta em uma entrega](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery).
