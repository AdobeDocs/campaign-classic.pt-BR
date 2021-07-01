---
product: campaign
title: Campaign - Conector do Microsoft Dynamics CRM
description: Conecte o Campaign e o Microsoft Dynamics
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 26737940-b3ce-425c-9604-f4cefd19afaa
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: ht
source-wordcount: '947'
ht-degree: 100%

---

# Conecte o Campaign e o Microsoft Dynamics 365{#connect-to-msdyn}

Nesta página, você aprenderá a conectar o Campaign Classic ao **Microsoft Dynamics CRM 365**.

As possíveis implantações são:

* via **API da Web** (recomendado). Consulte [esta seção abaixo](#microsoft-dynamics-implementation-step) para saber como configurar a conexão com o Microsoft Dynamics.
* com o **Office 365**. Consulte [este vídeo](#microsoft-dynamics-office-365) para saber mais sobre as etapas principais para configurar esta integração.
* para uma implantação **No local**, aplique as etapas principais do Office 365.

A sincronização de dados é realizada por meio de uma atividade de fluxo de trabalho dedicada. [Saiba mais](../../platform/using/crm-data-sync.md).

## Etapas de implementação{#microsoft-dynamics-implementation-steps}

Para conectar o Microsoft Dynamics 365 para trabalhar com o Adobe Campaign via **API da Web**, é necessário aplicar as seguintes etapas:

No Microsoft Dynamics CRM:
1. Obter a ID do Cliente do Microsoft Dynamics
1. Gerar Segredo do Cliente do Microsoft Dynamics
1. Configurar permissões
1. Criar um usuário do aplicativo
1. Codificar a chave privada

[Saiba mais nesta seção](#config-crm-microsoft)

No Campaign Classic:
1. Criar uma nova conta externa
1. Configurar a conta externa com as configurações do Microsoft Dynamics
1. Use o assistente de configuração para mapear tabelas e sincronizar as listas discriminadas
1. Crie o fluxo de trabalho de sincronização

[Saiba mais nesta seção](#configure-acc-for-microsoft)


>[!CAUTION]
>
> Ao conectar o Adobe Campaign com o Microsoft Dynamics, não é possível:
> * Instalar plug-ins que podem alterar o comportamento do CRM, o que pode levar a problemas de compatibilidade com o Adobe Campaign
> * Selecionar várias listas discriminadas
>



## Configurar o Microsoft Dynamics CRM {#config-crm-microsoft}

Para gerar o token de acesso e as chaves para configurar a conta, é necessário fazer logon no [Microsoft Azure Directory](https://portal.azure.com) usando as credenciais de **Administrador global**. Depois, siga as etapas descritas abaixo.

### Obter a ID do Cliente do Microsoft Dynamics {#get-client-id-microsoft}

Para obter a ID do cliente, é necessário registrar um aplicativo no Azure Active Directory. A ID do cliente é a mesma da ID da aplicação.

1. Navegue até **Azure Active Directory > Registros de aplicativo** e clique em **Novo registro de aplicativo**.
1. Dê um nome exclusivo que possa ajudar a identificar uma instância, como **adobecampaign`<instance identifier>`**.
1. Escolha **Tipo de aplicativo** como **Aplicativo Web/API**.
1. Use `http://localhost` para **URL de logon**.

Depois de salvar, você obtém uma **ID da aplicação** que é o Identificador de Cliente do Campaign.

Saiba mais [nesta página](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory).

### Gerar Segredo do Cliente do Microsoft Dynamics {#config-client-secret-microsoft}

O segredo do cliente é a chave exclusiva da ID do cliente. Para obter o identificador da chave do certificado, siga as etapas abaixo:

1. Navegue até o **Azure Active Directory > Registros de aplicativo** e selecione o Aplicativo que foi criado anteriormente.
1. Clique em **Certificados e Segredo**.
1. Clique em **Fazer upload do certificado** e procure e faça upload do seu certificado público gerado.
1. Para gerar o certificado, é possível usar o openssl.

   Por exemplo:

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

1. Clique no link **manifest** para obter o **identificador de chave de certificado** e a **ID de chave**.

### Configurar permissões {#config-permissions-microsoft}

Você precisa configurar as **Permissões necessárias** para o aplicativo que foi criado.

1. Navegue até **Azure Active Directory > Registros de aplicativo** e selecione o Aplicativo que foi criado anteriormente.
1. Clique em **Configurações** no canto superior esquerdo.
1. Em **Permissões necessárias**, clique em **Adicionar** e **Selecionar uma API > Dynamics CRM Online**.
1. Em seguida, clique em **Selecionar**, ative a caixa de seleção **Acessar o Dynamics 365 como usuários da organização** e clique em **Selecionar**.

### Criar um usuário do aplicativo {#create-app-user-microsoft}

O usuário do aplicativo é o usuário que o aplicativo registrado acima usará. Todas as alterações feitas no Microsoft Dynamics usando o aplicativo registrado acima serão feitas por meio desse usuário.

**Etapa 1**: criar um usuário não interativo no Azure Active Directory

1. Clique em **Azure Ative Directory > Usuários** e clique em **Novo usuário**.
1. Dê um nome adequado que você deseja usar, e o nome de usuário deve ser um formato do email.
1. Escolha **Administrador do Dynamics 365** na **Função de diretório**.

**Etapa 2**: atribuir uma licença adequada ao usuário criado

1. No [Microsoft Azure](https://portal.azure.com), clique em **Aplicativo admin**.
1. Vá para **Usuários > Usuários ativos** e clique no usuário recém-criado.
1. Clique em **Editar licenças de produto** e selecione o **Plano de Envolvimento do Cliente do Dynamics 365**.
1. Clique em **Fechar**.

**Etapa 3**: criar um usuário do aplicativo no Dynamics CRM

1. No [Microsoft Azure](https://portal.azure.com), navegue até **Configurações > Segurança > Usuários**.
1. Clique na lista suspensa, selecione **Usuários do aplicativo** e clique em **Novo**.
1. Use o mesmo nome de usuário que o usuário criado no active directory acima

   >[!NOTE]
   >
   >O uso do mesmo nome gera um erro de chave do duplicado, portanto, até que tenhamos uma confirmação de que essa etapa é necessária, use um nome de usuário diferente e continue.

1. Atribua o **ID da aplicação** para [o aplicativo criado anteriormente](#get-client-id-microsoft).
1. Clique em **Gerenciar funções** e escolha a função **Administrador do sistema** para o usuário.

## Configurar o Campaign {#configure-acc-for-microsoft}

Para conectar o Microsoft Dynamics 365 e o Campaign, é necessário criar e configurar uma Conta externa dedicada no Campaign.

1. Navegue até **[!UICONTROL Administration > Platform > External accounts]**.

1. Para criar uma nova conta externa, selecione o tipo **[!UICONTROL Microsoft Dynamics CRM]** e a opção **[!UICONTROL Enable]**.

1. Selecione o tipo de implantação **[!UICONTROL Web API]**:

   O Adobe Campaign Classic oferece suporte à interface REST do Dynamics 365 com protocolo OAuth para autenticação com um **[!UICONTROL Certificate]** ou **[!UICONTROL Password Credentials]**.

   Use as configurações [definidas anteriormente](#get-client-id-microsoft) no Azure Directory para configurar a conta externa.

   ![](assets/crm-ms-dynamics-ext-account.png)

   >[!NOTE]
   >
   >A configuração de Conta externa do Microsoft Dynamics CRM está detalhada [nesta seção](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account).

1. Clique no **[!UICONTROL Microsoft CRM configuration wizard...]** link: O Adobe Campaign detecta automaticamente as tabelas do modelo de dados do Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_02.png)

1. Selecione as tabelas a serem recuperadas.

   ![](assets/crm_connectors_msdynamics_03.png)

1. Clique em **[!UICONTROL Next]** para começar a criar o esquema correspondente.

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >Para aprovar a configuração, você deve se desconectar/reconectar ao console do Adobe Campaign.

   Você pode verificar se o esquema de dados correspondente fica disponível no Adobe Campaign.

   ![](assets/crm_connectors_msdynamics_05.png)

1. Clique no link **[!UICONTROL Synchronizing enumerations...]** para começar a sincronizar enumerações entre o Adobe Campaign e o Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_06.png)

O Campaign e o Microsoft Dynamics agora estão conectados. Você pode configurar a sincronização de dados entre os dois sistemas. Saiba mais na seção [Sincronização de dados](../../platform/using/crm-data-sync.md).

## Configurar a integração do Microsoft Dynamics CRM Office 365{#microsoft-dynamics-office-365}

Assista a este vídeo para saber como integrar o Dynamics 365 com o Adobe Campaign Classic, no contexto de uma implantação do Office 365.

>[!VIDEO](https://video.tv.adobe.com/v/23837?quality=12)


## Tipos de dados de campo suportados {#ms-dyn-supported-types}

Os tipos de atributos suportados/não suportados do Microsoft Dynamics 365 estão listados abaixo:


| Tipo de atributo | Suportado |
| --------------------------------------------------------------------------------- | --------- |
| Tipos básicos: booleano, datetime, decimal, float, duplo, integer, bigint, string | Sim |
| Dinheiro (como duplo) | Sim |
| memo, entityname, primarykey, uniqueidentifier (como strings) | Sim |
| Status, lista de opções (armazenamos os valores possíveis na lista discriminada), estado (string) | Sim |
| proprietário (como string) | Sim |
| Pesquisa (somente pesquisas de referência de entidade única) | Sim |
| cliente | Não |
| Sobre | Não |
| PartyList | Não |
| ManagedProperty | Não |
