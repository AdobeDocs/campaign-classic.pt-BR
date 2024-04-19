---
product: campaign
title: Escopo de simulação
description: Escopo de simulação
feature: Interaction, Offers
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: 4f6b3de2-3fdf-441d-925d-476e20e75c6f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: ht
source-wordcount: '247'
ht-degree: 100%

---

# Escopo de simulação{#simulation-scope}



## Definição do escopo {#definition-of-the-scope}

Abra a guia **[!UICONTROL Scope]** para escolher as configurações.

Os seguintes itens são obrigatórios:

* Categoria de ambiente ou oferta.
* Espaço de oferta.
* Data de contato. Ofertas não qualificadas na data de contato não são consideradas.
* População do target.

  Se não configurar um filtro no target, toda a tabela de destinatários será levada em conta.

* Número de propostas a serem simuladas por target.

  O destinatário receberá muitas propostas. Por exemplo, se inserir 5, cada destinatário receberá no máximo 5 propostas de oferta.

  ![](assets/offer_simulation_009.png)

Para refinar as ofertas a serem consideradas para a simulação, é possível adicionar um ou vários temas (especificados anteriormente nas categorias).

Também é possível optar por realizar a simulação em todas as ofertas ou apenas aquelas que estão online. Alguns filtros permitem alterar sua seleção se desejar.

>[!NOTE]
>
>É necessário especificar uma data de contato. Isso permite que o mecanismo do Interaction classifique as ofertas no ambiente ou categoria selecionada. Se nenhuma data estiver configurada, a simulação levantará um erro.

## Adição de eixos de relatórios {#adding-reporting-axes}

É possível aprimorar a análise da simulação adicionando eixos de relatórios no target ou nas próprias ofertas por meio da guia **[!UICONTROL Calculations]**.

Para fazer isso, clique no botão **[!UICONTROL Add]** e selecione os campos apropriados. Os eixos serão usados para calcular a simulação e são exibidos no relatório de análise. Para obter mais informações, consulte [Rastreamento de simulação](../../interaction/using/simulation-tracking.md).

![](assets/offer_simulation_011.png)
