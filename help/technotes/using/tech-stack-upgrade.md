---
product: campaign
title: Nota técnica - Atualizações do sistema Adobe Campaign
description: Atualização do sistema Adobe Campaign
hide: true
hidefromtoc: true
source-git-commit: 6fc11ea75863abe86e81c4978843e8487cbd83a0
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 8%

---

# Atualização do sistema Adobe Campaign 2023 {#ac-system-upgrade}

A infraestrutura do Campaign depende de sistemas de terceiros, que devem ser atualizados regularmente com as versões e correções mais recentes. Essas atualizações são obrigatórias para garantir a continuidade do serviço e proteger os ambientes do Campaign contra riscos de segurança. Além disso, uma atualização do Campaign é necessária para garantir a compatibilidade com alterações de sistema de terceiros.

Como um **Cliente Cloud Services hospedado ou gerenciado**, o Adobe informa você sobre essas atualizações quando elas são necessárias. Você precisará atualizar seus ambientes de acordo com as recomendações para garantir a conformidade.

Como um **Cliente local ou híbrido**, o Adobe recomenda que você atualize as versões do sistema e do Campaign de acordo com o mesmo calendário.

Por motivos de segurança, é necessário [instale a build mais recente do Campaign](#ac-upgrade)e, em seguida, atualize seu [sistema operacional](#os-upgrade) e/ou seu [Sistema de Gestão de Bases de Dados de Relação (RDBMS)](#pg-upgrade).

>[!NOTE]
>
>Em caso de dúvidas sobre essas alterações, entre em contato com o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Consulte também a [Perguntas frequentes sobre atualização de build](../../platform/using/faq-build-upgrade.md).

## Atualização de build da campanha {#ac-upgrade}

**Você será afetado?**

Se você for afetado pela variável [atualização do sistema operacional](#os-upgrade) e/ou a [atualização do sistema de banco de dados](#pg-upgrade) detalhado abaixo, você deve atualizar seus ambientes do Campaign para a versão 7.3.2 mais recente, que é compatível com esses sistemas.

**Como atualizar?**

* Como cliente hospedado ou gerenciado do Cloud Services, o Adobe entrará em contato com você e atualizará sua versão do Campaign.
* Como cliente híbrido, o Adobe informará você sobre as datas programadas de atualização de build para seu ambiente de mid-sourcing. Você também deve atualizar seu ambiente de marketing para essa mesma versão.
* Como cliente local, você deve atualizar seus ambientes do Campaign para a build 7.3.2 mais recente.


## Atualização do sistema operacional {#os-upgrade}

**Você será afetado?**

Se você estiver executando o Campaign em um sistema operacional Debian, para se beneficiar das atualizações de segurança mais recentes do Debian, será necessário mover sua infraestrutura do Campaign para o **Debian 11**. Observe que Debian 9 chegou ao fim da vida útil em 30 de junho de 2022 e não fornece mais correções de segurança.

**Como atualizar?**

* Como cliente hospedado ou gerenciado do Cloud Services, o Adobe entrará em contato com você e atualizará seu ambiente.
* Como cliente híbrido, o Adobe informará você sobre as datas de atualização programadas para seu ambiente de mid-sourcing. Se seu ambiente de marketing também estiver em execução no Debian, você também deverá atualizá-lo para o Debian 11.
* Como cliente local, você deve atualizar seus ambientes para o Debian 11.

## Atualização do sistema de banco de dados {#pg-upgrade}

**Você será afetado?**

Se o sistema de banco de dados para o Campaign for PostgreSQL, para se beneficiar das mais recentes inovações e atualizações de segurança do PostgreSQL, será necessário atualizar para **PostgreSQL 14**. Observe que o PostreSQL 11 chegará ao fim da vida útil em 30 de novembro de 2022.

**Como atualizar?**

* Como cliente hospedado ou gerenciado do Cloud Services, o Adobe entrará em contato com você e atualizará seu sistema de banco de dados do PostgreSQL 11 para o PostgreSQL 14.
* Como cliente híbrido, se o sistema de banco de dados de marketing for PostgreSQL, você deverá atualizá-lo para PostgreSQL 14.
* Como cliente local, você deve atualizar seu sistema de banco de dados para PostgreSQL 14.


## Links úteis

* [Atualizar seu ambiente](../../production/using/build-upgrade.md)
* [Perguntas frequentes sobre atualização de build](../../platform/using/faq-build-upgrade.md)
* [Baixe a build mais recente do Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html)
* [Disponibilizar o novo Console do cliente para os usuários](../../installation/using/client-console-availability-for-windows.md)
