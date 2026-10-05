---
product: campaign
title: Atualizar agregado
description: Saiba mais sobre a atividade de fluxo de trabalho Atualizar agregado
feature: Workflows
hide: true
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
TQID: 'https://experienceleague.adobe.com/YnOd1mT0WQqXHVeFUXFoumzDHxSSlKE2tgGSQFrjBzQ'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 100%
---
# Atualizar agregado{#update-aggregate}



Agregados são definidos em nível de cubo para fins de relatório. Uma guia **[!UICONTROL Workflow]** está disponível ao configurar uma agregação.

Agregações são úteis ao manipular grandes volumes de dados. Eles são atualizados automaticamente com base nas configurações definidas na caixa de fluxo de trabalho dedicada, para integrar os dados a serem coletados mais recentemente nos indicadores

As agregações são definidas na guia relevante de cada cubo.

![](assets/s_advuser_cube_agregate_01.png)


A atividade **[!UICONTROL Update aggregate]** permite selecionar o modo de atualização que será aplicado: completo ou parcial.

Por padrão, uma atualização completa é realizada durante cada cálculo. Para habilitar uma atualização parcial, selecione a opção relevante e defina as condições de atualização.

![](assets/s_advuser_cube_agregate_05.png)

**Prática recomendada**: uma atividade **[!UICONTROL Scheduler]** pode ser usada para especificar a frequência das atualizações de cálculo.

![](assets/s_advuser_cube_agregate_04.png)

