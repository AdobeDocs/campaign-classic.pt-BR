---
title: Antes de iniciar a migração
seo-title: Antes de iniciar a migração
description: Antes de iniciar a migração
seo-description: null
page-status-flag: never-activated
uuid: b9325510-2fa5-4be4-9cf0-f37232bbbd8c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: d8877378-fb43-4f32-91c6-60f2f788f916
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 3%

---


# Antes de iniciar a migração{#before-starting-migration}

>[!NOTE]
>
>Nesse documento, os comandos vinculados ao banco de dados são fornecidos como um exemplo. Eles podem variar dependendo de sua configuração. Entre em contato com o administrador do banco de dados.

## Avisos {#warnings}

### Versão instalada {#installed-version}

Antes de migrar, você deve instalar a versão mais recente da versão atual que está usando.

Verifique a versão no servidor indo para o **[!UICONTROL Help> About]** menu no console do cliente usando o comando **nlserver pdump** .

### Backup de dados {#data-backup}

Antes de iniciar um processo de migração, você **deve** fazer backup dos dados.

### Ambiente {#environment}

* Não é possível alterar o tipo de mecanismo de banco de dados (DBMS). Por exemplo, você não pode alternar de um mecanismo PostgreSQL para um mecanismo Oracle. No entanto, você pode alternar de um mecanismo Oracle 8 para um mecanismo Oracle 10.
* Não é possível ir de um banco de dados não Unicode para um banco de dados Unicode.

### Recomendações {#recommendation}

Dado que o procedimento de migração é particularmente sensível, recomendamos vivamente que este documento seja lido em profundidade antes de se iniciar o procedimento.

## Etapas de migração {#migration-steps}

O procedimento de migração deve ser executado em **todos** os servidores e numa ordem específica.

* No caso de uma plataforma **** independente (modo de máquina única), o aplicativo é migrado na sua totalidade.
* No caso de uma plataforma **** padrão (corporativa), as etapas de migração são as seguintes:

   1. Migre o servidor de marketing.
   1. Migre o servidor de correio (mta).
   1. Migre os servidores de redirecionamento e rastreamento (Apache / IIS).

* No caso de uma plataforma **de Mensagens na** nuvem, os servidores de execução são hospedados na Adobe Campaign. Entre em contato com a Adobe Campaign para coordenar a migração entre diferentes servidores.
* No caso de uma plataforma **** Power Booster ou Power Cluster, as etapas de migração são as seguintes:

   1. Migre os servidores de redirecionamento e rastreamento (Apache / IIS).
   1. Migre os servidores do Power Booster/Cluster.
   1. Migre o servidor de marketing.

>[!NOTE]
>
>A comunicação entre um servidor de marketing v6.02 e um servidor v7 Cloud Messaging ou Power Booster/Cluster é possível. No entanto, se você decidir manter seu servidor de marketing v6.02, ele deverá ser atualizado com a versão v6.02 mais recente antes de migrar para o Cloud Messaging ou o Power Booster/Cluster.

## Senhas de usuário {#user-passwords}

Na v7, a conexão do operador **interno** e do **administrador** deve ser protegida por uma senha. Recomendamos atribuir senhas a essas contas e a todas as contas de operadores, **antes da migração**. Se você não tiver especificado uma senha para **interno**, não poderá se conectar. Para atribuir uma senha a **interno**, digite o seguinte comando:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>A senha **interna** deve ser idêntica para todos os servidores de rastreamento. Para obter mais informações, consulte as seções Identificador [](../../installation/using/campaign-server-configuration.md#internal-identifier) interno e [Sobre permissões](../../platform/using/access-management.md#about-permissions) .

