---
solution: Campaign Classic
product: campaign
title: Backup
description: Backup
audience: production
content-type: reference
topic-tags: data-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '197'
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

>[!IMPORTANT]
>
>É essencial fazer backup do banco de dados.

## Banco de dados {#database}

O banco de dados contém todas as informações exibidas no console Adobe Campaign rich client, bem como todos os dados de linha de negócios.

Sua empresa de hospedagem e seus administradores de banco de dados em particular são responsáveis por essa operação.
