---
title: Publicação nas paredes do Facebook
seo-title: Publicação nas paredes do Facebook
description: Publicação nas paredes do Facebook
seo-description: null
page-status-flag: never-activated
uuid: 02288473-a0d7-42b5-9f86-3c96550ab1a8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: 8577db0b-f1fc-41af-aa0f-ec4d02dac376
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2e18121e4094bc4cb215e5471091810df56b3ef5

---


# Publicação nas paredes do Facebook{#publishing-on-facebook-walls}

Para que o Adobe Campaign possa enviar publicações para as paredes do Facebook, é necessário delegar o acesso de gravação dessas páginas ao Adobe Campaign. Isso envolve as seguintes etapas de configuração:

1. Crie uma conta do Facebook com uma ou mais páginas.
1. Crie uma página de teste do Facebook para enviar provas.
1. Crie um aplicativo do Facebook.
1. Insira as configurações do aplicativo do Facebook no Adobe Campaign, na conta **[!UICONTROL Facebook routing]** externa.

## Pré-requisitos {#prerequisites}

Comece criando uma conta do Facebook e várias páginas: serão utilizados para enviar publicações.

* Para criar uma conta do Facebook, use o link [https://www.facebook.com](https://www.facebook.com) .
* Para criar uma página do Facebook, use o link [https://www.facebook.com/pages/create.php](https://www.facebook.com/pages/create.php) .

   Recomendamos usar a mesma conta do Facebook para administrar todas as suas páginas. Dessa forma, você precisará apenas de um aplicativo do Facebook e de uma conta externa para gravar em todas as páginas da conta.

   ![](assets/social_diagram_fb_external_account.png)

## Criação de uma página de teste do Facebook {#creating-a-test-facebook-page}

Recomendamos criar uma página privada do Facebook para fornecer provas de publicação (para obter mais informações, consulte [Enviar a prova](#sending-the-proof)).

1. Faça logon na conta do Facebook que você usa para administrar suas páginas.
1. Crie uma nova página do Facebook.
1. Clique no **[!UICONTROL Settings]** botão no canto superior direito.
1. Na **[!UICONTROL General]** guia, modifique os parâmetros de visibilidade da página: marque a **[!UICONTROL Page unpublished]** caixa.
1. Clique no botão **[!UICONTROL Save Changes]**.

![](assets/social_facebook_test_page.png)

## Criação de um aplicativo do Facebook {#creating-a-facebook-application}

Para que o Adobe Campaign possa publicar nas paredes de suas páginas, é necessário criar um aplicativo do Facebook. Para fazer isso, siga as etapas abaixo:

1. Faça logon na conta do Facebook que você usa para administrar páginas.
1. Digite o seguinte endereço no seu navegador: [https://developers.facebook.com/apps](https://developers.facebook.com/apps).

   >[!IMPORTANT]
   >
   >Dependendo do tipo de conta que você possui, uma ou mais autorizações podem ser necessárias.
   >
   >Para criar um aplicativo do Facebook, você precisará de uma conta do Facebook **verificada** .

1. Clique no **[!UICONTROL Add a New App]** botão no canto superior direito da página. Digite um nome de aplicativo e um email de contato e passe a verificação de segurança.

   ![](assets/social_create_facebook_app_002.png)

1. Em **[!UICONTROL Settings > Basic]**, clique em **[!UICONTROL Add a platform]** e selecione o **[!UICONTROL Facebook Web Games]** tipo.

   ![](assets/social_create_facebook_app_003.png)

1. Na **[!UICONTROL Products]** seção, no menu esquerdo, verifique se o **[!UICONTROL Facebook Login]** produto está visível. Caso contrário, adicione um novo produto e selecione **[!UICONTROL Facebook Login]**.

   ![](assets/social_create_facebook_app_003bis.png)

1. Depois que o aplicativo for criado, selecione a **[!UICONTROL App Review]** guia e publique o aplicativo.

   ![](assets/social_create_facebook_app_004.png)

## Delegando acesso de gravação ao Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Para delegar o acesso de gravação ao Adobe Campaign para publicação nas paredes de suas páginas, é necessário inserir os parâmetros do aplicativo do Facebook criado anteriormente.

Esta etapa requer acesso ao console do Adobe Campaign e a um navegador da Internet conectado à conta do Facebook que você usa para a administração da página:

>[!IMPORTANT]
>
>O operador do Adobe Campaign deve ter direitos administrativos para executar essa configuração.

* **Facebook**: selecione o aplicativo criado anteriormente ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)) e selecione a **[!UICONTROL Settings > Basic]** guia.

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >Se a **[!UICONTROL Facebook Web Games]** seção não for exibida, clique no **[!UICONTROL Add Platform]** botão, na parte inferior da página, e selecione **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: vá para o **[!UICONTROL Administration > Platform > External Accounts]** nó da árvore, selecione a conta **[!UICONTROL Facebook routing]** externa e clique na **[!UICONTROL Connector]** guia.

   ![](assets/social_facebook_external_account_001.png)

1. No console do Adobe Campaign, copie o endereço contido no **[!UICONTROL Secure Canvas URL]** campo e cole-o no **[!UICONTROL Secure Web Games URL (https)]** campo do Facebook (na **[!UICONTROL Facebook Web Games]** seção).

   ![](assets/social_facebook_external_account_006.png)

   >[!IMPORTANT]
   >
   >Você não deve usar o URL inseguro em nenhuma circunstância.

   Copie e cole este URL também em **[!UICONTROL Products]** > **[!UICONTROL Facebook Login]** > **[!UICONTROL Settings]** > **[!UICONTROL Valid OAuth Redirect URIs]**. Para verificar a validade do URL, salve o aplicativo, copie e cole o URL no **[!UICONTROL Redirect URI to Check]** campo e clique em **[!UICONTROL Check URI]**.

   ![](assets/social_facebook_external_account_007bis.png)

1. No Facebook, copie o conteúdo dos campos **[!UICONTROL App ID]** e **[!UICONTROL App Secret]** e cole-o nos campos correspondentes do console.

   ![](assets/social_facebook_external_account_007.png)

1. No Facebook, clique no **[!UICONTROL Save Changes]** botão na parte inferior da página.
1. Vá para o console do Adobe Campaign e salve a conta externa.

   >[!NOTE]
   >
   >O **[!UICONTROL Marketing URL]** campo é opcional.

1. No console do Adobe Campaign, clique no **[!UICONTROL Request the authorization from the application]** link na parte inferior da **[!UICONTROL Connector]** guia. O **[!UICONTROL Synchronize Facebook pages]** fluxo de trabalho é acionado automaticamente e coleta todas as páginas do Facebook gerenciadas pelo administrador. Para obter mais informações, consulte [Sincronizar páginas](#synchronizing-facebook-pages)do Facebook.

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >Por padrão, as páginas são adicionadas à pasta **[!UICONTROL Facebook]** de serviço, disponível pelo **[!UICONTROL Profiles and Targets > Services and Subscriptions]** nó. O **[!UICONTROL Folder]** campo da guia **[!UICONTROL Connector]** permite alterar a pasta de serviço na qual as páginas do Facebook são criadas após a sincronização. Você também pode selecionar as páginas do Facebook que deseja sincronizar no Adobe Campaign graças ao **[!UICONTROL Filter]** campo. Se você deixar esse campo vazio, todas as páginas do Facebook gerenciadas pelo administrador serão sincronizadas.

1. Uma caixa de diálogo é exibida com as várias configurações de permissão do Facebook. Isso permite que o Adobe Campaign envie publicações para as páginas de conta do Facebook.

   Aceite as várias solicitações de permissão.

   ![](assets/social_facebook_external_account_003.png)

1. O Adobe Campaign recebeu o direito de publicar nas paredes das páginas da conta do Facebook.

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>Se a conta do Facebook administra várias páginas, basta configurar uma conta externa para gravar em qualquer página da conta do Facebook. Para cada nova conta do Facebook, será necessário criar um novo **[!UICONTROL Routing]** tipo de conta externa.

O **[!UICONTROL Synchronization of Facebook pages]** fluxo de trabalho sincroniza todas as páginas administradas pela conta do Facebook para permitir que você poste diretamente em seu mural por meio do Adobe Campaign. Para obter mais informações, consulte [Sincronizar páginas](#synchronizing-facebook-pages)do Facebook.

## Sincronizar páginas do Facebook {#synchronizing-facebook-pages}

O **[!UICONTROL Synchronization of Facebook pages]** fluxo de trabalho, acessado pelo **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** nó, permite sincronizar (no Adobe Campaign) as páginas da conta do Facebook configuradas anteriormente. Por padrão, esse fluxo de trabalho é configurado para ser executado uma vez por dia ou sempre que um administrador clicar no **[!UICONTROL Request an authorization from the application]** link na tela de configuração do serviço (consulte [Delegando acesso de gravação ao Adobe Campaign](#delegating-write-access-to-adobe-campaign)).

Quando a sincronização estiver concluída, as páginas coletadas aparecerão na pasta de serviço inserida na conta externa (consulte [Delegando acesso de gravação ao Adobe Campaign](#delegating-write-access-to-adobe-campaign)). Por padrão, as páginas são adicionadas à raiz da pasta de **[!UICONTROL Facebook]** serviço que está disponível por meio do **[!UICONTROL Profiles and Targets > Services and subscriptions]** menu.

![](assets/social_facebook_service_002.png)

Agora você pode publicar nas paredes de suas páginas do Facebook diretamente pelo Adobe Campaign. Para obter mais informações, consulte [Publicação no Facebook](#publishing-on-facebook-walls).
