---
product: campaign
title: Antes de iniciar a migração
description: Antes de iniciar a migração
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# Pré-requisitos{#before-starting-migration}



Esta página lista etapas específicas a serem executadas antes de iniciar o processo de migração. Você também deve se referir a [esta página](about-migration.md) para obter mais orientações.

>[!NOTE]
>
>Neste documento, os comandos são fornecidos como amostras. Elas podem variar dependendo da sua configuração.

1. Verifique a versão do Adobe Campaign: antes de migrar, instale a build mais recente da versão atual que você está usando.
1. Faça backup dos dados.
1. Verifique seu ambiente: não é possível alterar o sistema de mecanismo de banco de dados (DBMS). Por exemplo, não é possível alternar de um mecanismo PostgreSQL para um mecanismo de Oracle. No entanto, você pode alternar para a versão mais recente do mecanismo de banco de dados. Observe que não é possível ir de um banco de dados não Unicode para um banco de dados Unicode.

## Etapas de migração {#migration-steps}

O procedimento de migração deve ser executado **all** e em uma ordem específica.

* No caso de um **plataforma independente** (modo de máquina única), o aplicativo é migrado em sua totalidade.
* No caso de um **plataforma padrão** (corporativa), as etapas de migração são as seguintes:

   1. Migre o servidor de marketing.
   1. Migre o servidor de email (mta).
   1. Migre os servidores de redirecionamento e rastreamento (Apache / IIS).

* No caso de um **Plataforma Cloud Messaging**, os servidores de execução são hospedados na Adobe Campaign. Entre em contato com a Adobe Campaign para coordenar a migração entre diferentes servidores.
* No caso de um **Power Boster ou plataforma Power Cluster**, as etapas de migração são as seguintes:

   1. Migre os servidores de redirecionamento e rastreamento (Apache / IIS).
   1. Migre os servidores Power Boster/Cluster.
   1. Migre o servidor de marketing.

## Senhas do usuário {#user-passwords}

Na v7, **interno** e **administrador** a conexão do operador deve ser protegida por uma senha. É altamente recomendável atribuir senhas a essas contas e a todas as contas de operador, **antes da migração**. Se você não tiver especificado uma senha para **interno**, você não poderá se conectar. Para atribuir uma senha a **interno**, digite o seguinte comando:

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>O **interno** a senha deve ser idêntica para todos os servidores de rastreamento. Para obter mais informações, consulte [Identificador interno](../../installation/using/configuring-campaign-server.md#internal-identifier) e [Permissões](../../platform/using/access-management.md) seções.
