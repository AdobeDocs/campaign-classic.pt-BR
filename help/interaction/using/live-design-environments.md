---
title: Ambientes Live/Design
seo-title: Ambientes Live/Design
description: Ambientes Live/Design
seo-description: null
page-status-flag: never-activated
uuid: 38ee2f6a-e446-4ac6-b962-40b648eeaf66
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 3cea2be4-4da4-4ebd-a241-1bbaa5abb16e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Ambientes Live/Design{#live-design-environments}

## Princípio operacional {#operating-principle}

O Interaction opera com dois tipos de ambientes de oferta:

* **[!UICONTROL Design]** oferecem ambientes que incluem ofertas que estão sendo editadas e podem ser alteradas. Essas ofertas não foram feitas pelo ciclo de aprovação e não são entregues aos contatos.
* **[!UICONTROL Live]** oferecem ambientes que incluem ofertas aprovadas conforme são apresentadas aos contatos. As ofertas neste ambiente são somente leitura.

![](assets/offer_environments_overview_001.png)

Cada **[!UICONTROL Design]** ambiente está ligado a um **[!UICONTROL Live]** ambiente. Quando uma oferta é concluída, suas regras de conteúdo e qualificação estão sujeitas a um ciclo de aprovação. Once this cycle is complete, the concerned offer is automatically deployed to the **[!UICONTROL Live]** environment. A partir deste momento, ele estará disponível para delivery.

By default, Interaction comes with a **[!UICONTROL Design]** environment and a **[!UICONTROL Live]** environment linked to it. Ambos os ambientes são pré-configurados para direcionar a tabela de recipients integrada.

>[!NOTE]
>
>Para direcionar outra tabela (tabela de visitantes para ofertas anônimas ou uma tabela de recipients específica), é necessário usar o assistente de target mapping para criar os ambientes. Para obter mais informações, consulte [Criação de um ambiente](#creating-an-offer-environment)de ofertas.

![](assets/offer_environments_overview_002.png)

Os gerentes de oferta e os gerentes de delivery têm acesso a diferentes modos de exibição do ambiente. Delivery managers can only view the **[!UICONTROL Live]** offer environment and use offers to deliver them. Offer managers can view and alter the **[!UICONTROL Design]** environment and view the **[!UICONTROL Live]** environment. For more on this, refer to [Operator profiles](../../interaction/using/operator-profiles.md).

## Criação de um ambiente de oferta {#creating-an-offer-environment}

Por padrão, o Interaction vem com um ambiente pré-configurado para direcionar à tabela de recipients (ofertas identificadas). Se quiser direcionar outra tabela (tabela de visitantes para ofertas anônimas ou uma tabela de recipients específica), será necessário aplicar as seguintes configurações:

1. Posicione o cursor no nó **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]** . Clique com o botão direito do mouse no mapeamento de entrega que deseja usar (**[!UICONTROL Visitors]** se quiser usar ofertas anônimas) e selecione **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. Clique para continuar **[!UICONTROL Next]** para a próxima tela no assistente, marque a **[!UICONTROL Generate a storage schema for propositions]** caixa e clique em **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >Se a caixa já estiver marcada, a desmarque e então, a marque novamente.

1. Adobe Campaign creates two environments (**[!UICONTROL Design]** and **[!UICONTROL Live]** ) with targeting information from the previously enabled target mapping. O ambiente é pré-configurado com as informações de definição de metas.

   Se você ativou o **[!UICONTROL Visitor]** mapeamento, a **[!UICONTROL Environment dedicated to incoming anonymous interactions]** caixa é automaticamente marcada na guia do ambiente **[!UICONTROL General]** .

   Essa opção permite ativar funções específicas de interação anônima, especialmente quando configurar espaços de oferta de ambiente. Também é possível configurar opções que permitem alternar de um ambiente &quot;identificado&quot; para um ambiente &quot;anônimo&quot;.

   Por exemplo, é possível vincular um espaço de oferta de ambiente de recipient (contato identificado) com um espaço de oferta que corresponda a um ambiente de visitante (contato não identificado). Dessa forma, as diferentes ofertas serão disponibilizadas para o contato, dependendo de é identificado ou não. Para obter mais informações, consulte [Criação de espaços](../../interaction/using/creating-offer-spaces.md)de oferta.

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>For more information on anonymous interactions on an inbound channel, refer to [Anonymous interactions](../../interaction/using/anonymous-interactions.md).

