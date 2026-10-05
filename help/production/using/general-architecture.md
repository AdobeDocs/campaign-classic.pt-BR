---
product: campaign
title: Arquitetura geral
description: Arquitetura geral
feature: Monitoring, Architecture
audience: production
content-type: reference
topic-tags: introduction
exl-id: 3bfb5448-6996-4080-bf9a-434f1207637e
TQID: 'https://experienceleague.adobe.com/n-ppeL-j1SdCPTXFo8Mw4GEWcSD4L7LnDxg9K9klU3U'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: bae31391-3416-5fbd-bc4b-2cdcae2922db
    internal-label: Architecture
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 4%
---
# Arquitetura geral{#general-architecture}



## Arquitetura mínima {#minimum-architecture}

Em uma configuração mínima, o Adobe Campaign opera com:

* o servidor de aplicativos do Adobe Campaign,
* banco de dados.

  ![](assets/formation_exploitation.png)

Este diagrama mostra que o único tráfego envolvido no contexto de uma arquitetura mínima é:

1. Tráfego de protocolo HTTP para o servidor do Adobe Campaign pela Internet,
1. Tráfego do protocolo SMTP de e para o servidor do Adobe Campaign pela Internet.

## Arquitetura distribuída {#distributed-architecture}

O Adobe Campaign é composto de vários módulos que podem ser divididos em várias máquinas. Esse modo operacional tem várias vantagens:

* balanceamento de carga
* configuração de redundância de módulo,
* construção de uma arquitetura dividida em vários provedores de serviços (segmentação dos serviços fornecidos).

![](assets/architecturerepartie.png)

A distribuição de módulos por várias máquinas proporciona grande flexibilidade de uso e melhor adaptabilidade.

>[!NOTE]
>
>Para obter mais informações sobre as várias arquiteturas, consulte [esta seção](../../installation/using/general-architecture.md).

## Lista de portas abertas {#list-of-open-ports}

| Número da porta | Módulo ou aplicativo Adobe Campaign relacionado | Configurável |
|---|---|---|
| 443/tcp ou 80/tcp | Servidores da Web (Apache/IIS) | SIM |
| 6666/udp (local) | Adobe Campaign: Syslogd | SIM |
| 8005/tcp (local) | Adobe Campaign: módulo Web | SIM |
| 8080/tcp | Adobe Campaign: módulo web (tomcat) | SIM |
| 7777 | Servidor de estatísticas (servidor stat) | SIM |
