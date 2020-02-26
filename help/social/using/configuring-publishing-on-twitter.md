---
title: Configuração da publicação no Twitter
seo-title: Configuração da publicação no Twitter
description: Configuração da publicação no Twitter
seo-description: null
page-status-flag: never-activated
uuid: 88867881-fb59-4f0d-862e-537d498e9aef
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: 9d74ed9c-0055-4556-a205-6e5fea11816b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 963aaa81971a8883b944bfcf4d1a00d729627916

---


# Configuração da publicação no Twitter{#configuring-publishing-on-twitter}

Para que o Adobe Campaign possa enviar tweets para suas contas do Twitter, é necessário delegar acesso de gravação ao Adobe Campaign para essas contas. Para fazer isso, aplique as seguintes etapas de configuração:

* Crie uma conta do Twitter.
* Crie uma conta do Twitter de teste para enviar provas.
* Crie um aplicativo do Twitter por conta do Twitter.
* Para cada aplicativo do Twitter, crie um novo **[!UICONTROL Twitter]** tipo de serviço.

![](assets/social_diagram_twitter_service.png)

## Pré-requisitos {#prerequisites}

Comece criando uma ou mais contas do Twitter para enviar seus tweets.

Para criar uma conta do Twitter, acesse [https://twitter.com](https://twitter.com).

## Criação de uma conta de teste no Twitter {#creating-a-test-account-on-twitter}

Também recomendamos criar uma conta privada do Twitter que possa ser usada para enviar provas de tweet (para obter mais informações, consulte [Enviar a prova](../../social/using/publishing-on-twitter.md#sending-the-proof)):

* Crie uma nova conta do Twitter.
* Clique no menu no canto superior direito e selecione **[!UICONTROL Settings]**.
* Selecione a **[!UICONTROL Security and privacy]** guia e marque a **[!UICONTROL Protect my Tweets]** caixa.
* Clique no **[!UICONTROL Save Changes]** botão na parte inferior da página.

![](assets/social_twitter_test_page.png)

## Criação de um aplicativo no Twitter {#creating-an-application-on-twitter}

Para que o Adobe Campaign possa enviar tweets para suas contas do Twitter, é necessário criar um aplicativo do Twitter por conta do Twitter. Para fazer isso, siga as etapas abaixo:

1. Faça logon em sua conta do Twitter.
1. Digite o seguinte endereço no navegador da Internet: [https://apps.twitter.com/](https://apps.twitter.com/).
1. Em seguida, clique no **[!UICONTROL Create New App]** botão à direita.

   ![](assets/social_create_twitter_app_001.png)

1. Deixe o assistente orientá-lo pelo processo.

   Para que esse aplicativo permita que o Adobe Campaign envie tweets para sua conta, vá para a **[!UICONTROL Permissions]** guia do aplicativo e selecione **[!UICONTROL Read and Write]** a seção **[!UICONTROL Access]** . Na **[!UICONTROL Settings]** guia, também é necessário deixar o **[!UICONTROL Callback URL]** campo vazio.

   ![](assets/social_create_twitter_app_002.png)

## Delegando acesso de gravação ao Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Para cada aplicativo do Twitter, é necessário criar um serviço de **[!UICONTROL Twitter]** tipo diferente que incluirá as configurações do aplicativo.

Esta etapa requer acesso simultâneo ao console do Adobe Campaign e um navegador da Internet conectado à sua conta do Twitter:

* **Twitter**: selecione o aplicativo criado anteriormente ([https://dev.twitter.com/apps](https://dev.twitter.com/apps)) e clique na **[!UICONTROL Keys and Access Tokens]** guia.

   ![](assets/social_twitter_service_002.png)

* **Adobe Campaign**: vá para o **[!UICONTROL Profiles and targets]** universo, clique no **[!UICONTROL Services and Subscriptions]** link e clique no **[!UICONTROL Create]** botão.

   ![](assets/social_twitter_service_007.png)

1. Select the **[!UICONTROL Twitter]** type.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >A **[!UICONTROL Synchronize subscriptions]** opção é ativada por padrão. Quando a caixa é marcada, o fluxo de trabalho de sincronização de conta do Twitter (consulte [Sincronização de contas](#synchronizing-twitter-accounts)do Twitter) recupera a lista de seguidores do Twitter para que você possa enviá-los mensagens diretas (consulte [Envio de mensagens diretas a assinantes](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers)). Se não quiser recuperar a lista de seguidores, desmarque essa caixa.

1. Insira o rótulo e o nome interno do serviço.

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >O nome **[!UICONTROL Internal name]** do serviço deve ser idêntico ao nome da conta do Twitter. Para garantir que não haja erros de entrada, execute as etapas a seguir.

   * Clique no botão **[!UICONTROL Save]**.
   * Na visão geral dos serviços, clique no serviço de tipo Twitter que você acabou de criar.
   * Select the **[!UICONTROL Twitter page]** tab. A conta do Twitter deve ser exibida.

      ![](assets/social_twitter_service_010.png)

1. No **[!UICONTROL Visitor folder]** campo, selecione a pasta de visitante na qual os seguidores serão criados. For more on this, refer to [Operating principle](../../social/using/publishing-on-twitter.md#operating-principle). Por padrão, os seguidores serão criados na raiz da **[!UICONTROL Visitors]** pasta.

   ![](assets/social_twitter_service_010_b.png)

1. No Twitter, copie o conteúdo dos campos **[!UICONTROL Consumer Key (API Key)]** e **[!UICONTROL Consumer Secret (API Secret)]** e cole-o nos campos **[!UICONTROL Consumer key]** e **[!UICONTROL Consumer secret]** do console.

   ![](assets/social_twitter_service_012.png)

1. No Twitter, copie o conteúdo dos campos **[!UICONTROL Access Token]** e **[!UICONTROL Access Token Secret]** e cole-o nos campos **[!UICONTROL Access token]** e **[!UICONTROL Access token secret]** do console.

   ![](assets/social_twitter_service_013.png)

1. No console do Adobe Campaign, clique em **[!UICONTROL Save]**. A delegação de acesso de gravação ao Adobe Campaign está concluída.

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>Você deve criar um serviço de **[!UICONTROL Twitter]** tipo por aplicativo do Twitter.

O **[!UICONTROL Twitter account Synchronization]** fluxo de trabalho sincroniza as contas do Twitter no Adobe Campaign. Para obter mais informações, consulte [Sincronizar páginas](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages)do Facebook.

## Sincronizando contas do Twitter {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>Para que o fluxo de trabalho recupere a lista de assinantes do Twitter, a **[!UICONTROL Twitter account synchronization]** caixa deve ser marcada na seção de edição do serviço vinculado à conta. Para obter mais informações, consulte [Delegando acesso de gravação ao Adobe Campaign](#delegating-write-access-to-adobe-campaign).

O **[!UICONTROL Twitter account synchronization]** fluxo de trabalho, acessado pelo **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** nó, permite sincronizar contas do Twitter configuradas anteriormente com o Adobe Campaign. Por padrão, esse fluxo de trabalho é acionado todas as quintas-feiras às 7h30min.

>[!NOTE]
>
>É possível iniciar o fluxo de trabalho a qualquer momento executando o processamento antecipado da tarefa. Você também pode editar o agendador para alterar a frequência de acionamento do fluxo de trabalho. For more on the scheduler, refer to [this section](../../workflow/using/scheduler.md).

Agora você pode enviar tweets para suas contas do Twitter e mensagens diretas para seus seguidores. Para obter mais informações, consulte: [Publicação no Twitter](../../social/using/publishing-on-twitter.md).
