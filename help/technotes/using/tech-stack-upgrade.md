---
product: campaign
title: Nota técnica - Atualizações de sistema da Adobe Campaign
description: Atualização do sistema Adobe Campaign
feature: Technote, Upgrade
exl-id: 78949d94-60b3-44f1-8e5a-d61b5b723e87
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 4%

---

# Atualizações de ambiente do Adobe Campaign 2023 {#ac-system-upgrade}

A infraestrutura do Campaign depende de sistemas de terceiros que devem ser atualizados regularmente com as versões e correções mais recentes. Essas atualizações são obrigatórias para garantir a continuidade do serviço e proteger os ambientes do Campaign contra riscos de segurança. Além disso, uma atualização do Campaign é necessária para garantir a compatibilidade com alterações no sistema de terceiros.

Como um **cliente de Cloud Service hospedado ou gerenciado**, o Adobe informa sobre essas atualizações quando elas são necessárias. Você deverá atualizar seus ambientes de acordo com as recomendações para garantir a conformidade.

Como um **cliente no local ou híbrido**, a Adobe recomenda que você atualize as versões do sistema e do Campaign de acordo com o mesmo calendário.

Por motivos de segurança, você deve [instalar a compilação mais recente do Campaign](#ac-upgrade) e atualizar seu [sistema operacional](#os-upgrade) e/ou seu [Sistema de Gerenciamento de Banco de Dados Relativo (RDBMS)](#pg-upgrade).

>[!NOTE]
>
>Em caso de dúvidas sobre essas alterações, entre em contato com o [Adobe Customer Care](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Consulte também as [Perguntas frequentes sobre atualização de build](../../platform/using/faq-build-upgrade.md).
>

## Atualização de build do Campaign {#ac-upgrade}

**Você será afetado?**

Se você for afetado pela [atualização do sistema operacional](#os-upgrade) e/ou pela [atualização do sistema de banco de dados](#pg-upgrade) detalhada abaixo, será necessário atualizar seus ambientes do Campaign para a [versão mais recente da 7.3.2](../../rn/using/latest-release.md#release-7-3-2), que é compatível com esses sistemas.

**Como atualizar?**

* Como cliente de Cloud Service hospedado ou gerenciado, o Adobe entrará em contato com você e atualizará a versão do Campaign.
* Como cliente híbrido, o Adobe informará sobre as datas de atualização de build agendadas para seu ambiente de mid-sourcing. Você também deve atualizar seu ambiente de marketing para a mesma versão.
* Como cliente local, você deve atualizar seus ambientes do Campaign para a build 7.3.2 mais recente.


## Atualização do sistema operacional {#os-upgrade}

**Você será afetado?**

Se você estiver executando o Campaign em um sistema operacional Debian, para se beneficiar das atualizações de segurança mais recentes do Debian, será necessário mover sua infraestrutura do Campaign para **Debian 11**. Observe que o suporte de segurança para Debian 9 estará disponível até 30 de junho de 2023.

**Como atualizar?**

* Como cliente de Cloud Service hospedado ou gerenciado, o Adobe entrará em contato e atualizará seu ambiente.
* Como cliente híbrido, o Adobe informará sobre as datas de atualização programadas para o seu ambiente de mid-sourcing. Se seu ambiente de marketing também estiver sendo executado no Debian, você deverá atualizá-lo para o Debian 11 também.
* Como cliente local, você deve atualizar seus ambientes para o Debian 11.

## Atualização do sistema de banco de dados {#pg-upgrade}

**Você será afetado?**

Se o sistema de banco de dados do Campaign for PostgreSQL, para se beneficiar das inovações e atualizações de segurança mais recentes do PostgreSQL, é necessário atualizar para o **PostgreSQL 14**. Observe que o PostgreSQL 11 chegará ao fim da vida útil em 9 de novembro de 2023.

**Como atualizar?**

* Como cliente hospedado ou gerenciado do Cloud Service, o Adobe entrará em contato e atualizará seu sistema de banco de dados do PostgreSQL 11 para o PostgreSQL 14.
* Como cliente híbrido, se o sistema do banco de dados de marketing for PostgreSQL, você deverá atualizá-lo para o PostgreSQL 14.
* Como cliente local, você deve atualizar seu sistema de banco de dados para o PostgreSQL 14.


## Links úteis

* [Atualizar o ambiente](../../production/using/build-upgrade.md)
* [Perguntas frequentes sobre atualização de build](../../platform/using/faq-build-upgrade.md)
* [Baixar a compilação de Campaign Classic mais recente](https://experience.adobe.com/#/downloads/content/software-distribution/br/campaign.html)
* [Disponibilizar o novo Console do cliente para os usuários](../../installation/using/client-console-availability-for-windows.md)
