---
title: Arquitetura geral
seo-title: Arquitetura geral
description: Arquitetura geral
seo-description: null
page-status-flag: never-activated
uuid: a565a10c-cbef-455a-aa1d-9be9cd207c7a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: introduction
discoiquuid: f4879774-afe5-4556-ab60-9297cabbca2c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Arquitetura geral{#general-architecture}

## Arquitetura mínima {#minimum-architecture}

Em uma configuração mínima, o Adobe Campaign opera com:

* o servidor de aplicativos do Adobe Campaign,
* o banco de dados.

   ![](assets/formation_exploitation.png)

Este diagrama mostra que o único tráfego envolvido no contexto de uma arquitetura mínima é:

1. tráfego de protocolo HTTP para o servidor do Adobe Campaign pela Internet,
1. Tráfego de protocolo SMTP de e para o servidor do Adobe Campaign pela Internet.

## Arquitetura distribuída {#distributed-architecture}

O Adobe Campaign é composto por vários módulos que podem ser divididos em várias máquinas. Este modo operacional tem várias vantagens:

* balanceamento de carga,
* criação de redundância de módulo,
* construção de uma arquitetura repartida por vários prestadores de serviços (segmentação dos serviços prestados).

![](assets/architecturerepartie.png)

A distribuição de módulos em várias máquinas proporciona grande flexibilidade de uso e maior adaptabilidade.

>[!NOTE]
>
>For more on the various architectures, refer to [this section](../../installation/using/general-architecture.md).

## Lista de portas abertas {#list-of-open-ports}

| Número da porta | Aplicativo ou módulo do Adobe Campaign em questão | Configurável |
|---|---|---|
| 443/tcp ou 80/tcp | Servidores Web (Apache/IIS) | SIM |
| 6666/udp (local) | Adobe Campaign: Syslogd | SIM |
| 8005/tcp (local) | Adobe Campaign: módulo web | SIM |
| 8080/tcp | Adobe Campaign: módulo da Web (tomcat) | SIM |
| 7777 | Servidor de estatísticas (servidor estático) | SIM |

