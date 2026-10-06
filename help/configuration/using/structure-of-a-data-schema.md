---
product: campaign
title: Estrutura de um esquema de dados
description: Estrutura de um esquema de dados
feature: Custom Resources
role: Developer
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
TQID: 'https://experienceleague.adobe.com/bp-x2YrBY5WzNVTXJjpzdZgG45vNPPG9-z339I9U5Lw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: a2002dba-5e37-4dff-8e04-1cc3ec73558c
    internal-label: Custom resources
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 10%
---
# Estrutura de um esquema de dados{#structure-of-a-data-schema}

A estrutura de um schema de dados é mostrada na forma de uma estrutura em árvore. Para exibi-lo graficamente no console do cliente Adobe Campaign, selecione o esquema de destino e clique na subguia **[!UICONTROL Structure]**.

![](assets/d_ncs_integration_schema_arbo.png)

Como padrão, os campos são exibidos primeiro (Ativo, Ativado etc.) e por ordem alfabética. Os elementos estruturantes vêm em seguida (Endereço postal, Localização) e, por fim, os links (Informações de email, Pasta etc.).

As chaves primárias são identificadas por uma chave vermelha e as chaves estrangeiras são identificadas por uma chave amarela.

Os links são diferenciados graficamente, dependendo se pertencem à tabela. Os que começam na tabela, ou seja, que têm a chave externa na tabela, são exibidos primeiro (Informações de email, Pasta, País). Links de coleta &quot;reversa&quot; (Assinatura, Pedidos, etc.) são exibidos no final.
