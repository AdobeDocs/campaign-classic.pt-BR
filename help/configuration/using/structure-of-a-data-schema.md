---
product: campaign
title: Estrutura de um esquema de dados
description: Estrutura de um esquema de dados
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 10%

---

# Estrutura de um esquema de dados{#structure-of-a-data-schema}

![](../../assets/v7-only.svg)

A estrutura de um schema de dados é mostrada no formato de uma estrutura em árvore. Para exibi-lo graficamente no console do cliente Adobe Campaign, selecione o schema direcionado e clique no botão **[!UICONTROL Structure]** subguia .

![](assets/d_ncs_integration_schema_arbo.png)

Como padrão, os campos são exibidos primeiro (Ativo, Ativado, etc.) e em ordem alfabética. Os elementos de estruturação vêm em seguida (Endereço postal, Local) e finalmente os links (Informações de email, Pasta etc.).

As chaves primárias são identificadas por uma tecla vermelha e as chaves estrangeiras são identificadas por uma chave amarela.

Os links são distintos graficamente, dependendo se pertencem à tabela. As que começam na tabela, ou seja, que têm a chave estrangeira na tabela, são exibidas primeiro (Informações de email, Pasta, País). Links de coleção &quot;inversa&quot; (assinatura, pedidos etc.) são exibidos no final.
