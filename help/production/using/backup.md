---
title: Backup
seo-title: Backup
description: Backup
seo-description: null
page-status-flag: never-activated
uuid: 50134154-a671-4534-b48d-a9e2c42e8f1a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 870ab0f2-1bd7-42e7-8d83-a08a520b6587
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 2%

---


# Backup{#backup}

O backup é essencial para evitar a perda de dados no evento de um problema (físico ou relacionado ao sistema) em uma máquina.

Os dados são armazenados em dois locais separados:

* os arquivos físicos são armazenados nos diretórios do Adobe Campaign,
* outros dados são armazenados no banco de dados.

A maioria dos dados está no banco de dados. Isso representa 99% das informações a serem copiadas em backup.

## Arquivos físicos {#physical-files}

Os arquivos são divididos em várias categorias:

* Arquivos de configuração, localizados em **nl6/conf**

   Isso permite que você reconfigure o Adobe Campaign muito rapidamente.

* Redirecionar arquivos ** nl6/var/`<instancename>`/redir**

   Eles estão nos servidores de rastreamento (geralmente chamados de &quot;frontais&quot;) e incluem todos os redirecionamentos de campanha anteriores. Elas ainda são usadas por campanhas anteriores.

* Arquivos de registro: **nl6/var/`<instancename>`/log**

   Estes podem ser usados para rastrear problemas.

Os diretórios que devem ser submetidos a backup são, por conseguinte:

* nl6/conf

* nl6/var/`<instanceName>`/redir (para cada instância)

* nl6/var/`<instanceName>`/log (opcional)

* nl6/var/`<instanceName>`/relay (opcional)

>[!CAUTION]
>
>É essencial fazer backup do banco de dados.

## Banco de dados {#database}

O banco de dados contém todas as informações exibidas no console Adobe Campaign rich client, bem como todos os dados de linha de negócios.

Sua empresa de hospedagem e seus administradores de banco de dados em particular são responsáveis por essa operação.
