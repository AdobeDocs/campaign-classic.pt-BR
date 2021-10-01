---
product: campaign
title: Atualizar agregação
description: Saiba mais sobre a atividade de workflow Atualizar agregação
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: ht
source-wordcount: '96'
ht-degree: 100%

---

# Atualizar agregado{#update-aggregate}

![](../../assets/common.svg)

Agregados são definidos em nível de cubo para fins de relatório. Uma guia **[!UICONTROL Workflow]** está disponível ao configurar uma agregação.

Para obter mais informações sobre cubos e usando agregados no Adobe Campaign, consulte a [seção](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates) dedicada.

A atividade **[!UICONTROL Update aggregate]** permite selecionar o modo de atualização que será aplicado: completo ou parcial.

Por padrão, uma atualização completa é realizada durante cada cálculo. Para habilitar uma atualização parcial, selecione a opção relevante e defina as condições de atualização.

![](assets/s_advuser_cube_agregate_05.png)

**Prática recomendada**: uma atividade **[!UICONTROL Scheduler]** pode ser usada para especificar a frequência das atualizações de cálculo.

![](assets/s_advuser_cube_agregate_04.png)
