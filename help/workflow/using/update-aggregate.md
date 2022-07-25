---
product: campaign
title: Atualizar agregado
description: Saiba mais sobre a atividade de fluxo de trabalho Atualizar agregado
feature: Workflows
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: ht
source-wordcount: '97'
ht-degree: 100%

---

# Atualizar agregado{#update-aggregate}

![](../../assets/v7-only.svg)

Agregados são definidos em nível de cubo para fins de relatório. Uma guia **[!UICONTROL Workflow]** está disponível ao configurar uma agregação.

Para obter mais informações sobre cubos e usando agregados no Adobe Campaign, consulte a [seção](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates) dedicada.

A atividade **[!UICONTROL Update aggregate]** permite selecionar o modo de atualização que será aplicado: completo ou parcial.

Por padrão, uma atualização completa é realizada durante cada cálculo. Para habilitar uma atualização parcial, selecione a opção relevante e defina as condições de atualização.

![](assets/s_advuser_cube_agregate_05.png)

**Prática recomendada**: uma atividade **[!UICONTROL Scheduler]** pode ser usada para especificar a frequência das atualizações de cálculo.

![](assets/s_advuser_cube_agregate_04.png)
