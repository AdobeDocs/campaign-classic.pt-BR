---
product: campaign
title: Gerenciamento de fluxos de trabalho
description: Gerenciamento de fluxos de trabalho
feature: Workflows, Configuration
role: Developer
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
TQID: 'https://experienceleague.adobe.com/dpHtLw4PYGg35t-ihmw9LGUSbjgeNloUhGXp9KPJaRU'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 11%
---
# Gerenciamento de fluxos de trabalho{#managing-workflows}



Por padrão, seus novos fluxos de trabalho são baseados em um modelo de fluxo de trabalho pré-configurado e baseado em uma tabela de destinatários (nms:recipient). Para que eles sejam baseados automaticamente na tabela personalizada de destinatários referenciados na opção **Nms_DefaultRcpSchema** (consulte a seção [Configuração da interface](../../configuration/using/configuring-the-interface.md)), você deve criar um novo modelo de fluxo de trabalho.

Crie um novo modelo através do nó **[!UICONTROL Resources > Templates > Workflow templates]**. Nas propriedades do template, as dimensões fornecidas correspondem à tabela de recipients externos.

Ao basear seus novos workflows em um template criado recentemente, sua tabela personalizada será selecionada por padrão para o targeting global e a dimensão de filtro do workflow.

Todas as atividades usadas em seu fluxo de trabalho usarão sua tabela personalizada sem precisar de configuração manual adicional.

Para obter mais informações sobre fluxos de trabalho, consulte [esta seção](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)
