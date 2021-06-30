---
product: campaign
title: Configuração da publicação no Twitter
description: Configuração da publicação no Twitter
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2d2a6e32-587d-4a7b-ba1c-d9140da53f64
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: ht
source-wordcount: '710'
ht-degree: 100%

---

# Configuração da publicação no Twitter{#configuring-publishing-on-twitter}

Para que o Adobe Campaign possa enviar tweets para suas contas do Twitter, é necessário delegar acesso de edição ao Adobe Campaign para essas contas. Para fazer isso, siga as etapas abaixo:

* Crie uma conta do Twitter.
* Crie uma conta do Twitter de teste para enviar provas.
* Crie um aplicativo do Twitter por conta do Twitter.
* Para cada aplicativo do , crie um novo serviço do tipo **[!UICONTROL Twitter]** Twitter.

![](assets/social_diagram_twitter_service.png)

## Pré-requisitos {#prerequisites}

Comece criando uma ou mais contas do Twitter para enviar tweets.

Para criar uma conta do Twitter, acesse [ https://twitter.com](https://twitter.com).

## Criação de uma conta de teste no Twitter {#creating-a-test-account-on-twitter}

Também recomendamos criar uma conta privada do Twitter que possa ser usada para enviar provas de tweet (para obter mais informações, consulte [Envio de prova](../../social/using/publishing-on-twitter.md#sending-the-proof)):

* Crie uma nova conta do Twitter.
* Clique no menu no canto superior direito e selecione **[!UICONTROL Settings]**.
* Selecione a guia **[!UICONTROL Security and privacy]** e marque a caixa **[!UICONTROL Protect my Tweets]**.
* Clique no botão **[!UICONTROL Save Changes]** na parte inferior da página.

![](assets/social_twitter_test_page.png)

## Criação de um aplicativo no Twitter {#creating-an-application-on-twitter}

Para que o Adobe Campaign possa enviar tweets para suas contas do Twitter, é necessário criar um aplicativo do Twitter por conta do Twitter. Para fazer isso, siga as etapas abaixo:

1. Faça logon em sua conta do Twitter.
1. Digite o seguinte endereço no navegador da Internet: [https://apps.twitter.com/](https://apps.twitter.com/).
1. Em seguida, clique no botão **[!UICONTROL Create New App]** à direita.

   ![](assets/social_create_twitter_app_001.png)

1. Deixe o assistente orientá-lo pelo processo.

   Para que esse aplicativo permita que o Adobe Campaign envie tweets para sua conta, vá para a guia **[!UICONTROL Permissions]** do aplicativo e selecione **[!UICONTROL Read and Write]** para a seção **[!UICONTROL Access]**. Na guia **[!UICONTROL Settings]**, também é necessário deixar o campo **[!UICONTROL Callback URL]** vazio.

   ![](assets/social_create_twitter_app_002.png)

## Delegação de acesso de gravação ao Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Para cada aplicativo do , é necessário criar um serviço tipo **[!UICONTROL Twitter]** Twitter diferente que incluirá as configurações do aplicativo.

Esta etapa requer acesso simultâneo ao console do Adobe Campaign e um navegador da Internet conectado à sua conta do Twitter:

* **Twitter**: selecione o aplicativo criado anteriormente ([https://dev.twitter.com/apps](https://dev.twitter.com/apps)) e clique na guia **[!UICONTROL Keys and Access Tokens]**.

   ![](assets/social_twitter_service_002.png)

* **Adobe Campaign**: acesse a guia **[!UICONTROL Profiles and targets]**, clique no link **[!UICONTROL Services and Subscriptions]** e clique no botão **[!UICONTROL Create]**.

   ![](assets/social_twitter_service_007.png)

1. Selecione o tipo **[!UICONTROL Twitter]**.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >A opção **[!UICONTROL Synchronize subscriptions]** é ativada por padrão. Quando a caixa é marcada, o workflow de sincronização de conta do Twitter (consulte [Sincronização de contas do Twitter](#synchronizing-twitter-accounts)) recupera a lista de seguidores do Twitter para os enviar mensagens diretas (consulte [Envio de mensagens diretas a assinantes](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers)). Se não quiser recuperar a lista de seguidores, desmarque essa caixa.

1. Insira o rótulo e o nome interno do serviço.

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >O **[!UICONTROL Internal name]** do serviço deve ser idêntico ao nome da conta do Twitter. Para garantir que não haja erros de entrada, execute as etapas a seguir.

   * Clique no botão **[!UICONTROL Save]**.
   * Na visão geral dos serviços, clique no serviço de tipo Twitter que acabou de criar.
   * Selecione a guia **[!UICONTROL Twitter page]**. A conta do Twitter deve ser exibida.

      ![](assets/social_twitter_service_010.png)

1. No campo **[!UICONTROL Visitor folder]**, selecione a pasta de visitante na qual os seguidores serão criados. Para obter mais informações, consulte [Princípio de operação](../../social/using/publishing-on-twitter.md#operating-principle). Por padrão, os seguidores serão criados na raiz da pasta **[!UICONTROL Visitors]**.

   ![](assets/social_twitter_service_010_b.png)

1. No Twitter, copie o conteúdo dos campos **[!UICONTROL Consumer Key (API Key)]** e **[!UICONTROL Consumer Secret (API Secret)]** e os cole nos campos **[!UICONTROL Consumer key]** e **[!UICONTROL Consumer secret]** do console.

   ![](assets/social_twitter_service_012.png)

1. No Twitter, copie o conteúdo dos campos **[!UICONTROL Access Token]** e **[!UICONTROL Access Token Secret]** e os cole nos campos **[!UICONTROL Access token]** e **[!UICONTROL Access token secret]** do console.

   ![](assets/social_twitter_service_013.png)

1. No console do Adobe Campaign, clique em **[!UICONTROL Save]**. A delegação de acesso de gravação ao Adobe Campaign está concluída.

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>É necessário criar um serviço do tipo **[!UICONTROL Twitter]** por aplicativo do Twitter.

O workflow **[!UICONTROL Twitter account Synchronization]** sincroniza as contas do Twitter no Adobe Campaign. Para obter mais informações, consulte [Sincronização de páginas do Facebook](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages).

## Sincronização de contas do Twitter {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>Para que o workflow recupere a lista de inscritos do Twitter, a caixa **[!UICONTROL Twitter account synchronization]** deve ser marcada na seção de edição do serviço vinculado à conta. Para obter mais informações, consulte [Delegação de acesso de gravação ao Adobe Campaign](#delegating-write-access-to-adobe-campaign).

O workflow **[!UICONTROL Twitter account synchronization]**, acessado pelo nó **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]**, permite sincronizar as contas do Twitter configuradas anteriormente com o Adobe Campaign. Por padrão, esse workflow é acionado todas as quintas-feiras às 7:30 am.

>[!NOTE]
>
>É possível iniciar o workflow a qualquer momento executando o processamento antecipado da tarefa. Também é possível editar o scheduler para alterar a frequência de acionamento do workflow. Para saber mais sobre o scheduler, consulte [esta seção](../../workflow/using/scheduler.md).

Agora é possível enviar tweets para suas contas do Twitter e mensagens diretas para seus seguidores. Para obter mais informações, consulte: [Publicação no Twitter](../../social/using/publishing-on-twitter.md).
