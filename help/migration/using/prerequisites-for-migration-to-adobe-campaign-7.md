---
solution: Campaign Classic
product: campaign
title: Pré-requisitos da migração para o Adobe Campaign 7
description: Pré-requisitos da migração para o Adobe Campaign 7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 22%

---


# Pré-requisitos da migração para o Adobe Campaign 7{#prerequisites-for-migration-to-adobe-campaign}

Antes de executar qualquer migração, consulte [Antes de iniciar a migração](../../migration/using/before-starting-migration.md) e [Configurar as seções da plataforma](../../migration/using/configuring-your-platform.md) .

Ao migrar da v6.02 para o Adobe Campaign v7, alguns arquivos entregues anteriormente não são entregues.

Se um erro de cliente for exibido, você precisará atualizar seus painéis com o novo código Adobe Campaign v7 ou copiar manualmente os seguintes arquivos da instância v6.02 para a instância v7:

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
