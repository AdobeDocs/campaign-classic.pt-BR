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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 100%

---


# Definição do conteúdo condicional{#defining-a-conditional-content}

É possível documentar a exibição de itens ou páginas de relatório específicos.

Para tornar itens específicos condicionais, adapte suas configurações de visibilidade. Para obter mais informações, consulte [Exibição do item de condição](#conditioning-item-display).

Para exibir uma ou mais páginas condicionais, use uma atividade do tipo **[!UICONTROL Test]**. Para obter mais informações, consulte [Condições para exibição de página](#conditioning-page-display).

## Exibição do item de condição {#conditioning-item-display}

Para exibir parte de um relatório condicional, é preciso definir suas condições de visibilidade: se elas não forem atendidas, os itens não serão exibidos.

As condições de visibilidade podem depender do status do operador, nos itens selecionados ou inseridos na página do relatório.

Exemplos mostrando a exibição condicional de itens em uma página são fornecidos [nesta seção](../../web/using/form-rendering.md#defining-fields-conditional-display).

No exemplo a seguir, a condição de exibição depende do idioma:

![](assets/reporting_display_condition.png)

## Condições de exibição da página {#conditioning-page-display}

No gráfico de um relatório, a atividade **[!UICONTROL Test]** permite alterar a sequência de páginas dependendo de uma ou mais condições.

Essa atividade baseia-se no seguinte princípio operacional:

1. Coloque um **[!UICONTROL Test]** em um gráfico e faça a edição dele.
1. Clique no botão **[!UICONTROL Add]** para criar os vários casos possíveis.

   ![](assets/reporting_test_sample.png)

   Para cada caso, uma transição de saída é adicionada à atividade **[!UICONTROL Test]**.

   ![](assets/reporting_test_transitions.png)

1. Selecione **[!UICONTROL Enable default transition]** para adicionar uma transição, caso uma das condições configuradas não seja atendida.

   Para obter mais informações, consulte [esta seção](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).

Uma atividade **[!UICONTROL Test]** pode ser colocada no início do gráfico para condicionar a exibição, dependendo do contexto ou do perfil do operador, por exemplo.
