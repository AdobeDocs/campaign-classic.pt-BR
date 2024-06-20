---
product: campaign
title: Criar e configurar a conta técnica do Adobe para APIs
description: Saiba como criar sua conta da API Adobe
role: User, Admin
level: Beginner
source-git-commit: efd09fd71069878a5096bfa3592e6ebbaa9dd4e4
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 12%

---

# Crie sua conta técnica do Adobe {#create-service-account}

As credenciais de autenticação de servidor para servidor permitem que o servidor do aplicativo gere tokens de acesso e faça chamadas de API em nome do próprio aplicativo. [Saiba mais](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

## Migrar integrações existentes {#migrate-jwt}

A credencial da conta de serviço (JWT) está sendo substituída pelo Adobe. As integrações do Campaign com soluções e aplicativos Adobe agora devem depender da credencial OAuth de servidor para servidor.

Se você tiver implementado integrações de entrada ou saída com o Campaign antes de junho de 2024, será necessário atualizar seu ambiente do Campaign para a v7.4.1 e migrar sua conta técnica para oAuth conforme detalhado [nesta documentação](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration){target="_blank"}. As credenciais da Conta de serviço (JWT) existentes continuarão a funcionar até **27 de janeiro de 2025**.

Depois que a migração for concluída, você deverá associar sua nova credencial ao Campaign, conforme explicado em [nesta seção](#add-credentials).

## Criar nova conta técnica do OAuth para novas integrações {#oauth-service}

Para criar sua conta técnica OAuth para novas integrações, siga estas etapas:

1. Acesse o console do Adobe Developer e faça logon como **Administrador do sistema** da sua organização.

   Para obter mais informações sobre papéis de Administrador, consulte esta [página](https://helpx.adobe.com/br/enterprise/using/admin-roles.html).

1. Clique em **[!UICONTROL Create a new project]**.

   ![](assets/api-account-1.png)

1. Clique em **[!UICONTROL Add to Project]** e selecione **[!UICONTROL API]**.

   ![](assets/api-account-2.png)

1. Selecione o produto que deseja integrar ao Campaign e clique em **[!UICONTROL Next]**.

1. Escolha **[!UICONTROL OAuth Server-to-Server]** como tipo de autenticação e clique em **[!UICONTROL Next]**.

   ![](assets/api-account-3.png)

1. Selecione o **[!UICONTROL Product profile]** para o seu projeto.

   Você pode criar um novo, se necessário. [Saiba mais](https://helpx.adobe.com/enterprise/using/manage-product-profiles.html)

1. Em seguida, clique em **[!UICONTROL Save Configured API]**.

   ![](assets/api-account-4.png)

1. Em seu projeto, em Credencial, selecione [!DNL OAuth Server-to-Server] e copie as seguintes informações:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

## Adicionar credenciais do projeto OAuth no Adobe Campaign {#add-credentials}

Siga as etapas abaixo para adicionar suas credenciais de projeto do OAuth no Adobe Campaign:

1. Faça logon via SSH em cada container em que a instância do Adobe Campaign está instalada.

1. Adicione as credenciais do projeto OAuth no Adobe Campaign executando o seguinte comando como `neolane` usuário. Isso inserirá as credenciais **[!UICONTROL Technical Account]** no arquivo de configuração da instância.

   ```
   nlserver config -instance:<instance_name> -setimsoauth:ims-org-id/client-id/technical-account-id/client-secret
   ```
