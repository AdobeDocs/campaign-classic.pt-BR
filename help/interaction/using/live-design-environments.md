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
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '450'
ht-degree: 100%

---


# Ambientes Live/Design{#live-design-environments}

## Princípio operacional {#operating-principle}

O Interaction opera com dois tipos de ambientes de oferta:

* Os ambientes de oferta **[!UICONTROL Design]** que incluem ofertas que estão sendo editadas e podem ser alteradas. Essas ofertas não foram feitas pelo ciclo de aprovação e não são entregues aos contatos.
* Os ambientes de oferta **[!UICONTROL Live]** que incluem ofertas aprovadas conforme são apresentadas aos contatos. As ofertas neste ambiente são somente leitura.

![](assets/offer_environments_overview_001.png)

Cada ambiente **[!UICONTROL Design]** está vinculado a um ambiente **[!UICONTROL Live]**. Quando uma oferta é concluída, suas regras de conteúdo e qualificação estão sujeitas a um ciclo de aprovação. Depois que este ciclo for concluído, a oferta relacionada será implantada automaticamente no ambiente **[!UICONTROL Live]**. A partir deste momento, ele estará disponível para delivery.

Por padrão, o Interaction vem com um ambiente **[!UICONTROL Design]** e um ambiente **[!UICONTROL Live]** vinculado a ele. Ambos os ambientes são pré-configurados para direcionar a tabela de recipients integrada.

>[!NOTE]
>
>Para direcionar outra tabela (tabela de visitantes para ofertas anônimas ou uma tabela de recipients específica), é necessário usar o assistente de target mapping para criar os ambientes. Para obter mais informações, consulte [Criação de um ambiente de ofertas](#creating-an-offer-environment).

![](assets/offer_environments_overview_002.png)

Os gerentes de oferta e os gerentes de delivery têm acesso a diferentes modos de exibição do ambiente. Os gerentes de delivery só podem visualizar o ambiente **[!UICONTROL Live]** de oferta e usar ofertas para entregá-los. Os gerentes de oferta podem visualizar e alterar o ambiente **[!UICONTROL Design]** e visualizar o ambiente **[!UICONTROL Live]**. Para obter mais informações, consulte [Perfis de operador](../../interaction/using/operator-profiles.md).

## Criação de um ambiente de oferta {#creating-an-offer-environment}

Por padrão, o Interaction vem com um ambiente pré-configurado para direcionar à tabela de recipients (ofertas identificadas). Se quiser direcionar outra tabela (tabela de visitantes para ofertas anônimas ou uma tabela de recipients específica), será necessário aplicar as seguintes configurações:

1. Coloque o cursor no nó **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]**. Clique com o botão direito do mouse no mapeamento de delivery que deseja usar (**[!UICONTROL Visitors]** se quiser usar ofertas anônimas) e selecione **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. Clique em **[!UICONTROL Next]** para prosseguir para a próxima tela no assistente, marque a caixa **[!UICONTROL Generate a storage schema for propositions]** e clique em **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >Se a caixa já estiver marcada, a desmarque e então, a marque novamente.

1. O Adobe Campaign cria dois ambientes (**[!UICONTROL Design]** e **[!UICONTROL Live]**) com informações de direcionamento do target mapping habilitado anteriormente. O ambiente é pré-configurado com as informações de definição de metas.

   Se ativado o mapeamento **[!UICONTROL Visitor]**, a caixa **[!UICONTROL Environment dedicated to incoming anonymous interactions]** é automaticamente marcada na guia **[!UICONTROL General]** do ambiente.

   Essa opção permite ativar funções específicas de interação anônima, especialmente quando configurar espaços de oferta de ambiente. Também é possível configurar opções que permitem alternar de um ambiente &quot;identificado&quot; para um ambiente &quot;anônimo&quot;.

   Por exemplo, é possível vincular um espaço de oferta de ambiente de recipient (contato identificado) com um espaço de oferta que corresponda a um ambiente de visitante (contato não identificado). Dessa forma, as diferentes ofertas serão disponibilizadas para o contato, dependendo de é identificado ou não. Para obter mais informações, consulte [Criação de espaços de oferta](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>Para obter mais informações sobre interações anônimas em um canal de entrada, consulte [Interações anônimas](../../interaction/using/anonymous-interactions.md).

