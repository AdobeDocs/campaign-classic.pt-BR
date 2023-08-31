---
product: campaign
title: Estrutura de um esquema de dados
description: Estrutura de um esquema de dados
feature: Custom Resources
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 14%

---

# Estrutura de um esquema de dados{#structure-of-a-data-schema}

A estrutura de um schema de dados é mostrada na forma de uma estrutura em árvore. Para visualizá-lo graficamente no console do cliente Adobe Campaign, selecione o esquema direcionado e clique no link **[!UICONTROL Structure]** subguia.

![](assets/d_ncs_integration_schema_arbo.png)

Como padrão, os campos são exibidos primeiro (Ativo, Ativado etc.) e por ordem alfabética. Os elementos estruturantes vêm em seguida (Endereço postal, Localização) e, por fim, os links (Informações de email, Pasta etc.).

As chaves primárias são identificadas por uma chave vermelha e as chaves estrangeiras são identificadas por uma chave amarela.

Os links são diferenciados graficamente, dependendo se pertencem à tabela. Os que começam na tabela, ou seja, que têm a chave externa na tabela, são exibidos primeiro (Informações de email, Pasta, País). Links de coleta &quot;reversa&quot; (Assinatura, Pedidos, etc.) são exibidos no final.
