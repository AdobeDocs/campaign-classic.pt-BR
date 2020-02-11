---
title: Estrutura de um esquema de dados
seo-title: Estrutura de um esquema de dados
description: Estrutura de um esquema de dados
seo-description: null
page-status-flag: never-activated
uuid: 83e3995d-fa31-4cb5-acf2-83f17329c99c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: a1a39eaa-6d6f-42c5-a36b-bd1cb3a77dcb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Estrutura de um esquema de dados{#structure-of-a-data-schema}

A estrutura de um esquema de dados é mostrada na forma de uma estrutura em árvore. Para exibi-lo graficamente no console do cliente do Adobe Campaign, selecione o esquema direcionado e clique na **[!UICONTROL Structure]** subguia.

![](assets/d_ncs_integration_schema_arbo.png)

Como padrão, os campos são exibidos primeiro (Ativo, Ativado etc.) e por ordem alfabética. Os elementos estruturantes vêm em seguida (Endereço postal, Localização) e, finalmente, os links (Informações de email, Pasta etc.).

As teclas primárias são identificadas por uma tecla vermelha e as teclas estrangeiras são identificadas por uma chave amarela.

Os links são distintos graficamente, dependendo se pertencem à tabela. As que começam com a tabela, ou seja, que têm a chave estrangeira na tabela, são exibidas primeiro (Informações de email, Pasta, País). Links de coleção &quot;Inverter&quot; (Assinatura, Pedidos etc.) são exibidos no final.
