---
solution: Campaign Classic
product: campaign
title: Limpeza de eventos
description: Limpeza de eventos
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 100%

---


# Limpeza de eventos{#purging-events}

Você pode usar o assistente de implantação para definir por quanto tempo os dados devem ser armazenados no banco de dados.

A limpeza de eventos é executada automaticamente pelo fluxo de trabalho **[!UICONTROL Database cleanup]**. Esse workflow limpa os eventos recebidos e armazenados nas instâncias de execução e eventos arquivados em uma instância de controle.

Use as setas conforme o caso para alterar as configurações de limpeza:

Configurações de limpeza de eventos em uma instância de controle:

![](assets/messagecenter_delete_events_001.png)

Configurações de limpeza de eventos em uma instância de execução:

![](assets/messagecenter_delete_events_002.png)

Para obter mais informações sobre o workflow de limpeza de banco de dados, consulte [esta seção](../../production/using/database-cleanup-workflow.md).
