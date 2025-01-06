---
product: campaign
title: Migração para o Campaign Classic
description: Saiba como migrar de uma versão anterior do Campaign para o Campaign Classic
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-overview
hide: true
hidefromtoc: true
exl-id: 3050238d-6f77-4ffa-9aef-677ab8009388
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 2%

---

# Introdução à migração{#about-migration}



Este documento detalha os pré-requisitos para uma migração, as etapas de migração para o Adobe Campaign Classic v7. As etapas e configurações opcionais dependem da sua configuração.

O processo de migração deve ser realizado com cautela, os seus impactos devem ser previamente considerados e o procedimento deve ser realizado com rigor. Ela só deve ser executada por um usuário especialista. É altamente recomendável entrar em contato com o [Atendimento ao cliente do Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) antes de iniciar qualquer procedimento de migração.

A migração deve ser testada no ambiente de teste/preparo antecipadamente para garantir que seja executada sem problemas e sem erros. A migração do ambiente de produção só deve ser executada depois que o ambiente de teste migrado for totalmente validado.

>[!NOTE]
>
>Os novos recursos e aprimoramentos do Adobe Campaign v7 estão detalhados nas [Notas de versão](../../rn/using/latest-release.md).


## Pré-requisitos

* O processo de migração deve ser executado por usuários especialistas. Você deve ser assistido por pelo menos um especialista em banco de dados, um administrador de sistema e um desenvolvedor de aplicativos da Adobe Campaign.
* Antes de iniciar a migração, verifique se os sistemas e os componentes do sistema que você usa são compatíveis com o v7. [Saiba mais](../../rn/using/compatibility-matrix.md).
* Se você usar o Adobe Campaign Cloud Messaging (implantação mid-sourcing), entre em contato com o Atendimento ao cliente da Adobe antes de iniciar.
* Antes de iniciar um processo de migração, você **deve** fazer backup dos dados.
* O processo de migração pode levar vários dias para ser concluído.
* O Adobe Campaign v7 é uma versão mais segura do que as anteriores: isso afeta as diretrizes de configuração para evitar problemas como corrupção de dados e preservar a integridade dos dados no banco de dados. Como cliente do, você é responsável por testar todas as configurações, incluindo workflows.

Mais pré-requisitos estão disponíveis em [esta página](../../migration/using/before-starting-migration.md).


## Ambiente modernizado {#modernizing-your-environment}

Executar uma migração pode ser uma chance de atualizar seu ambiente (mecanismos de banco de dados, sistemas operacionais). A Adobe Campaign recomenda atualizar seus ambientes de produção para as versões mais recentes.

>[!CAUTION]
>
>Para obter mais informações sobre as versões compatíveis com o Adobe Campaign v7, consulte a [Matriz de Compatibilidade](../../rn/using/compatibility-matrix.md).

## Principais etapas de migração {#key-migration-steps}

O procedimento geral para migrar para o Adobe Campaign v7 está detalhado em [esta página](../../migration/using/before-starting-migration.md).


## Configurações específicas {#specific-configurations}

As alterações provocadas pelo Adobe Campaign v7 também podem significar a necessidade de adaptar determinadas configurações específicas desenvolvidas nas versões anteriores. Portanto, pode ser necessário executar uma auditoria em todas as configurações antes da migração: entre em contato com a Adobe Campaign para obter assistência.

Por exemplo, deve-se prestar atenção especial a configurações específicas para aplicações web, extensões de esquema com dados SQL ou clonagem de esquema pronta para uso. Para obter mais informações, consulte [esta página](../../migration/using/configuring-your-platform.md).

Da mesma forma, para responder à maior segurança no Adobe Campaign, alguns mecanismos internos foram modificados: é necessário adaptar essas configurações de acordo.

