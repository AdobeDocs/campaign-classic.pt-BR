---
solution: Campaign Classic
product: campaign
title: Método de migração
description: Método de migração
audience: migration
content-type: reference
topic-tags: migration-overview
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 1%

---


# Método de migração{#migration-method}

## Modernizar seu ambiente {#modernizing-your-environment}

Executar uma migração pode ser uma oportunidade de atualizar seu ambiente (mecanismos de banco de dados, sistemas operacionais). A Adobe Campaign recomenda que você atualize seus ambientes de produção para as versões mais recentes.

Os bancos de dados de versão de 32 bits e os sistemas operacionais ainda são suportados na versão v7, mas não serão mais suportados em versões futuras do Adobe Campaign. Recomendamos que você atualize sua plataforma para 64 bits o mais rápido possível.

Na v6.02, o modo &quot;multifuso horário&quot; estava disponível somente para mecanismos de banco de dados PostgreSQL. Agora, ele é oferecido independentemente do tipo de mecanismo de banco de dados usado. Recomendamos que você transforme sua base em uma base de &quot;vários fusos horários&quot;. Para obter mais informações sobre isso, consulte a seção [Fusos horários](../../migration/using/general-configurations.md#time-zones) .

>[!IMPORTANT]
>
>Algumas versões de software suportadas pelo Adobe Campaign 5.11 e 6.02 não são mais suportadas pelo Adobe Campaign v7.
>
>Para obter mais informações sobre as versões suportadas pela Adobe Campaign, consulte a matriz de [compatibilidade](../../rn/using/compatibility-matrix.md).

## Principais etapas de migração {#key-migration-steps}

O procedimento geral para migrar para o Adobe Campaign v7 é detalhado na seção [Antes de iniciar a migração](../../migration/using/before-starting-migration.md) .

As etapas de implementação para a migração para o Adobe Campaign v7 estão detalhadas na seção [Pré-requisitos para migração para o Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .

As configurações necessárias dependem das configurações existentes e da versão inicial da plataforma. Eles são descritos na seção Configurações [](../../migration/using/general-configurations.md) gerais.

## Configurações específicas {#specific-configurations}

As mudanças geradas pelo Adobe Campaign v7 também podem significar que é necessário adaptar determinadas configurações específicas desenvolvidas nas versões anteriores. Portanto, pode ser necessário realizar uma auditoria em todas as configurações antes da migração: entre em contato com a Adobe Campaign para obter assistência.

Por exemplo, deve ser prestada atenção especial a configurações específicas para Aplicação web, extensões de schema com dados SQL ou clonagem predefinida de schemas. Para obter mais informações, consulte a seção [Configuração da plataforma](../../migration/using/configuring-your-platform.md) .

Da mesma forma, para responder ao aumento da segurança dentro da Adobe Campaign, alguns mecanismos internos foram modificados: você deve adaptar essas configurações correspondentes.
