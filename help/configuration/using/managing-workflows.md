---
product: campaign
title: Gerenciamento de workflows
description: Gerenciamento de workflows
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 11%

---

# Gerenciamento de workflows{#managing-workflows}



Por padrão, seus novos workflows são baseados em um template de workflow que foi pré-configurado e com base em uma tabela de recipient (nms:recipient). Para serem automaticamente baseados na tabela personalizada de recipients referenciados no **Nms_DefaultRcpSchema** (consulte [Configuração da interface](../../configuration/using/configuring-the-interface.md) ), você deve criar um novo template de workflow.

Crie um novo modelo por meio do **[!UICONTROL Resources > Templates > Workflow templates]** nó. Nas propriedades do template, as dimensões fornecidas correspondem à tabela de recipients externos.

Ao basear seus novos workflows em um template criado recentemente, sua tabela personalizada será selecionada por padrão para o targeting global e a dimensão de filtro do workflow.

Todas as atividades usadas em seu fluxo de trabalho usarão sua tabela personalizada sem precisar de configuração manual adicional.

Para obter mais informações sobre fluxos de trabalho, consulte [esta seção](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)
