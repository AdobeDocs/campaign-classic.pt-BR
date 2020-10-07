---
title: Estrutura de um schema de dados
seo-title: Estrutura de um schema de dados
description: Estrutura de um schema de dados
seo-description: null
page-status-flag: never-activated
uuid: 83e3995d-fa31-4cb5-acf2-83f17329c99c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: a1a39eaa-6d6f-42c5-a36b-bd1cb3a77dcb
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 13%

---


# Estrutura de um schema de dados{#structure-of-a-data-schema}

A estrutura de um schema de dados é mostrada na forma de uma estrutura em árvore. Para visualização gráfica no console do cliente Adobe Campaign, selecione o schema direcionado e clique na **[!UICONTROL Structure]** subguia.

![](assets/d_ncs_integration_schema_arbo.png)

Como padrão, os campos são exibidos primeiro (Ativo, Ativado etc.) e por ordem alfabética. Os elementos estruturantes vêm em seguida (Endereço postal, Localização) e, finalmente, os links (Informações de email, Pasta etc.).

As teclas primárias são identificadas por uma tecla vermelha e as teclas estrangeiras são identificadas por uma chave amarela.

Os links são distintos graficamente, dependendo se pertencem à tabela. Os start que aparecem na tabela, ou seja, que têm a chave estrangeira na tabela, são exibidos primeiro (Informações de email, Pasta, País). Links de coleção &quot;Inverter&quot; (Subscrição, Pedidos etc.) são exibidos no final.
