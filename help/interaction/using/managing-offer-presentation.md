---
product: campaign
title: Gestão de apresentação de ofertas
description: Gestão de apresentação de ofertas
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: 6158ffaa-cb08-4f77-82b8-b3e5e1bf7fd7
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 98%

---

# Gestão de apresentação de ofertas{#managing-offer-presentation}

![](../../assets/v7-only.svg)

## Visão geral das regras de apresentação {#presentation-rules-overview}

A interação permite controlar o fluxo de apresentações de oferta usando regras de apresentação. Essas regras, que são específicas à Interação, são regras de tipologia. Elas permitem excluir ofertas com base no histórico de apresentações já feitas a um recipient. Eles são referenciados no ambiente

## Criação e referência a uma regra de apresentação de oferta {#creating-and-referencing-an-offer-presentation-rule}

1. Vá para o nó **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]**.
1. Crie uma regra de tipologia e escolha o tipo **[!UICONTROL Offer presentation]**.

   ![](assets/offer_typology_001.png)

1. Especifique o canal no qual a regra será aplicada:

   ![](assets/offer_typology_002.png)

1. Configure os critérios de aplicação da regra. Para obter mais informações, consulte [Configurações da regra de apresentação](#presentation-rule-settings).
1. Vá para o nó **[!UICONTROL Administration]** > **[!UICONTROL Campaign execution]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typologies]** e crie uma tipologia que irá agrupar todos os tipos de regras **[!UICONTROL Offer presentation]**.

   ![](assets/offer_typology_003.png)

1. Depois da criação da tipologia, coloque o cursor nas regras de tipologia e as agrupe na tipologia recém-criada.

   ![](assets/offer_typology_004.png)

1. No seu ambiente de oferta, faça referência à tipologia usando a lista suspensa.

   ![](assets/offer_typology_005.png)

## Configurações da regra de apresentação {#presentation-rule-settings}

### Critérios de aplicação {#application-criteria-}

Os critérios de aplicação disponíveis na guia **[!UICONTROL General]** permitem especificar as ofertas às quais a regra de apresentação será aplicada. Para fazer isso, é necessário criar um query e escolher as ofertas relacionadas, conforme descrito abaixo.

1. Na regra de tipologia, clique no link **[!UICONTROL Edit the rule application conditions...]** para criar sua query.

   ![](assets/offer_typology_006.png)

1. Na janela de query, é possível aplicar um filtro nas ofertas às quais deseja aplicar uma regra de tipologia.

   Por exemplo, você pode selecionar uma categoria de oferta.

   ![](assets/offer_typology_008.png)

### Dimensões da oferta {#offer-dimensions}

Na guia **[!UICONTROL Offer presentation]**, você deve especificar as mesmas dimensões para a regra de apresentação como aquelas configuradas no ambiente.

O **[!UICONTROL Targeting dimension]** coincide com a tabela de recipients (por padrão: nms:recipients) que receberão as apresentações de oferta. O **[!UICONTROL Storage dimension]** coincide com a tabela que contém o histórico de apresentações vinculado ao targeting dimension (por padrão,:nms:propositionRcp).

![](assets/offer_typology_009.png)

>[!NOTE]
>
>Você também pode usar tabelas não padrão. Se quiser usar um targeting dimension específico, é necessário criar tabelas e um ambiente dedicado usando o targeting mapping. Para obter mais informações, consulte [Criação de um ambiente de ofertas](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

### Período {#period}

Este é um período de deslizamento que começa na data de apresentação da oferta. Ele define um limite temporal para a validade de apresentações de oferta. A regra não se aplica às apresentações de oferta feitas fora deste período.

O período começa **n** dias antes da data de apresentação e termina **n** dias depois, onde **n** corresponde ao número inserido no campo **[!UICONTROL Period considered]**:

* Para espaços de entrada, a data da apresentação é a data de apresentação da oferta.
* Para espaços de saída, a data da proposta é a data de contato do delivery (por exemplo, a data de delivery inserida em um workflow para construção do target).

Use as setas para alterar o número de dias ou insira um período diretamente (&quot;2d 6h&quot;, por exemplo).

![](assets/offer_typology_010.png)

### Número de apresentações {#number-of-propositions}

É possível definir o número mais alto de apresentações que podem ser feitas antes que a(s) oferta(s) relacionada(s) seja/sejam excluída(s).

Use as setas para modificar o número de apresentações de ofertas:

![](assets/offer_typology_011.png)

## Definição de apresentações e recipients {#defining-propositions-and-recipients}

A seção **[!UICONTROL Propositions to count]** permite especificar os recipients e as apresentações que levarão à exclusão das ofertas definidas na guia **[!UICONTROL General]** se aparecerem um determinado número de vezes no histórico de apresentações.

### Filtragem de apresentações {#filtering-propositions}

Você pode selecionar critérios de filtragem para excluir apresentações com base no canal, as ofertas relacionadas ou o status das apresentações atribuídas anteriormente.

![](assets/offer_typology_014.png)

Esses critérios representam as aplicações mais frequentes das regras de apresentação. Para usar outros critérios, é possível criar uma query usando o link **[!UICONTROL Limit propositions...]**. Para obter mais informações, consulte a seção [Criação de uma consulta nas apresentações](#creating-a-query-on-propositions).

* **Filtro no canal**

   **[!UICONTROL On the same channel only]**: permite excluir apresentações de oferta no canal especificado na guia **[!UICONTROL General]**.

   Por exemplo, o canal especificado para a regra na guia **[!UICONTROL General]** é email. Se as ofertas que a regra se aplica até agora forem oferecidas apenas no canal da Web, o motor de interação pode apresentar as ofertas em um delivery de email. No entanto, uma vez que as ofertas tenham sido apresentadas por email, o motor de interação escolherá um canal diferente para apresentar as ofertas.

   >[!NOTE]
   >
   >Estamos falando sobre o canal e não o espaço. Se a regra precisar excluir uma oferta no canal da Web, a oferta destinada a ser apresentada em um site em dois espaços (em um banner e no corpo da página, por exemplo), não será exibida no site se já tiver sido apresentada antes.
   >
   >Para um workflow envolvendo a apresentação, as regras são devidamente levadas em conta se estiverem configuradas em **[!UICONTROL All channels]**.

* **Filtro na oferta**

   Esse filtro permite restringir as apresentações de oferta a serem contadas para conjuntos específicos de ofertas.

   **[!UICONTROL All offers]** : valor padrão. Nenhum filtro é aplicado às ofertas.

   **[!UICONTROL Offer being presented]**: a oferta especificada na guia **[!UICONTROL General]** é excluída se já tiver sido apresentada.

   **[!UICONTROL Offers from the same category]**: a oferta será excluída se uma oferta da mesma categoria já tiver sido apresentada.

   **[!UICONTROL The offers which the rule applies to]**: quando várias ofertas são definidas na guia **[!UICONTROL General]**, cada apresentação de oferta desse conjunto de ofertas é considerada e resulta na exclusão de todas as ofertas se o limite de apresentações for atingido.

   Por exemplo, as ofertas 2, 3 e 5 são definidas na guia **[!UICONTROL General]**. O número máximo de apresentações é definido como 2. Se as ofertas 2 e 5 forem apresentadas uma vez, o número de apresentações será 2. Como resultado, a oferta 3 nunca será apresentada.

* **Filtro no status da apresentação**

   Esse filtro permite escolher os status mais frequentes para que as apresentações de oferta sejam consideradas no histórico de apresentações.

   **[!UICONTROL Regardless of the proposition status]** : valor padrão. Nenhum filtro é aplicado ao status da apresentação.

   **[!UICONTROL Accepted or rejected propositions]**: permite excluir ofertas apresentadas anteriormente que foram aceitas ou rejeitadas.

   **[!UICONTROL Accepted propositions]**: permite excluir ofertas apresentadas anteriormente que foram aceitas.

   **[!UICONTROL Rejected propositions]**: permite excluir ofertas apresentadas anteriormente que foram rejeitadas.

### Definição de recipients {#defining-recipients}

Para especificar os recipients, clique no link **[!UICONTROL Edit the query from the targeting dimension...]** e selecione os recipients relacionados à regra.

![](assets/offer_typology_012.png)

### Criação de um query em apresentações {#creating-a-query-on-propositions}

Para especificar as apresentações que serão contadas por meio de uma query, clique no link **[!UICONTROL Limit propositions...]** e especifique os critérios que serão considerados.

No exemplo a seguir, as apresentações a serem contadas após duas apresentações são aquelas na categoria **Ofertas especiais**, para o espaço **Call center**, com um peso abaixo de **20**.

![](assets/offer_typology_013.png)
