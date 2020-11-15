---
title: Avisos de migração
description: Avisos de migração
page-status-flag: never-activated
uuid: 35361471-881c-4aaf-a57b-ed7e89a97eae
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-overview
discoiquuid: 1fa1fe0f-c392-413a-9fa0-d1b4e10e2e5e
translation-type: tm+mt
source-git-commit: 99d766cb6234347ea2975f3c08a6ac0496619b41
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 3%

---


# Avisos de migração{#migration-warnings}

* O processo de migração é reservado para usuários especialistas. Você deve ser assistido por pelo menos um especialista em banco de dados, um administrador de sistema e um desenvolvedor de aplicativos da Adobe Campaign.
* Antes de iniciar a migração, verifique se os sistemas e componentes do sistema usados são compatíveis com a v7. Consulte a matriz de [compatibilidade](../../rn/using/compatibility-matrix.md).
* Se você usar o Adobe Campaign Cloud Messaging (anteriormente mid-sourcing), entre em contato com a Adobe Campaign antes de iniciar todo o procedimento de migração.
* Antes de iniciar um processo de migração, você **deve** fazer backup dos dados.
* O processo de migração pode levar vários dias para ser concluído.
* O Adobe Campaign v7 é mais estrito do que as versões 5.11 e 6.02 em termos de configuração. Isso serve principalmente para evitar problemas como corrupção de dados e preservar a integridade dos dados no banco de dados. Consequentemente, certas funções oferecidas na v5.11 e na v6.02 podem não funcionar mais na v7 e podem, portanto, precisar ser adaptadas após a migração. Antes de colocar em produção qualquer coisa, sugerimos que você teste sistematicamente todas as configurações, especialmente os workflows necessários para usar o Adobe Campaign.

>[!NOTE]
>
>Consulte também a seção [Antes de iniciar a migração](../../migration/using/before-starting-migration.md) .

