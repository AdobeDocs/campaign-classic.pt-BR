---
product: campaign
title: Migração para o Campaign Classic
description: Saiba como migrar para o Campaign Classic de uma versão anterior do Campaign
audience: migration
content-type: reference
topic-tags: migration-overview
exl-id: 3050238d-6f77-4ffa-9aef-677ab8009388
source-git-commit: 2594e4943ba24ae65d1fc005da589dc674aa2b0f
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 3%

---

# Introdução à migração{#about-migration}

![](../../assets/v7-only.svg)

Este documento detalha os pré-requisitos para uma migração, as etapas para uma migração para o Adobe Campaign Classic v7. As etapas e as configurações opcionais dependem da sua configuração.

O processo de migração deve ser realizado com cautela, os seus impactos devem ser plenamente considerados previamente e o procedimento deve ser executado com rigor. Ele só deve ser executado por um usuário especialista. É altamente recomendável entrar em contato com o [Atendimento ao cliente do Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) antes de iniciar qualquer procedimento de migração.

A migração deve ser testada previamente no ambiente de teste/estágio para garantir que seja executada sem problemas e sem erros. A migração do ambiente de produção só deve ser realizada depois que o ambiente de teste migrado for totalmente validado.

>[!NOTE]
>
>Os novos recursos e aprimoramentos que vêm com o Adobe Campaign v7 estão detalhados na seção [Notas de versão](../../rn/using/latest-release.md).


## Pré-requisitos

* O processo de migração deve ser executado por usuários especialistas. Você deve ser assistido por pelo menos um especialista em banco de dados, um administrador de sistema e um desenvolvedor de aplicativos da Adobe Campaign.
* Antes de iniciar a migração, verifique se os sistemas e componentes do sistema usados são compatíveis com o v7. [Saiba mais](../../rn/using/compatibility-matrix.md).
* Se você usar o Adobe Campaign Cloud Messaging (implantação de mid-sourcing), entre em contato com o Atendimento ao cliente do Adobe antes de iniciar.
* Antes de iniciar um processo de migração, você **must** faça backup dos seus dados.
* O processo de migração pode levar vários dias para ser concluído.
* O Adobe Campaign v7 é uma versão mais segura do que as anteriores: isso afeta as diretrizes de configuração para evitar problemas como corrupção de dados e preservar a integridade dos dados no banco de dados. Como cliente, você é responsável por testar todas as configurações, incluindo workflows.

Mais pré-requisitos estão disponíveis em [esta página](../../migration/using/before-starting-migration.md).


## Ambiente modernizado {#modernizing-your-environment}

A execução de uma migração pode ser uma oportunidade de atualizar seu ambiente (mecanismos de banco de dados, sistemas operacionais). A Adobe Campaign recomenda que você atualize seus ambientes de produção para as versões mais recentes.

>[!CAUTION]
>
>Para obter mais informações sobre as versões compatíveis com o Adobe Campaign v7, consulte [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md).

## Etapas principais de migração {#key-migration-steps}

O procedimento geral para migração para o Adobe Campaign v7 está detalhado em [esta página](../../migration/using/before-starting-migration.md).


## Configurações específicas {#specific-configurations}

As alterações acionadas pelo Adobe Campaign v7 também podem significar que você precisa adaptar determinadas configurações específicas desenvolvidas nas versões anteriores. Portanto, pode ser necessário executar uma auditoria em todas as suas configurações antes da migração: entre em contato com a Adobe Campaign para obter assistência.

Por exemplo, deve-se prestar especial atenção às configurações específicas para aplicações Web, extensões de schema com dados SQL ou clonagem de schema pronta para uso. Para obter mais informações, consulte [esta página](../../migration/using/configuring-your-platform.md).

Da mesma forma, para responder ao aumento da segurança no Adobe Campaign, alguns mecanismos internos foram modificados: é necessário adaptar essas configurações adequadamente.

