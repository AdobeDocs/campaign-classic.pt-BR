---
product: campaign
title: Atualizar agregado
description: Saiba mais sobre a atividade de fluxo de trabalho Atualizar agregado
feature: Workflows
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: 1635366b9e1302acd3d8997312bf07d5c1a68982
workflow-type: ht
source-wordcount: '123'
ht-degree: 100%

---

# Atualizar agregado{#update-aggregate}

![](../../assets/v7-only.svg)

Agregados são definidos em nível de cubo para fins de relatório. Uma guia **[!UICONTROL Workflow]** está disponível ao configurar uma agregação.

Agregações são úteis ao manipular grandes volumes de dados. Eles são atualizados automaticamente com base nas configurações definidas na caixa de workflow dedicada, para integrar os dados a serem coletados mais recentemente nos indicadores

As agregações são definidas na guia relevante de cada cubo.

![](assets/s_advuser_cube_agregate_01.png)


A atividade **[!UICONTROL Update aggregate]** permite selecionar o modo de atualização que será aplicado: completo ou parcial.

Por padrão, uma atualização completa é realizada durante cada cálculo. Para habilitar uma atualização parcial, selecione a opção relevante e defina as condições de atualização.

![](assets/s_advuser_cube_agregate_05.png)

**Prática recomendada**: uma atividade **[!UICONTROL Scheduler]** pode ser usada para especificar a frequência das atualizações de cálculo.

![](assets/s_advuser_cube_agregate_04.png)
