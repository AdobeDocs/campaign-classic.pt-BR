---
solution: Campaign Classic
product: campaign
title: Conector do Microsoft Dynamics CRM
description: Connect Campaign e Microsoft Dynamics
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 7478ae37aee5e8b0d9c904f5b9d810375d9d6481
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 4%

---


# Connect Campaign e Microsoft Dynamics 365{#connect-to-msdyn}

Nesta página, você aprenderá a conectar o Campaign Classic a **Microsoft Dynamics CRM 365**.

As possíveis implantações são:

* via **API Web** (recomendado). Consulte [a seção abaixo](#microsoft-dynamics-implementation-step) para saber mais sobre as etapas para configurar a conexão com o Microsoft Dynamics.
* com **Office 365**. Consulte [este vídeo](#microsoft-dynamics-office-365) para saber mais sobre as etapas principais para configurar esta integração.
* para uma implantação **Local**, aplique as etapas principais do Office 365.

A sincronização de dados é realizada por meio de uma atividade de fluxo de trabalho dedicada. [Saiba mais](../../platform/using/crm-data-sync.md).


>[!NOTE]
>
> A versão dos sistemas CRM compatíveis com a Campanha está listada na [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md#CRMconnectors).


## Etapas de implementação{#microsoft-dynamics-implementation-steps}

Para conectar o Microsoft Dynamics 365 para trabalhar com a Adobe Campaign por meio de **API da Web**, é necessário aplicar as seguintes etapas:

No Microsoft Dynamics CRM:
1. Obter a ID do Microsoft Dynamics Client
1. Gerar Segredo do Cliente do Microsoft Dynamics
1. Configurar permissões
1. Criar um usuário do aplicativo
1. Codificar a chave privada

[Saiba mais nesta seção](#config-crm-microsoft)

No Campaign Classic:
1. Criar uma nova conta externa
1. Configurar a conta externa com as configurações do Microsoft Dynamics
1. Use o assistente de configuração para mapear tabelas e sincronizar o lista discriminada
1. Crie o workflow de sincronização

[Saiba mais nesta seção](#configure-acc-for-microsoft)


>[!CAUTION]
> Ao conectar o Adobe Campaign ao Microsoft Dynamics, não é possível:
> * Instale plug-ins que podem alterar o comportamento do CRM e levar a problemas de compatibilidade com o Adobe Campaign
> * Selecionar várias listas discriminadas

>



## Configurar o Microsoft Dynamics CRM {#config-crm-microsoft}

Para gerar o token de acesso e as chaves para configurar a conta, é necessário fazer logon no [Diretório do Microsoft Azure](https://portal.azure.com) usando as credenciais **Administrador global**. Em seguida, siga as etapas descritas abaixo.

### Obter a ID do Cliente do Microsoft Dynamics {#get-client-id-microsoft}

Para obter a ID do cliente, é necessário registrar um aplicativo no Ative Diretory do Azure. A ID do cliente é a mesma do ID da aplicação.

1. Navegue até **Ative Diretory do Azure > Registros do aplicativo** e clique em **Novo registro do aplicativo**.
1. Dê um nome exclusivo que possa ajudar a identificar uma instância, como **adobecampaign`<instance identifier>`**.
1. Escolha **Tipo de aplicativo** como **Aplicativo Web / API**.
1. Use `http://localhost` para **URL de logon**.

Depois de salvar, você obtém um **ID da aplicação** que é o Identificador de Cliente para Campanha.

Saiba mais em [esta página](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory).

### Gerar Segredo do Cliente do Microsoft Dynamics {#config-client-secret-microsoft}

O segredo do cliente é a chave exclusiva da ID do cliente. Para obter o identificador da chave do certificado, siga as etapas abaixo:

1. Navegue até **Ative Diretory do Azure > Registros do aplicativo** e selecione o Aplicativo que foi criado anteriormente.
1. Clique em **Certificados e Segredo**.
1. Clique em **Carregar certificado** e procure e carregue seu certificado público gerado.
1. Para gerar o certificado, você pode usar openssl.

   Por exemplo:

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

1. Clique no link **manifest** para obter o **identificador de chave de certificado** e a **ID de chave**.

### Configurar permissões {#config-permissions-microsoft}

Você precisa configurar as **Permissões necessárias** para o aplicativo que foi criado.

1. Navegue até **Ative Diretory do Azure > Registros do aplicativo** e selecione o Aplicativo que foi criado anteriormente.
1. Clique em **Configurações** no canto superior esquerdo.
1. Em **Permissões necessárias**, clique em **Adicionar** e **Selecione uma API > Dynamics CRM Online**.
1. Clique em **Marque**, ative a caixa de seleção **Acessar o Dynamics 365 como usuários da organização** e clique em **Selecionar**.

### Criar um usuário do aplicativo {#create-app-user-microsoft}

O usuário do aplicativo é o usuário que o aplicativo registrado acima usará. Todas as alterações feitas no Microsoft Dynamics usando o aplicativo registrado acima serão feitas por meio deste usuário.

**Etapa 1**: Criar um usuário não interativo no diretório ativo do Azure

1. Clique em **Azure Ative Diretory > Usuários** e clique em **Novo usuário**.
1. Dê um nome adequado que você deseja usar e o nome de usuário deve ser um formato do email.
1. Escolha **Administrador do Dynamics 365** na **Função de Diretório**.

**Etapa 2**: Atribuir uma licença adequada ao usuário criado

1. Em [Microsoft Azure](https://portal.azure.com), clique em **Aplicativo admin**.
1. Vá para **Usuários > Usuários ativos** e clique no usuário recém-criado.
1. Clique em **Editar licenças de produto** e selecione o **Plano de Envolvimento do Cliente do Dynamics 365**.
1. Clique em **Fechar**.

**Etapa 3**: Criar um usuário do aplicativo no Dynamics CRM

1. Em [Microsoft Azure](https://portal.azure.com), navegue até **Configurações > Segurança > Usuários**.
1. Clique na lista suspensa, selecione **Usuários do aplicativo** e clique em **Novo**.
1. Use o mesmo nome de usuário que o usuário criado no diretório ativo acima

   >[!NOTE]
   >
   >O uso do mesmo nome gera um erro de chave do duplicado, portanto, até que tenhamos uma confirmação de que essa etapa é necessária, use um nome de usuário diferente e continue.

1. Atribua **ID da aplicação** para [o aplicativo criado anteriormente](#get-client-id-microsoft).
1. Clique em **Gerenciar funções** e escolha a função **Administrador do sistema** para o usuário.

## Configurar Campanha {#configure-acc-for-microsoft}

Para conectar o Microsoft Dynamics 365 e o Campaign, é necessário criar e configurar uma Conta externa dedicada no Campaign.

1. Navegue até **[!UICONTROL Administration > Platform > External accounts]**.

1. Crie uma nova conta externa, selecione o tipo **[!UICONTROL Microsoft Dynamics CRM]** e a opção **[!UICONTROL Enable]**.

1. Selecione o tipo de implantação **[!UICONTROL Web API]**:

   A Adobe Campaign Classic oferece suporte à interface REST do Dynamics 365 com protocolo OAuth para autenticação com **[!UICONTROL Certificate]** ou **[!UICONTROL Password Credentials]**.

   Use as configurações [definidas anteriormente](#get-client-id-microsoft) no Diretório do Azure para configurar a conta externa.

   ![](assets/crm-ms-dynamics-ext-account.png)

   >[!NOTE]
   >
   >A configuração de Conta externa do Microsoft Dynamics CRM está detalhada [nesta seção](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account).

1. Clique no link **[!UICONTROL Microsoft CRM configuration wizard...]**: A Adobe Campaign detecta automaticamente as tabelas do modelo de dados do Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_02.png)

1. Selecione as tabelas a serem recuperadas.

   ![](assets/crm_connectors_msdynamics_03.png)

1. Clique em **[!UICONTROL Next]** para criar o start correspondente.

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >Para aprovar a configuração, você deve se desconectar/reconectar ao console do Adobe Campaign.

   Você pode verificar se o schema de dados correspondente fica disponível no Adobe Campaign.

   ![](assets/crm_connectors_msdynamics_05.png)

1. Clique no link **[!UICONTROL Synchronizing enumerations...]** para sincronizar listas discriminadas de start entre o Adobe Campaign e o Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_06.png)

Campaign e Microsoft Dynamics agora estão conectados. Você pode configurar a sincronização de dados entre os dois sistemas. Saiba mais na seção [Sincronização de dados](../../platform/using/crm-data-sync.md).

## Configurar a integração do Microsoft Dynamics CRM Office 365{#microsoft-dynamics-office-365}

Assista a este vídeo para saber como integrar o Dynamics 365 com a Adobe Campaign Classic, no contexto de uma implantação do Office 365.

>[!VIDEO](https://video.tv.adobe.com/v/23837?quality=12)
