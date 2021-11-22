---
product: campaign
title: Método de migração
description: Método de migração
audience: migration
content-type: reference
topic-tags: migration-overview
exl-id: dd4d068b-f414-448f-8d9a-eedf44e7b6e6
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 1%

---

# Método de migração{#migration-method}

![](../../assets/v7-only.svg)

## Modernização de seu ambiente {#modernizing-your-environment}

A execução de uma migração pode ser uma oportunidade de atualizar seu ambiente (mecanismos de banco de dados, sistemas operacionais). A Adobe Campaign recomenda que você atualize seus ambientes de produção para as versões mais recentes.

Os bancos de dados e sistemas operacionais da versão de 32 bits ainda são compatíveis com o v7, mas não serão mais compatíveis com versões futuras do Adobe Campaign. Recomendamos que você atualize sua plataforma para 64 bits o mais rápido possível.

Na v6.02, o modo &quot;vários fusos horários&quot; só estava disponível para mecanismos de banco de dados PostgreSQL. Agora, ele é oferecido independentemente do tipo de mecanismo de banco de dados usado. É altamente recomendável transformar sua base em uma base de &quot;vários fusos horários&quot;. Para obter mais informações sobre isso, consulte o [Fusos horários](../../migration/using/general-configurations.md#time-zones) seção.

>[!IMPORTANT]
>
>Algumas versões de software compatíveis com o Adobe Campaign 5.11 e 6.02 não são mais compatíveis com o Adobe Campaign v7.
>
>Para obter mais informações sobre as versões compatíveis com o Adobe Campaign, consulte o [matriz de compatibilidade](../../rn/using/compatibility-matrix.md).

## Etapas principais de migração {#key-migration-steps}

O procedimento geral para migração para o Adobe Campaign v7 está detalhado na seção [Antes de iniciar a migração](../../migration/using/before-starting-migration.md) seção.

As etapas de implementação da migração para o Adobe Campaign v7 estão detalhadas no [Pré-requisitos da migração para o Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) seção.

As configurações necessárias dependem das configurações existentes e da versão inicial da plataforma. Elas são descritas na seção [Configurações gerais](../../migration/using/general-configurations.md) seção.

## Configurações específicas {#specific-configurations}

As alterações acionadas pelo Adobe Campaign v7 também podem significar que você precisa adaptar determinadas configurações específicas desenvolvidas nas versões anteriores. Portanto, pode ser necessário executar uma auditoria em todas as suas configurações antes da migração: entre em contato com a Adobe Campaign para obter assistência.

Por exemplo, deve-se prestar especial atenção às configurações específicas para aplicações Web, extensões de schema com dados SQL ou clonagem de schema pronta para uso. Para obter mais informações, consulte [Configuração da plataforma](../../migration/using/configuring-your-platform.md) seção.

Da mesma forma, para responder ao aumento da segurança no Adobe Campaign, alguns mecanismos internos foram modificados: você deve adaptar essas configurações correspondentes.
