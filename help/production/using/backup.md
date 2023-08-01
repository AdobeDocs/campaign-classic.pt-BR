---
product: campaign
title: Backup
description: Backup
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Aplicável somente ao Campaign Classic v7"
badge-v7-prem: label="no local e híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 9%

---

# Backup{#backup}

O backup é essencial para evitar a perda de dados no caso de um problema (seja físico ou relacionado ao sistema) em uma máquina.

Os dados são armazenados em dois locais separados:

* os arquivos físicos são armazenados nos diretórios do Adobe Campaign,
* outros dados são armazenados no banco de dados.

A maioria dos dados está no banco de dados. Isso representa 99% das informações cujo backup será feito.

## Arquivos físicos {#physical-files}

Os arquivos são divididos em várias categorias:

* Arquivos de configuração, armazenados em **nl6/conf**, permitem reconfigurar o Adobe Campaign muito rapidamente.

* Arquivos de redirecionamento, armazenados em  **nl6/var/`<instance-name>`/redir**, estão nos servidores de rastreamento (geralmente chamados de &quot;frontais&quot;) e incluem todos os redirecionamentos de campanha anteriores. Eles ainda são usados por campanhas anteriores.

* Arquivos de log, armazenados em **nl6/var/`<instance-name>`/log**, pode ser usado para rastrear problemas.

Portanto, os diretórios dos quais será feito backup são:

* nl6/conf

* nl6/var/`<instance-name>`/redir (para cada instância)

* nl6/var/`<instance-name>`/log (opcional)

* nl6/var/`<instance-name>`/relay (opcional)


## Banco de dados {#database}

>[!IMPORTANT]
>
>É fundamental fazer backup do banco de dados.


O banco de dados contém todas as informações exibidas no console do cliente avançado Adobe Campaign, bem como todos os dados da linha de negócios.

Sua empresa de hospedagem e seus administradores de banco de dados em particular são responsáveis por essa operação.
