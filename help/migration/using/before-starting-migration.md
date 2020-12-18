---
solution: Campaign Classic
product: campaign
title: Antes de iniciar a migração
description: Antes de iniciar a migração
audience: migration
content-type: reference
topic-tags: migration-procedure
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 2%

---


# Antes de iniciar a migração{#before-starting-migration}

>[!NOTE]
>
>Nesse documento, os comandos vinculados ao banco de dados são fornecidos como um exemplo. Eles podem variar dependendo de sua configuração. Entre em contato com o administrador do banco de dados.

## Avisos {#warnings}

* O processo de migração deve ser executado somente por usuários especialistas. Você deve ser assistido por pelo menos um especialista em banco de dados, um administrador de sistema e um desenvolvedor de aplicativos da Adobe Campaign.
* Antes de iniciar a migração, verifique se os sistemas e componentes do sistema usados são compatíveis com a v7. Consulte a matriz de compatibilidade [a1/>.](../../rn/using/compatibility-matrix.md)
* Se você usar o Adobe Campaign Cloud Messaging (mid-sourcing), entre em contato com o Adobe antes de iniciar todo o procedimento de migração.
* Antes de iniciar um processo de migração, você **deve** fazer backup de seus dados.
* O processo de migração pode levar vários dias para ser concluído.
* O Adobe Campaign v7 é mais estrito do que as versões 5.11 e 6.02 em termos de configuração. Isso serve principalmente para evitar problemas como corrupção de dados e preservar a integridade dos dados no banco de dados. Consequentemente, certas funções oferecidas na v5.11 e na v6.02 podem não funcionar mais na v7 e podem, portanto, precisar ser adaptadas após a migração. Antes de colocar em produção qualquer coisa, sugerimos que você teste sistematicamente todas as configurações, especialmente os workflows necessários para usar o Adobe Campaign.

### Versão instalada {#installed-version}

Antes de migrar, você deve instalar a versão mais recente da versão atual que está usando.

Verifique a versão do servidor indo para o menu **[!UICONTROL Help> About]** no console do cliente usando o comando **nlserver pdump**.

### Backup de dados {#data-backup}

Antes de iniciar um processo de migração, você **deve** fazer backup de seus dados.

### Ambiente {#environment}

* Não é possível alterar o tipo de mecanismo de banco de dados (DBMS). Por exemplo, você não pode alternar de um mecanismo PostgreSQL para um mecanismo Oracle. Entretanto, você pode alternar de um mecanismo Oracle 8 para um mecanismo Oracle 10.
* Não é possível ir de um banco de dados não Unicode para um banco de dados Unicode.

### Recomendações {#recommendation}

Dado que o procedimento de migração é sensível, recomendamos vivamente que este documento seja lido em profundidade antes de se iniciar o procedimento.

## Etapas de migração {#migration-steps}

O procedimento de migração deve ser executado em **todos** servidores e em uma ordem específica.

* No caso de uma **plataforma independente** (modo de máquina única), o aplicativo é migrado em sua totalidade.
* No caso de uma **plataforma padrão** (corporativa), as etapas de migração são as seguintes:

   1. Migre o servidor de marketing.
   1. Migre o servidor de correio (mta).
   1. Migre os servidores de redirecionamento e rastreamento (Apache / IIS).

* No caso de uma **plataforma Cloud Messaging**, os servidores de execução são hospedados na Adobe Campaign. Entre em contato com a Adobe Campaign para coordenar a migração entre diferentes servidores.
* No caso de uma **Power Booster ou plataforma Power Cluster**, as etapas de migração são as seguintes:

   1. Migre os servidores de redirecionamento e rastreamento (Apache / IIS).
   1. Migre os servidores do Power Booster/Cluster.
   1. Migre o servidor de marketing.

## Senhas de usuário {#user-passwords}

Na v7, a conexão do operador **internal** e **admin** deve ser protegida por uma senha. É altamente recomendável atribuir senhas a essas contas e a todas as contas de operador, **antes da migração**. Se você não tiver especificado uma senha para **internal**, não poderá se conectar. Para atribuir uma senha a **internal**, insira o seguinte comando:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>A senha **internal** deve ser idêntica para todos os servidores de rastreamento. Para obter mais informações, consulte as seções [Identificador interno](../../installation/using/campaign-server-configuration.md#internal-identifier) e [Sobre permissões](../../platform/using/access-management.md#about-permissions).

