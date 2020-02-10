---
title: Definição do conteúdo condicional
seo-title: Definição do conteúdo condicional
description: Definição do conteúdo condicional
seo-description: null
page-status-flag: never-activated
uuid: 2b49958d-6429-445d-a7dc-caaca072f4e4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0ca5e0f6-cc81-4da9-aecf-a095cc1a19f9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Definição do conteúdo condicional{#defining-a-conditional-content}

É possível documentar a exibição de itens ou páginas de relatório específicos.

Para tornar itens específicos condicionais, adapte suas configurações de visibilidade. For more on this, refer to [Conditioning item display](#conditioning-item-display).

To make the display of one or more pages conditional, use a **[!UICONTROL Test]** type activity. Para obter mais informações, consulte [Condições para exibição de página](#conditioning-page-display).

## Exibição do item de condição {#conditioning-item-display}

Para exibir parte de um relatório condicional, é preciso definir suas condições de visibilidade: se elas não forem atendidas, os itens não serão exibidos.

As condições de visibilidade podem depender do status do operador, nos itens selecionados ou inseridos na página do relatório.

Exemplos mostrando a exibição condicional de itens em uma página são fornecidos [nesta seção](../../web/using/form-rendering.md#defining-fields-conditional-display).

No exemplo a seguir, a condição de exibição depende do idioma:

![](assets/reporting_display_condition.png)

## Condições de exibição da página {#conditioning-page-display}

In the chart of a report, the **[!UICONTROL Test]** activity lets you change the sequence of pages depending on one or more conditions.

Essa atividade baseia-se no seguinte princípio operacional:

1. Place a **[!UICONTROL Test]** in a chart and edit it.
1. Click the **[!UICONTROL Add]** button to create the various possible cases.

   ![](assets/reporting_test_sample.png)

   For each case, an output transition is added to the **[!UICONTROL Test]** activity.

   ![](assets/reporting_test_transitions.png)

1. Select the **[!UICONTROL Enable default transition]** to add a transition, in case one of the configured conditions isn&#39;t met.

   Para obter mais informações, consulte [esta seção](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).

A **[!UICONTROL Test]** activity can be placed at the start of the chart to condition the display depending on context or operator profile for instance.
