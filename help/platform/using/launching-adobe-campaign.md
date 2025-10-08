---
product: campaign
title: Iniciar o Adobe Campaign
description: Iniciar o Adobe Campaign
feature: Access Management, Permissions
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
source-git-commit: b4059e43d98643f0f8b5b3f68f03e10b755e8ba3
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 79%

---

# Iniciar o Adobe Campaign {#launching-adobe-campaign}

O console do Campaign Client é um cliente avançado que permite a conexão com seu(s) servidor(es) de aplicativos do Campaign. Saiba como baixar e configurar o console do cliente [nesta página](../../installation/using/installing-the-client-console.md).

>[!CAUTION]
>
>Verifique a compatibilidade do sistema e das ferramentas com o Console do cliente do Adobe Campaign na [Matriz de compatibilidade](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

## Iniciar o Adobe Campaign {#starting-adobe-campaign}

Você pode iniciar o Adobe Campaign selecionando **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

A janela de conexão do console do cliente permite selecionar ou configurar bancos de dados existentes e conectar-se a eles usando um nome de usuário e uma senha:

![](assets/acc-logon.png)

## Conexão com o Adobe Campaign {#connecting-to-adobe-campaign}

### Conectar-se ao Adobe ID

Os usuários do Campaign se conectam ao console do Adobe Campaign usando a Adobe ID, por meio do Sistema de gerenciamento de identidades (IMS) da Adobe. É possível usar a mesma ID em todas as soluções da Adobe. A conexão é salva ao usar o Adobe Campaign com outras soluções. Saiba mais sobre o Adobe IMS [nesta página](https://helpx.adobe.com/br/enterprise/using/identity.html).

Para configurar a conexão do Campaign Classic v7 com o Adobe Identity Management Service (IMS), consulte [esta página](../../integrations/using/about-adobe-id.md).

Quando a configuração estiver concluída, saiba como se conectar ao Campaign com sua Adobe ID na [documentação do Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/new/connect){target=_blank}.


### Conectar-se com um logon/senha

Você também pode se conectar com um login/senha dedicado. Essa conexão é conhecida como a &quot;Autenticação nativa&quot; do Campaign:

1. Digite o identificador da conta do operador no campo **[!UICONTROL Login]**.

   Seu identificador é fornecido pelo administrador da plataforma Adobe Campaign.

1. Digite sua senha no campo **[!UICONTROL Password]**.

   Na primeira vez que você acessar o banco de dados, sua senha será fornecida pelo administrador. Depois de conectado, você poderá alterar a senha usando o menu **[!UICONTROL Tools > Change password...]** Os detalhes sobre operadores e conexões estão disponíveis em [Gerenciamento de acesso](../../platform/using/access-management.md).

1. Clique em **[!UICONTROL LOG IN]** para confirmar.

Agora, você pode acessar o [Workspace do Adobe Campaign](../../platform/using/adobe-campaign-workspace.md).

## Configurar conexões {#setting-up-connections}

É possível acessar as configurações de conexão do servidor pelo link acima da zona de entrada.

![](assets/s_ncs_user_connections_management.png)

Saiba como configurar conexões na [documentação do Campaign v8 (console)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/connect#create-your-connection){target=_blank}.

## Operadores e permissões {#operators-and-permissions}

Os identificadores e senhas dos operadores com acesso ao software e suas respectivas permissões são definidos pelo administrador do sistema no caminho **[!UICONTROL Administration > Access management > Operators]** do Adobe Campaign.

Essa funcionalidade é detalhada na seção [Gerenciamento de acesso](../../platform/using/access-management.md).

## Obtenha a sua versão do Adobe Campaign {#getting-your-campaign-version}

O menu **[!UICONTROL Help > About...]** permite acessar as seguintes informações:

* **número de** versão do console do cliente Campaign e o servidor de aplicativos
* **número da** compilação do console do cliente Campaign e o servidor de aplicativos
* um link para entrar em contato com o Atendimento ao cliente da Adobe
* links para Política de privacidade da Adobe, Termos de uso e Política de cookies

![](assets/about-acc.png)

Sempre que entrar em contato com a equipe de Atendimento ao cliente da Adobe, você precisará fornecer o número da versão e o número da compilação do seu console de cliente do Adobe Campaign e do servidor de aplicativos.

