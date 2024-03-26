---
product: campaign
title: Criar um filtro
description: Saiba como criar um filtro ao executar consultas
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
feature: Query Editor, Workflows
exl-id: 297ea1e1-39ef-4b99-aaaa-9e88611fb1bf
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 93%

---

# Criar um filtro {#creating-a-filter}



Os filtros disponíveis no Adobe Campaign são definidos por meio das condições de filtro que são criadas usando o mesmo modo operacional que as queries.

>[!NOTE]
>
>Para saber mais sobre criação de filtros, consulte [esta seção](../../platform/using/filtering-options.md).

O nó **[!UICONTROL Administration > Configuration > Predefined filters]** contém todos os filtros usados nas listas e visões gerais.

Por exemplo, a lista de operadores pode ser filtrada por **[!UICONTROL Active accounts]**:

![](assets/query_editor_filter_sample_1.png)

O filtro correspondente contém a consulta no valor **[!UICONTROL Account disabled]** do schema **[!UICONTROL Operators]**:

![](assets/query_editor_filter_sample_2.png)

Para a mesma lista, o filtro **[!UICONTROL By login or label]** permite filtrar os dados na lista com base no valor inserido no campo de filtro:

![](assets/query_editor_filter_sample_3.png)

Ele é construído da seguinte maneira:

![](assets/query_editor_filter_sample_4.png)

Para corresponder às condições do filtro, a conta do operador deve verificar uma das seguintes condições:

* Seu rótulo contém os caracteres inseridos no campo de entrada,
* O nome do operador contém os caracteres inseridos no campo de entrada,
* O conteúdo da área de descrição contém os caracteres inseridos no campo de entrada.

>[!NOTE]
>
>A função **[!UICONTROL Upper]** permite desativar a função com diferenciação de maiúsculas e minúsculas.

A coluna **[!UICONTROL Taken into account if]** permite definir os critérios do aplicativo para essas condições de filtro. Aqui, os caracteres **$(/tmp/@text)** representam o conteúdo do campo de entrada vinculado ao filtro:

![](assets/query_editor_filter_sample_5.png)

Aqui, **$(/tmp/@text)=&#39;agency&#39;**

A variável **$(/tmp/@text)!=&#39;&#39;** A expressão aplica cada condição quando o campo de entrada não está vazio.
