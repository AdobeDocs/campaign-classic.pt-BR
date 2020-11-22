---
solution: Campaign Classic
product: campaign
title: Arquitetura geral
description: Arquitetura geral
audience: production
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 6%

---


# Arquitetura geral{#general-architecture}

## Arquitetura mínima {#minimum-architecture}

Em uma configuração mínima, a Adobe Campaign opera com:

* o servidor de aplicativos Adobe Campaign,
* o banco de dados.

   ![](assets/formation_exploitation.png)

Este diagrama mostra que o único tráfego envolvido no contexto de uma arquitetura mínima é:

1. tráfego de protocolo HTTP para o servidor Adobe Campaign através da Internet,
1. Tráfego de protocolo SMTP de e para o servidor Adobe Campaign via Internet.

## Arquitetura distribuída {#distributed-architecture}

A Adobe Campaign é composta de vários módulos que podem ser divididos em várias máquinas. Este modo operacional tem várias vantagens:

* balanceamento de carga,
* criação de redundância de módulo,
* construção de uma arquitetura repartida por vários provedores de serviço (segmentação dos serviços prestados).

![](assets/architecturerepartie.png)

A distribuição de módulos em várias máquinas proporciona grande flexibilidade de uso e maior adaptabilidade.

>[!NOTE]
>
>For more on the various architectures, refer to [this section](../../installation/using/general-architecture.md).

## Lista de portas abertas {#list-of-open-ports}

| Número da porta | Módulo ou aplicativo Adobe Campaign em questão | Configurável |
|---|---|---|
| 443/tcp ou 80/tcp | Servidores Web (Apache/IIS) | SIM |
| 6666/udp (local) | Adobe Campaign: Syslogd | SIM |
| 8005/tcp (local) | Adobe Campaign: módulo web | SIM |
| 8080/tcp | Adobe Campaign: módulo da Web (tomcat) | SIM |
| 7777 | Servidor de estatísticas (servidor estadual) | SIM |

