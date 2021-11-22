---
product: campaign
title: Backup
description: Backup
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 2%

---

# Backup{#backup}

![](../../assets/v7-only.svg)

O backup é essencial para evitar a perda de dados em caso de problema (físico ou relacionado ao sistema) em uma máquina.

Os dados são armazenados em dois locais separados:

* os arquivos físicos são armazenados nos diretórios do Adobe Campaign,
* outros dados são armazenados no banco de dados.

A maioria dos dados está no banco de dados. Isso representa 99% das informações do backup.

## Arquivos físicos {#physical-files}

Os arquivos são divididos em várias categorias:

* Arquivos de configuração, localizados em **nl6/conf**

   Isso permite reconfigurar o Adobe Campaign muito rapidamente.

* Arquivos de redirecionamento ** nl6/var/`<instancename>`/redirer**

   Eles estão nos servidores de rastreamento (geralmente chamados de &quot;frontais&quot;) e incluem todos os redirecionamentos de campanha anteriores. Elas ainda são usadas por campanhas anteriores.

* Arquivos de log: **nl6/var/`<instancename>`/log**

   Eles podem ser usados para rastrear problemas.

Os diretórios a serem submetidos a backup são, portanto:

* nl6/conf

* nl6/var/`<instanceName>`/redir (para cada instância)

* nl6/var/`<instanceName>`/log (opcional)

* nl6/var/`<instanceName>`/relay (opcional)

>[!IMPORTANT]
>
>É essencial fazer backup do banco de dados.

## Banco de dados {#database}

O banco de dados contém todas as informações exibidas no console do cliente avançado do Adobe Campaign, bem como todos os dados de linha de negócios.

Sua empresa de hospedagem e seus administradores de banco de dados em particular são responsáveis por essa operação.
