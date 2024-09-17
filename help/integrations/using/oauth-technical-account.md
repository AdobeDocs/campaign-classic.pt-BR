---
product: campaign
title: Criar e configurar a conta técnica do Adobe para APIs
description: Saiba como criar sua conta da API Adobe
role: User, Admin
level: Beginner
exl-id: 5d830ea0-a0a3-4b35-8dc4-e955380431fb
source-git-commit: 2ce7a91aaddb0df412fc0002ff1463d48b2b7c3c
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 16%

---

# Crie sua conta técnica da Adobe {#create-service-account}

As credenciais de autenticação de servidor para servidor permitem que o servidor do aplicativo gere tokens de acesso e faça chamadas de API em nome do próprio aplicativo. [Saiba mais](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

## Migrar integrações existentes {#migrate-jwt}

A credencial da conta de serviço (JWT) está sendo substituída pelo Adobe. As integrações do Campaign com soluções e aplicativos Adobe agora devem depender da credencial OAuth de servidor para servidor.

Se você implementou integrações de entrada ou saída com o Campaign antes de junho de 2024, atualize seu ambiente do Campaign para v7.4.1 e migre sua conta técnica para oAuth conforme detalhado [nesta documentação](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration){target="_blank"}. As credenciais da conta de serviço (JWT) já existentes continuarão a funcionar até **27 de janeiro de 2025**. 

Depois que a migração for concluída, você deverá associar sua nova credencial ao Campaign, conforme explicado em [esta seção](#add-credentials).

## Criar nova conta técnica do OAuth para novas integrações {#oauth-service}

Para criar sua conta técnica OAuth para novas integrações, siga estas etapas:

1. Acesse o console do Adobe Developer e faça logon como **Administrador do sistema** da organização.

   Para obter mais informações sobre papéis de Administrador, consulte esta [página](https://helpx.adobe.com/br/enterprise/using/admin-roles.html).

1. Clique em **[!UICONTROL Create a new project]**.

   ![](assets/api-account-1.png)

1. Clique em **[!UICONTROL Add to Project]** e selecione **[!UICONTROL API]**.

   ![](assets/api-account-2.png)

1. Selecione o produto que você deseja integrar ao Campaign e clique em **[!UICONTROL Next]**.

1. Escolha **[!UICONTROL OAuth Server-to-Server]** como tipo de autenticação e clique em **[!UICONTROL Next]**.

   ![](assets/api-account-3.png)

1. Selecione o link **[!UICONTROL Product profile]** para o seu projeto.

   Você pode criar um novo, se necessário. [Saiba mais](https://helpx.adobe.com/enterprise/using/manage-product-profiles.html)

1. Em seguida, clique em **[!UICONTROL Save Configured API]**.

   ![](assets/api-account-4.png)

1. Em Credenciais, selecione [!DNL OAuth Server-to-Server] e copie as seguintes informações:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

## Adicionar credenciais do projeto OAuth no Campaign {#add-credentials}

Depois que as etapas acima forem executadas, adicione suas credenciais do projeto OAuth no Adobe Campaign.

>[!NOTE]
>
>Como cliente de Cloud Service hospedado ou gerenciado, essas etapas não são necessárias: o Adobe já adicionou suas credenciais de projeto do OAuth ao seu ambiente.
>

Como cliente no local ou híbrido, siga estas etapas:

1. Faça logon via SSH em cada container em que a instância do Adobe Campaign está instalada.

1. Adicione as credenciais do projeto OAuth no Adobe Campaign executando o seguinte comando como usuário `neolane`. Isso inserirá as credenciais **[!UICONTROL Technical Account]** no arquivo de configuração da instância.

   ```
   nlserver config -instance:<instance_name> -setimsoauth:ims-org-id/client-id/technical-account-id/client-secret
   ```
