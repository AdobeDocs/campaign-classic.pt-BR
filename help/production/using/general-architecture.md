---
product: campaign
title: Arquitetura geral
description: Arquitetura geral
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: introduction
exl-id: 3bfb5448-6996-4080-bf9a-434f1207637e
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
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
1. Tráfego do protocolo SMTP de e para o servidor Adobe Campaign pela Internet.

## Arquitetura distribuída {#distributed-architecture}

O Adobe Campaign é composto de vários módulos que podem ser divididos em várias máquinas. Esse modo operacional tem várias vantagens:

* balanceamento de carga,
* configuração da redundância do módulo,
* construção de uma arquitetura distribuída por vários fornecedores de serviços (segmentação dos serviços prestados).

![](assets/architecturerepartie.png)

A distribuição de módulos em várias máquinas proporciona uma grande flexibilidade de utilização e uma melhor adaptabilidade.

>[!NOTE]
>
>Para obter mais informações sobre as várias arquiteturas, consulte [esta seção](../../installation/using/general-architecture.md).

## Lista de portas abertas {#list-of-open-ports}

| Número da porta | Módulo ou aplicativo Adobe Campaign relacionado | Configurável |
|---|---|---|
| 443/tcp ou 80/tcp | Servidores da Web (Apache/IIS) | SIM |
| 6666/udp (local) | Adobe Campaign: Syslogd | SIM |
| 8005/tcp (local) | Adobe Campaign: módulo da web | SIM |
| 8080/tcp | Adobe Campaign: módulo da Web (tomcat) | SIM |
| 7777 | Servidor de Estatísticas (stat server) | SIM |
