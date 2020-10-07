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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 12%

---


# Gerenciamento de fluxos de trabalho{#managing-workflows}

Por padrão, seus novos workflows se baseiam em um modelo de fluxo de trabalho que foi pré-configurado e baseado em uma tabela de recipient (nms:recipient). Para que eles sejam baseados automaticamente na tabela personalizada de recipient referenciados na opção **Nms_DefaultRcpSchema** (consulte [Configuração da seção da interface](../../configuration/using/configuring-the-interface.md) ), você deve criar um novo modelo de fluxo de trabalho.

Create a new template via the **[!UICONTROL Resources > Templates > Workflow templates]** node. Nas propriedades do modelo, as dimensões fornecidas correspondem à tabela de recipient externos.

Ao basear seus novos workflows em um modelo criado recentemente, sua tabela personalizada será selecionada por padrão para o direcionamento global e dimensões do filtro do fluxo de trabalho.

Todas as atividades usadas em seu fluxo de trabalho usarão sua tabela personalizada sem precisar de qualquer configuração manual adicional.

Para obter mais informações sobre fluxos de trabalho, consulte [esta seção](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)

