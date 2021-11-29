---
product: campaign
title: Publicar nos murais do Facebook
description: Publicar nos murais do Facebook
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2135a836-245f-406e-b351-c27d38e0f9fd
source-git-commit: b5334de18eca8fc1147ae0c42fe23a6932bf71d2
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 91%

---

# Publicar nos murais do Facebook{#publishing-on-facebook-walls}

![](../../assets/v7-only.svg)

Para que o Adobe Campaign possa enviar publicações para os murais do Facebook, é necessário delegar o acesso de gravação dessas páginas ao Adobe Campaign. Isso envolve as seguintes etapas de configuração:

1. Crie uma conta do Facebook com uma ou mais páginas.
1. Crie uma página de teste do Facebook para enviar provas.
1. Crie um aplicativo do Facebook.
1. Insira as configurações do aplicativo do Facebook no Adobe Campaign, na conta externa de **[!UICONTROL Facebook routing]**.

## Pré-requisitos {#prerequisites}

Comece criando uma conta do Facebook e várias páginas: eles serão utilizados para enviar publicações.

* Para criar uma conta do Facebook, use o link [https://www.facebook.com](https://www.facebook.com).
* Para criar uma página do Facebook, use o link [https://www.facebook.com/pages/create](https://www.facebook.com/pages/create).

   Recomendamos usar a mesma conta do Facebook para administrar todas as suas páginas. Dessa forma, é preciso apenas um aplicativo do Facebook e uma conta externa para gravar em todas as páginas da conta.

   ![](assets/social_diagram_fb_external_account.png)

## Criar uma página de teste do Facebook {#creating-a-test-facebook-page}

Recomendamos criar uma página privada do Facebook para fornecer provas de publicação (para obter mais informações, consulte [esta seção](../../social/using/publishing-on-facebook.md#sending-the-proof).

1. Faça logon na conta do Facebook utilizada para administrar suas páginas.
1. Crie uma nova página do Facebook.
1. Clique no botão **[!UICONTROL Settings]** no canto superior direito.
1. Na guia **[!UICONTROL General]**, modifique os parâmetros de visibilidade da página: marque a caixa **[!UICONTROL Page unpublished]**.
1. Clique no botão **[!UICONTROL Save Changes]**.

![](assets/social_facebook_test_page.png)

## Criar um aplicativo do Facebook {#creating-a-facebook-application}

Para que o Adobe Campaign possa publicar nos murais de suas páginas, é necessário criar um aplicativo do Facebook. Para fazer isso, siga as etapas abaixo:

1. Faça logon na conta do Facebook usada para administrar páginas.
1. Digite o seguinte endereço no navegador: [https://developers.facebook.com/apps](https://developers.facebook.com/apps).

   >[!CAUTION]
   >
   >Dependendo do tipo de conta que você tiver, uma ou mais autorizações podem ser necessárias.
   >
   >Para criar um aplicativo do Facebook, é necessário uma conta do Facebook **verificada**.

1. Clique no botão **[!UICONTROL Add a New App]** no canto superior direito da página. Digite um nome de aplicativo e um email de contato e passe a verificação de segurança.

   ![](assets/social_create_facebook_app_002.png)

1. Em **[!UICONTROL Settings > Basic]**, clique em **[!UICONTROL Add a platform]** e selecione o tipo **[!UICONTROL Facebook Web Games]**.

   ![](assets/social_create_facebook_app_003.png)

1. Na seção **[!UICONTROL Products]**, no menu esquerdo, verifique se o produto **[!UICONTROL Facebook Login]** está visível. Caso contrário, adicione um novo produto e selecione **[!UICONTROL Facebook Login]**.

   ![](assets/social_create_facebook_app_003bis.png)

1. Depois que o aplicativo for criado, selecione a guia **[!UICONTROL App Review]** e publique o aplicativo.

   ![](assets/social_create_facebook_app_004.png)

## Delegar acesso de gravação ao Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Para delegar o acesso de gravação ao Adobe Campaign para publicação nos murais de suas páginas, é necessário inserir os parâmetros do aplicativo do Facebook criado anteriormente.

Esta etapa requer o acesso ao console do Adobe Campaign e a um navegador da Internet conectado à conta do Facebook usada na administração da página:

>[!CAUTION]
>
>O operador do Adobe Campaign deve ter direitos administrativos para executar essa configuração.

* **Facebook**: selecione o aplicativo criado anteriormente ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)) e selecione a guia **[!UICONTROL Settings > Basic]**.

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >Se a seção **[!UICONTROL Facebook Web Games]** não for exibida, clique no botão **[!UICONTROL Add Platform]**, na parte inferior da página, e selecione **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: vá para o nó **[!UICONTROL Administration > Platform > External Accounts]** da árvore, selecione a conta externa de **[!UICONTROL Facebook routing]** e clique na guia **[!UICONTROL Connector]**.

   ![](assets/social_facebook_external_account_001.png)

1. No console do Adobe Campaign, copie o endereço contido no campo **[!UICONTROL Secure Canvas URL]** e o cole no campo **[!UICONTROL Secure Web Games URL (https)]** no Facebook (na seção **[!UICONTROL Facebook Web Games]**).

   ![](assets/social_facebook_external_account_006.png)

   >[!CAUTION]
   >
   >Evite o uso do URL inseguro nas circunstância.

   Copie e cole este URL também em **[!UICONTROL Products]** > **[!UICONTROL Facebook Login]** > **[!UICONTROL Settings]** > **[!UICONTROL Valid OAuth Redirect URIs]**. Para verificar a validade do URL, salve o aplicativo, copie e cole o URL no campo **[!UICONTROL Redirect URI to Check]** e clique em **[!UICONTROL Check URI]**.

   ![](assets/social_facebook_external_account_007bis.png)

1. No Facebook, copie o conteúdo dos campos **[!UICONTROL App ID]** e **[!UICONTROL App Secret]** e o cole nos campos correspondentes do console.

   ![](assets/social_facebook_external_account_007.png)

1. No Facebook, clique no botão **[!UICONTROL Save Changes]** na parte inferior da página.
1. Vá para o console do Adobe Campaign e salve a conta externa.

   >[!NOTE]
   >
   >O campo **[!UICONTROL Marketing URL]** é opcional.

1. No console do Adobe Campaign, clique em **[!UICONTROL Request the authorization from the application]**, na parte inferior da guia **[!UICONTROL Connector]**. O fluxo de trabalho **[!UICONTROL Synchronize Facebook pages]** é acionado automaticamente e coleta todas as páginas do Facebook gerenciadas pelo administrador. [Saiba mais](#synchronizing-facebook-pages).

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >Por padrão, as páginas são adicionadas à pasta de serviço do **[!UICONTROL Facebook]**, disponível por meio do nó **[!UICONTROL Profiles and Targets > Services and Subscriptions]**. O campo **[!UICONTROL Folder]** da guia **[!UICONTROL Connector]** permite alterar a pasta de serviço na qual as páginas do Facebook são criadas após a sincronização. Também é possível selecionar as páginas do Facebook que deseja sincronizar no Adobe Campaign graças ao campo **[!UICONTROL Filter]**. Se deixar esse campo vazio, todas as páginas do Facebook gerenciadas pelo administrador serão sincronizadas.

1. Uma caixa de diálogo é exibida com as várias configurações de permissão do Facebook. Isso permite que o Adobe Campaign envie publicações para as páginas de conta do Facebook.

   Aceite as várias solicitações de permissão.

   ![](assets/social_facebook_external_account_003.png)

1. O Adobe Campaign recebeu o direito de publicar nos murais das páginas da conta do Facebook.

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>Se a conta do Facebook administra várias páginas, basta configurar uma conta externa para publicar em qualquer página da conta do Facebook. Para cada nova conta do Facebook, será necessário criar uma nova conta externa do tipo **[!UICONTROL Routing]**.

O fluxo de trabalho **[!UICONTROL Synchronization of Facebook pages]** sincroniza todas as páginas administradas pela conta do Facebook, para permitir publicar em seu mural diretamente pelo Adobe Campaign. [Saiba mais](#synchronizing-facebook-pages).

## Sincronizar páginas do Facebook {#synchronizing-facebook-pages}

O fluxo de trabalho **[!UICONTROL Synchronization of Facebook pages]**, que é acessado por meio do nó **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]**, permite sincronizar (no Adobe Campaign) as páginas da conta do Facebook configuradas anteriormente. Por padrão, esse workflow é configurado para ser executado uma vez por dia ou sempre que um administrador clicar no botão **[!UICONTROL Request an authorization from the application]** na tela de configuração do serviço. [Saiba mais](#delegating-write-access-to-adobe-campaign).

Quando a sincronização estiver concluída, as páginas coletadas aparecerão na pasta de serviço inserida na conta externa. [Saiba mais](#delegating-write-access-to-adobe-campaign)).

Por padrão, as páginas são adicionadas à raiz da pasta de serviço do **[!UICONTROL Facebook]** que está disponível por meio do menu **[!UICONTROL Profiles and Targets > Services and subscriptions]**.

![](assets/social_facebook_service_002.png)

Agora, é possível publicar nos murais de suas páginas do Facebook diretamente pelo Adobe Campaign. [Saiba mais](#publishing-on-facebook-walls).
