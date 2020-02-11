---
title: Gerenciamento de fluxos de trabalho
seo-title: Gerenciamento de fluxos de trabalho
description: Gerenciamento de fluxos de trabalho
seo-description: null
page-status-flag: never-activated
uuid: 8b6320c0-1aae-4acd-a698-03f9bebd916d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ee724240-c337-489d-a21b-5f3aec1f247a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Gerenciamento de fluxos de trabalho{#managing-workflows}

Por padrão, seus novos fluxos de trabalho se baseiam em um modelo de fluxo de trabalho que foi pré-configurado e baseado em uma tabela de destinatários (nms:receipt). Para que eles sejam baseados automaticamente na tabela personalizada de destinatários referenciados na opção **Nms_DefaultRcpSchema** (consulte [Configuração da seção da interface](../../configuration/using/configuring-the-interface.md) ), você deve criar um novo modelo de fluxo de trabalho.

Crie um novo modelo pelo **[!UICONTROL Resources > Templates > Workflow templates]** nó. Nas propriedades do modelo, as dimensões fornecidas correspondem à tabela de destinatários externos.

Ao basear seus novos fluxos de trabalho em um modelo criado recentemente, sua tabela personalizada será selecionada por padrão para as dimensões de filtragem e direcionamento global do fluxo de trabalho.

Todas as atividades usadas em seu fluxo de trabalho usarão sua tabela personalizada sem precisar de qualquer configuração manual adicional.

Para obter mais informações sobre fluxos de trabalho, consulte [esta seção](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)

