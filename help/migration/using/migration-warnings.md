---
product: campaign
title: Avisos de migração
description: Avisos de migração
audience: migration
content-type: reference
topic-tags: migration-overview
exl-id: 46b46fc9-c7c9-4c74-b5f3-7935d5368520
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 3%

---

# Avisos de migração{#migration-warnings}

![](../../assets/v7-only.svg)

* O processo de migração é reservado para usuários especialistas. Você deve ser assistido por pelo menos um especialista em banco de dados, um administrador de sistema e um desenvolvedor de aplicativos da Adobe Campaign.
* Antes de iniciar a migração, verifique se os sistemas e componentes do sistema usados são compatíveis com o v7. Consulte o [matriz de compatibilidade](../../rn/using/compatibility-matrix.md).
* Se você usar o Adobe Campaign Cloud Messaging (anteriormente mid-sourcing), entre em contato com a Adobe Campaign antes de iniciar todo o procedimento de migração.
* Antes de iniciar um processo de migração, você **must** faça backup dos seus dados.
* O processo de migração pode levar vários dias para ser concluído.
* O Adobe Campaign v7 é mais rigoroso que as versões 5.11 e 6.02 em termos de configuração. Isso é principalmente para evitar problemas como corrupção de dados e preservar a integridade dos dados no banco de dados. Consequentemente, certas funções oferecidas na v5.11 e v6.02 podem não funcionar mais no v7 e podem, portanto, precisar ser adaptadas após a migração. Antes de colocar em produção qualquer item, sugerimos que você teste sistematicamente todas as configurações, especialmente os workflows necessários para usar o Adobe Campaign.

>[!NOTE]
>
>Você também deve consultar o [Antes de iniciar a migração](../../migration/using/before-starting-migration.md) seção.
