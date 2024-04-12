---
product: campaign
title: Antes de iniciar a migração
description: Antes de iniciar a migração
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# Pré-requisitos{#before-starting-migration}



Esta página lista etapas específicas a serem executadas antes de iniciar o processo de migração. Você também deve consultar [esta página](about-migration.md) para obter mais orientações.

>[!NOTE]
>
>Neste documento, os comandos são fornecidos como exemplos. Eles podem variar dependendo da sua configuração.

1. Verifique a versão do Adobe Campaign: antes de migrar, instale o build mais recente da versão atual que você está usando.
1. Faça backup dos seus dados.
1. Verificar o ambiente: não é possível alterar o sistema do mecanismo de banco de dados (DBMS). Por exemplo, não é possível alternar de um mecanismo PostgreSQL para um mecanismo Oracle. No entanto, você pode alternar para a versão mais recente do mecanismo de banco de dados. Observe que não é possível ir de um banco de dados não-Unicode para um banco de dados Unicode.

## Etapas de migração {#migration-steps}

O procedimento de migração deve ser executado em **all** servidores e em uma ordem específica.

* No caso de um **plataforma independente** (modo de máquina única), o aplicativo é migrado na íntegra.
* No caso de um **plataforma padrão** (empresarial), as etapas de migração são as seguintes:

   1. Migrar o servidor de marketing.
   1. Migrar o servidor de email (mta).
   1. Migrar os servidores de redirecionamento e rastreamento (Apache/IIS).

* No caso de um **Plataforma de mensagens em nuvem**, os servidores de execução são hospedados na Adobe Campaign. Entre em contato com a Adobe Campaign para coordenar a migração entre diferentes servidores.
* No caso de um **Plataforma Power Boster ou Power Cluster**, as etapas de migração são as seguintes:

   1. Migrar os servidores de redirecionamento e rastreamento (Apache/IIS).
   1. Migre os servidores Power Boster/Cluster.
   1. Migrar o servidor de marketing.

## Senhas de usuário {#user-passwords}

Na v7, **interno** e **administrador** a conexão do operador deve ser protegida por uma senha. É altamente recomendável atribuir senhas a essas contas e a todas as contas de operador, **antes da migração**. Se você não tiver especificado uma senha para **interno**, você não poderá se conectar. Para atribuir uma senha a **interno**, digite o seguinte comando:

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>A variável **interno** a senha deve ser idêntica para todos os servidores de rastreamento. Para obter mais informações, consulte [Identificador interno](../../installation/using/configuring-campaign-server.md#internal-identifier) e [Permissões](../../platform/using/access-management.md) seções.
