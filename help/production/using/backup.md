---
product: campaign
title: Backup
description: Backup
feature: Monitoring
badge-v7-prem: label="Somente no local/híbrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
TQID: https://experienceleague.adobe.com/ZCExecNbs9DnWVoQLpvzlrH7k2eGhBNq7pEiybyQdi4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616a
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 232
ht-degree: 14%

---

# Backup{#backup}

O backup é essencial para evitar a perda de dados no caso de um problema (seja físico ou relacionado ao sistema) em uma máquina.

Os dados são armazenados em dois locais separados:

* os arquivos físicos são armazenados nos diretórios do Adobe Campaign,
* outros dados são armazenados no banco de dados.

A maioria dos dados está no banco de dados. Isso representa 99% das informações cujo backup será feito.

## Arquivos físicos {#physical-files}

Os arquivos são divididos em várias categorias:

* Os arquivos de configuração, armazenados em **nl6/conf**, permitem que você reconfigure o Adobe Campaign muito rapidamente.

* Os arquivos de redirecionamento, armazenados em **nl6/var/`<instance-name>`/redir**, estão nos servidores de rastreamento (geralmente chamados de &quot;frontais&quot;) e incluem todos os redirecionamentos de campanha anteriores. Eles ainda são usados por campanhas anteriores.

* Arquivos de log, armazenados em **nl6/var/`<instance-name>`/log**, podem ser usados para rastrear problemas.

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
