---
solution: Campaign Classic
product: campaign
title: Atualizar agregação
description: Saiba mais sobre a atividade de workflow Atualizar agregação
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: ht
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: ht
source-wordcount: '96'
ht-degree: 100%

---


# Atualizar agregação{#update-aggregate}

Agregados são definidos em nível de cubo para fins de relatório. Uma guia **[!UICONTROL Workflow]** está disponível ao configurar uma agregação.

Para obter mais informações sobre cubos e usando agregados no Adobe Campaign, consulte a [seção](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates) dedicada.

A atividade **[!UICONTROL Update aggregate]** permite selecionar o modo de atualização que será aplicado: completo ou parcial.

Por padrão, uma atualização completa é realizada durante cada cálculo. Para habilitar uma atualização parcial, selecione a opção relevante e defina as condições de atualização.

![](assets/s_advuser_cube_agregate_05.png)

**Prática recomendada**: uma atividade **[!UICONTROL Scheduler]** pode ser usada para especificar a frequência das atualizações de cálculo.

![](assets/s_advuser_cube_agregate_04.png)

