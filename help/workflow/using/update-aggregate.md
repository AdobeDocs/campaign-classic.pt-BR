---
title: Agregação de atualizações
seo-title: Agregação de atualizações
description: Agregação de atualizações
seo-description: null
page-status-flag: never-activated
uuid: 34ae42e1-da34-43be-b219-0b3b872177b3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 031f8d5d-940c-4a4c-97e7-ad4ef61983c1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Agregação de atualizações{#update-aggregate}

Agregados são definidos em nível de cubo para fins de relatório. A **[!UICONTROL Workflow]** tab is available when configuring an aggregate.

Para obter mais informações sobre cubos e usando agregados no Adobe Campaign, consulte a  [seção](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates) dedicada.

The **[!UICONTROL Update aggregate]** activity lets you select the update mode to apply: full or partial.

Por padrão, uma atualização completa é realizada durante cada cálculo. Para habilitar uma atualização parcial, selecione a opção relevante e defina as condições de atualização.

![](assets/s_advuser_cube_agregate_05.png)

**Boas práticas**: uma **[!UICONTROL Scheduler]** atividade pode ser usada para especificar a frequência das atualizações de cálculo.

![](assets/s_advuser_cube_agregate_04.png)

