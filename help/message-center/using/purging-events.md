---
title: Limpeza de eventos
seo-title: Limpeza de eventos
description: Limpeza de eventos
seo-description: null
page-status-flag: never-activated
uuid: bbce6813-dfa8-418c-9b52-06e814c15265
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 2f643080-93b4-4c9f-80cf-b1770b149e6c
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '90'
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
