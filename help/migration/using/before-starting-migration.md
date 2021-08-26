---
product: campaign
title: Antes de iniciar a migração
description: Antes de iniciar a migração
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 2%

---

# Antes de iniciar a migração{#before-starting-migration}

![](../../assets/v7-only.svg)

>[!NOTE]
>
>Neste documento, comandos vinculados ao banco de dados são fornecidos como exemplo. Elas podem variar dependendo de sua configuração. Entre em contato com o administrador do banco de dados.

## Avisos {#warnings}

* O processo de migração deve ser executado somente por usuários especialistas. Você deve ser assistido por pelo menos um especialista em banco de dados, um administrador de sistema e um desenvolvedor de aplicativos da Adobe Campaign.
* Antes de iniciar a migração, verifique se os sistemas e componentes do sistema usados são compatíveis com o v7. Consulte a [matriz de compatibilidade](../../rn/using/compatibility-matrix.md).
* Se você usar o Adobe Campaign Cloud Messaging (mid-sourcing), entre em contato com o Adobe antes de iniciar todo o procedimento de migração.
* Antes de iniciar um processo de migração, você **deve** fazer backup de seus dados.
* O processo de migração pode levar vários dias para ser concluído.
* O Adobe Campaign v7 é mais rigoroso que as versões 5.11 e 6.02 em termos de configuração. Isso é principalmente para evitar problemas como corrupção de dados e preservar a integridade dos dados no banco de dados. Consequentemente, certas funções oferecidas na v5.11 e v6.02 podem não funcionar mais no v7 e podem, portanto, precisar ser adaptadas após a migração. Antes de colocar em produção qualquer item, sugerimos que você teste sistematicamente todas as configurações, especialmente os workflows necessários para usar o Adobe Campaign.

### Versão instalada {#installed-version}

Antes de migrar, você deve instalar a build mais recente da versão atual que você está usando.

Verifique a versão no seu servidor indo até o menu **[!UICONTROL Help> About]** no console do cliente usando o comando **nlserver pdump**.

### Backup de dados {#data-backup}

Antes de iniciar um processo de migração, você **deve** fazer backup de seus dados.

### Ambiente {#environment}

* Não é possível alterar o tipo de mecanismo de banco de dados (DBMS). Por exemplo, não é possível alternar de um mecanismo PostgreSQL para um mecanismo de Oracle. No entanto, é possível alternar de um mecanismo de Oracle 8 para um mecanismo de Oracle 10.
* Não é possível ir de um banco de dados não Unicode para um banco de dados Unicode.

### Recomendações {#recommendation}

Como o procedimento de migração é delicado, recomendamos ler este documento completamente antes de iniciar o procedimento.

## Etapas de migração {#migration-steps}

O procedimento de migração deve ser executado em **all** servidores e em uma ordem específica.

* No caso de uma **plataforma independente** (modo de máquina única), o aplicativo é migrado em sua totalidade.
* No caso de uma **plataforma padrão** (corporativa), as etapas de migração são as seguintes:

   1. Migre o servidor de marketing.
   1. Migre o servidor de email (mta).
   1. Migre os servidores de redirecionamento e rastreamento (Apache / IIS).

* No caso de uma **plataforma Cloud Messaging**, os servidores de execução são hospedados na Adobe Campaign. Entre em contato com a Adobe Campaign para coordenar a migração entre diferentes servidores.
* No caso de uma **Power Boster ou plataforma Power Cluster**, as etapas de migração são as seguintes:

   1. Migre os servidores de redirecionamento e rastreamento (Apache / IIS).
   1. Migre os servidores Power Boster/Cluster.
   1. Migre o servidor de marketing.

## Senhas do usuário {#user-passwords}

Na v7, a conexão do operador **internal** e **admin** deve ser protegida por uma senha. É altamente recomendável atribuir senhas a essas contas e a todas as contas de operadores, **antes da migração**. Se você não tiver especificado uma senha para **internal**, não será possível se conectar. Para atribuir uma senha a **internal**, digite o seguinte comando:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>A senha **interna** deve ser idêntica para todos os servidores de rastreamento. Para obter mais informações, consulte as seções [Identificador interno](../../installation/using/configuring-campaign-server.md#internal-identifier) e [Permissões](../../platform/using/access-management.md).
