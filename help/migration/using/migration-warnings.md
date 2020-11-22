---
solution: Campaign Classic
product: campaign
title: Avisos de migração
description: Avisos de migração
audience: migration
content-type: reference
topic-tags: migration-overview
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
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

