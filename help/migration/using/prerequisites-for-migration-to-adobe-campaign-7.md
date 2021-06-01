---
product: campaign
title: Pré-requisitos da migração para o Adobe Campaign 7
description: Pré-requisitos da migração para o Adobe Campaign 7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 747d8a2c-b13a-4852-a9b5-0d37b236a36f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 22%

---

# Pré-requisitos da migração para o Adobe Campaign 7{#prerequisites-for-migration-to-adobe-campaign}

Antes de executar qualquer migração, consulte as seções [Antes de iniciar a migração](../../migration/using/before-starting-migration.md) e [Configuração da plataforma](../../migration/using/configuring-your-platform.md).

Ao migrar da v6.02 para o Adobe Campaign v7, alguns arquivos entregues anteriormente não são entregues.

Se um erro de cliente for exibido, é necessário atualizar seus painéis com o novo código Adobe Campaign v7 ou copiar manualmente os seguintes arquivos da instância v6.02 para a instância v7:

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
