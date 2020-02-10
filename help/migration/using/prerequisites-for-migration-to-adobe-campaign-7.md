---
title: Pré-requisitos para migração para o Adobe Campaign 7
seo-title: Pré-requisitos para migração para o Adobe Campaign 7
description: Pré-requisitos para migração para o Adobe Campaign 7
seo-description: null
page-status-flag: never-activated
uuid: 9f4e4cdf-5338-4597-9d9d-5a3bd13033c7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: a3bbd8cc-97c6-4b08-adbf-76ab77b97262
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f460c79a763c6a207656c54351a4c685f2a78a03

---


# Pré-requisitos para migração para o Adobe Campaign 7{#prerequisites-for-migration-to-adobe-campaign}

Antes de executar qualquer migração, consulte [Antes de iniciar a migração](../../migration/using/before-starting-migration.md) e [Configurar as seções da plataforma](../../migration/using/configuring-your-platform.md) .

Ao migrar da v6.02 para o Adobe Campaign v7, alguns arquivos entregues antecipadamente não são entregues.

Se um erro de cliente for exibido, você precisará atualizar seus painéis com o novo código do Adobe Campaign v7 ou copiar manualmente os seguintes arquivos da instância v6.02 para a instância v7:

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
