---
title: Agregação de atualizações
description: Saiba mais sobre a atividade de fluxo de trabalho Atualizar agregação
page-status-flag: never-activated
uuid: 34ae42e1-da34-43be-b219-0b3b872177b3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 031f8d5d-940c-4a4c-97e7-ad4ef61983c1
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 92%

---


# Agregação de atualizações{#update-aggregate}

Agregados são definidos em nível de cubo para fins de relatório. Uma guia **[!UICONTROL Workflow]** está disponível ao configurar uma agregação.

Para obter mais informações sobre cubos e usando agregados no Adobe Campaign, consulte a [seção](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates) dedicada.

A atividade **[!UICONTROL Update aggregate]** permite selecionar o modo de atualização que será aplicado: completo ou parcial.

Por padrão, uma atualização completa é realizada durante cada cálculo. Para habilitar uma atualização parcial, selecione a opção relevante e defina as condições de atualização.

![](assets/s_advuser_cube_agregate_05.png)

**Prática recomendada**: uma atividade **[!UICONTROL Scheduler]** pode ser usada para especificar a frequência das atualizações de cálculo.

![](assets/s_advuser_cube_agregate_04.png)

