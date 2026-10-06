---
product: campaign
title: Aguardar
description: Saiba mais sobre a atividade de fluxo de trabalho Aguardar
feature: Workflows
hide: true
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
TQID: 'https://experienceleague.adobe.com/sQ3GwMFQnhy6eOmFSfMUwT8Z3UE0p4cHLAjr8CjS2FM'
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
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 100%
---
# Aguardar{#wait}



Uma atividade **Wait** ativa sua transição após um atraso de tempo de qualquer valor entre alguns segundos até vários meses. Uma tarefa de espera não bloqueia a execução de outras tarefas; o fluxo de trabalho pode executar tarefas em paralelo enquanto esta tarefa está pendente.

É possível inserir o rótulo e o tempo de espera usando o editor, como no exemplo abaixo:

![](assets/edit_wait.png)

No campo **[!UICONTROL Duration]**, o valor pode ser expresso na unidade de sua escolha: (de acordo com as configurações regionais do operador):

* Se as configurações regionais não forem especificadas: **s** para segundos, **m** para minutos, **h** para horas, **d** para dias e **y** para anos. No momento da aprovação, o valor é convertido automaticamente para a unidade mais legível.

  A unidade padrão é dia (**d**).

* Enquanto que, por exemplo, se as configurações regionais forem definidas como &quot;Français&quot;: **s** para segundos, **mn** para minutos, **h** para horas, **j** para dias, **m** para meses e **a** para anos. No momento da aprovação, o valor é convertido automaticamente na unidade mais legível, como no exemplo acima, **90s** foi convertido para **1mn 30s**.

  A unidade padrão é dia (**d**).

