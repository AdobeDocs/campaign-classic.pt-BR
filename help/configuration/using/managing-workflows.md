---
product: campaign
title: Gerenciamento de workflows
description: Gerenciamento de workflows
feature: Workflows, Configuration
role: Data Engineer, Developer
badge-v8: label="Também se aplica à versão v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 14%

---

# Gerenciamento de workflows{#managing-workflows}



Por padrão, seus novos workflows são baseados em um template de workflow que foi pré-configurado e com base em uma tabela de recipient (nms:recipient). Para serem automaticamente baseados na tabela personalizada de recipients referenciados no **Nms_DefaultRcpSchema** (consulte [Configuração da interface](../../configuration/using/configuring-the-interface.md) ), você deve criar um novo template de workflow.

Crie um novo modelo por meio do **[!UICONTROL Resources > Templates > Workflow templates]** nó. Nas propriedades do template, as dimensões fornecidas correspondem à tabela de recipients externos.

Ao basear seus novos workflows em um template criado recentemente, sua tabela personalizada será selecionada por padrão para o targeting global e a dimensão de filtro do workflow.

Todas as atividades usadas em seu fluxo de trabalho usarão sua tabela personalizada sem precisar de configuração manual adicional.

Para obter mais informações sobre fluxos de trabalho, consulte [esta seção](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)
