---
product: campaign
title: Ambientes ao vivo/de design
description: Ambientes Live/Design
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: 965c4a6a-6535-454d-bd37-e9c8312b4d13
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: ht
source-wordcount: '447'
ht-degree: 100%

---

# Ambientes ao vivo/de design{#live-design-environments}



## Princípio operacional {#operating-principle}

O Interaction opera com dois tipos de ambientes de oferta:

* Os ambientes de oferta **[!UICONTROL Design]** que incluem ofertas que estão sendo editadas e podem ser alteradas. Essas ofertas não foram feitas pelo ciclo de aprovação e não são entregues aos contatos.
* Os ambientes de oferta **[!UICONTROL Live]** que incluem ofertas aprovadas conforme são apresentadas aos contatos. As ofertas neste ambiente são somente leitura.

![](assets/offer_environments_overview_001.png)

Cada ambiente **[!UICONTROL Design]** está vinculado a um ambiente **[!UICONTROL Live]**. Quando uma oferta é concluída, suas regras de conteúdo e qualificação estão sujeitas a um ciclo de aprovação. Depois que este ciclo for concluído, a oferta relacionada será implantada automaticamente no ambiente **[!UICONTROL Live]**. A partir deste momento, ele estará disponível para entrega.

Por padrão, o Interaction vem com um ambiente **[!UICONTROL Design]** e um ambiente **[!UICONTROL Live]** vinculado a ele. Ambos os ambientes são pré-configurados para ter como alvo a tabela de destinatários integrada.

>[!NOTE]
>
>Para direcionar outra tabela (tabela de visitantes para ofertas anônimas ou uma tabela de destinatários específica), é necessário usar o assistente de mapeamento de destinos para criar os ambientes. Para obter mais informações, consulte [Criação de um ambiente de ofertas](#creating-an-offer-environment).

![](assets/offer_environments_overview_002.png)

Os gerentes de oferta e os gerentes de entrega têm acesso a diferentes modos de exibição do ambiente. Os gerentes de delivery só podem visualizar o ambiente **[!UICONTROL Live]** de oferta e usar ofertas para entregá-los. Os gerentes de oferta podem visualizar e alterar o ambiente **[!UICONTROL Design]** e visualizar o ambiente **[!UICONTROL Live]**. Para obter mais informações, consulte [Perfis de operador](../../interaction/using/operator-profiles.md).

## Criação de um ambiente de oferta {#creating-an-offer-environment}

Por padrão, o Interaction vem com um ambiente pré-configurado para direcionar a tabela de destinatários (ofertas identificadas). Se quiser direcionar outra tabela (tabela de visitantes para ofertas anônimas ou uma tabela de destinatários específica), será necessário aplicar as seguintes configurações:

1. Coloque o cursor no nó **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]**. Clique com o botão direito do mouse no mapeamento de entrega que deseja usar (**[!UICONTROL Visitors]** se quiser usar ofertas anônimas) e selecione **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. Clique em **[!UICONTROL Next]** para passar para a próxima tela do assistente, marque a caixa **[!UICONTROL Generate a storage schema for propositions]** e clique em **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >Se a caixa já estiver marcada, a desmarque e então, a marque novamente.

1. O Adobe Campaign cria dois ambientes (**[!UICONTROL Design]** e **[!UICONTROL Live]**) com informações de direcionamento do target mapping habilitado anteriormente. O ambiente é pré-configurado com as informações de definição de metas.

   Se ativado o mapeamento **[!UICONTROL Visitor]**, a caixa **[!UICONTROL Environment dedicated to incoming anonymous interactions]** é automaticamente marcada na guia **[!UICONTROL General]** do ambiente.

   Essa opção permite ativar funções específicas de interação anônima, especialmente quando configurar espaços de oferta de ambiente. Também é possível configurar opções que permitem alternar de um ambiente &quot;identificado&quot; para um ambiente &quot;anônimo&quot;.

   Por exemplo, é possível vincular um espaço de oferta de ambiente de destinatário (contato identificado) com um espaço de oferta que corresponda a um ambiente de visitante (contato não identificado). Dessa forma, as diferentes ofertas serão disponibilizadas para o contato, dependendo se ele for identificado ou não. Para obter mais informações, consulte [Criação de espaços de oferta](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>Para obter mais informações sobre interações anônimas em um canal de entrada, consulte [Interações anônimas](../../interaction/using/anonymous-interactions.md).
