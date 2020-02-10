---
title: Escopo de simulação
seo-title: Escopo de simulação
description: Escopo de simulação
seo-description: null
page-status-flag: never-activated
uuid: d3145926-0a7e-455f-9b93-55be1b2a0518
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: simulating-offers
discoiquuid: ef658468-e20b-45d9-a714-c152e55c1c79
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Escopo de simulação{#simulation-scope}

## Definição do escopo {#definition-of-the-scope}

Open the **[!UICONTROL Scope]** tab to choose your settings.

Os seguintes itens são obrigatórios:

* Categoria de ambiente ou oferta.
* Espaço de oferta.
* Data de contato. Ofertas não qualificadas na data de contato não são consideradas.
* População do target.

   Se não configurar um filtro no target, toda a tabela de recipients será levada em conta.

* Número de propostas a serem simuladas por target.

   O recipient receberá muitas propostas. Por exemplo, se inserir 5, cada recipient receberá no máximo 5 propostas de oferta.

   ![](assets/offer_simulation_009.png)

Para refinar as ofertas a serem consideradas para a simulação, é possível adicionar um ou vários temas (especificados anteriormente nas categorias).

Também é possível optar por realizar a simulação em todas as ofertas ou apenas aquelas que estão online. Alguns filtros permitem alterar sua seleção se desejar.

>[!NOTE]
>
>É necessário especificar uma data de contato. Isso permite que o mecanismo do Interaction classifique as ofertas no ambiente ou categoria selecionada. Se nenhuma data estiver configurada, a simulação levantará um erro.

## Adição de eixos de relatórios {#adding-reporting-axes}

You can enhance the simulation analysis by adding reporting axes on the target or the offers themselves via the **[!UICONTROL Calculations]** tab.

To do this, click the **[!UICONTROL Add]** button and choose the appropriate fields. Os eixos serão usados para calcular a simulação e são exibidos no relatório de análise. For more on this, refer to [Simulation tracking](../../interaction/using/simulation-tracking.md).

![](assets/offer_simulation_011.png)

