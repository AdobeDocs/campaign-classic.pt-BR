---
title: Iniciar o Adobe Campaign
seo-title: Iniciar o Adobe Campaign
description: Iniciar o Adobe Campaign
seo-description: null
page-status-flag: never-activated
uuid: c1c5bb0d-ae8e-4b0e-ab39-8b2291162557
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 6652b081-66b6-47a8-97e5-383e3251647e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 51e4d72abf3a1f48700ca38566dbf06dd24594b8

---


# Iniciar o Adobe Campaign{#launching-adobe-campaign}

## Introdução ao Adobe Campaign {#starting-adobe-campaign}

Você pode iniciar o Adobe Campaign selecionando **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

A janela de conexão do console do cliente permite selecionar ou configurar bancos de dados existentes e conectar-se a eles usando um nome de usuário e uma senha:

![](assets/s_ncs_user_login.png)

## Conexão com o Adobe Campaign {#connecting-to-adobe-campaign}

Você pode se conectar ao Adobe Campaign usando sua Adobe ID. Para obter mais informações, consulte [esta página](../../integrations/using/about-adobe-id.md).

Também é possível conectar-se com uma combinação exclusiva de login e senha:

1. Digite o identificador da conta do operador no campo **[!UICONTROL login]**.

   Seu identificador é fornecido pelo administrador da plataforma Adobe Campaign.

1. Digite sua senha no campo **[!UICONTROL Password]**.

   Na primeira vez que você acessar o banco de dados, sua senha será fornecida pelo administrador. Once you are connected, you can change your password via the **[!UICONTROL Tools > Change password...]** menu. Details on operators and connections are available in [Access management](../../platform/using/access-management.md).

1. Click **[!UICONTROL Log in]** to confirm.

Agora, você pode acessar a [área de trabalho do Adobe Campaign](../../platform/using/adobe-campaign-workspace.md).

## Configurar conexões {#setting-up-connections}

É possível acessar as configurações de conexão do servidor pelo link acima da zona de entrada.

![](assets/s_ncs_user_connections_management.png)

Na **[!UICONTROL Connections]** janela, clique em **[!UICONTROL Add > Connection]**.

![](assets/s_ncs_user_add_connexion.png)

Em seguida, defina as configurações de conexão. Para fazer isso:

* Digite um valor em **[!UICONTROL Label]** para atribuir um nome à conexão de banco de dados.
* Adicione o endereço do servidor de aplicativos no campo **[!UICONTROL URL]** . Se você não souber o URL de conexão, contate o administrador.
* Check **[!UICONTROL Connect with an Adobe ID]** for the operators to connect to the console using their Adobe ID. Para obter mais informações, consulte [esta página](../../integrations/using/about-adobe-id.md).
* Click **[!UICONTROL OK]** to validate.

>[!NOTE]
>
>The **[!UICONTROL Add]** button lets you create **[!UICONTROL folders]** to organize all your connections. Basta arrastar e soltar cada conexão em uma pasta.

## Operadores e permissões {#operators-and-permissions}

Os identificadores e senhas dos operadores com acesso ao software e suas respectivas permissões são definidos pelo administrador do sistema no caminho **[!UICONTROL Administration > Access management > Operators]** do Adobe Campaign.

This functionality is detailed in the [Access management](../../platform/using/access-management.md) section.

## Desconectar-se do Adobe Campaign {#disconnecting-from-adobe-campaign}

Para desconectar-se do Adobe Campaign, use o primeiro ícone na barra de ícones.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>Você também pode fechar o aplicativo sem fazer logoff.

## Conheça a sua versão do Campaign {#getting-your-campaign-version}

The **[!UICONTROL Help > About...]** menu lets you access the following information:

* número da **versão**,
* número da **compilação**,
* um link para entrar em contato com o Suporte do Adobe Campaign.

   >[!CAUTION]
   >
   >Sempre que você entrar em contato com a equipe de suporte da Adobe, precisará fornecer o número da versão e o número da compilação do seu console de cliente do Campaign e do servidor de aplicativos.

