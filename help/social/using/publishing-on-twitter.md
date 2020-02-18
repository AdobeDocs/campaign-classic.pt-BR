---
title: Publicação no Twitter
seo-title: Publicação no Twitter
description: Publicação no Twitter
seo-description: null
page-status-flag: never-activated
uuid: 405bce50-a63c-4bd3-8f03-c71809bb1cfd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
discoiquuid: 2dc278ce-477c-493d-8abb-8bbdf2e988a5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2e18121e4094bc4cb215e5471091810df56b3ef5

---


# Publicação no Twitter{#publishing-on-twitter}

## Publicação em suas contas do Twitter {#publishing-on-your-twitter-accounts}

Quando a configuração for concluída, o Social Marketing permitirá que você envie tweets para suas contas do Twitter.

### Limitações {#limitations}

As limitações a seguir são restrições inerentes ao Twitter.

* A mensagem não pode exceder 140 caracteres.
* O formato HTML não é compatível.

### Criação de delivery {#creating-the-delivery}

Crie uma nova entrega com base no modelo de **[!UICONTROL Tweet (twitter)]** entrega.

![](assets/social_twitter_delivery_001.png)

### Seleção do target principal {#selecting-the-main-target}

Selecione as contas para as quais deseja enviar tweets.

1. Clique no **[!UICONTROL To]** link.

   ![](assets/social_twitter_delivery_002.png)

1. Clique no botão **[!UICONTROL Add]**.

   ![](assets/social_twitter_delivery_006.png)

1. Select **[!UICONTROL A Twitter account]**.

   ![](assets/social_twitter_delivery_007.png)

1. No **[!UICONTROL Folder]** campo, selecione a pasta de serviço que contém a conta do Twitter. Em seguida, selecione a conta do Twitter para a qual você deseja enviar seu tweet.

   ![](assets/social_twitter_delivery_011.png)

### Selecionar o destino da prova {#selecting-the-target-of-the-proof}

A **[!UICONTROL Target of the proofs]** guia permite que você defina a conta do Twitter a ser usada para testes de entregas antes da entrega final. Portanto, recomendamos que você crie uma conta privada do Twitter dedicada ao envio de provas. Para obter mais informações sobre como criar uma conta privada do Twitter, consulte [Criar uma conta de teste no Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). As etapas para selecionar a meta de prova são as mesmas que para selecionar a meta principal. Consulte [Criação de uma conta de teste no Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter).

![](assets/social_twitter_delivery_004.png)

>[!NOTE]
>
>Se você estiver usando a mesma conta de teste do Twitter para todas as entregas, poderá salvar a meta de prova no modelo de **[!UICONTROL Tweet]** entrega, acessada pelo **[!UICONTROL Resources > Templates > Delivery templates]** nó. O destino da prova será inserido por padrão para cada nova entrega.

### Definição do conteúdo da mensagem {#defining-the-message-content}

Digite o conteúdo do tweet na **[!UICONTROL Content]** guia.

![](assets/social_twitter_delivery_005.png)

### Exibição da visualização {#viewing-the-preview}

A **[!UICONTROL Preview]** guia permite exibir uma renderização do tweet.

1.  Clique na **[!UICONTROL Preview]** guia.
1. Clique no menu **[!UICONTROL Test personalization]** suspenso e selecione **[!UICONTROL Service]**.
1. No **[!UICONTROL Folder]** campo, selecione a pasta de serviço que contém sua conta do Twitter.
1. Escolha a conta do Twitter com a qual deseja testar a visualização.

![](assets/social_twitter_delivery_008.png)

>[!NOTE]
>
>A visualização pode diferir ligeiramente do tweet final. Recomendamos enviar uma prova antes da entrega final para exibir uma renderização exata do tweet. Consulte [Envio da prova](#sending-the-proof).

### Configuração do rastreamento {#configuring-tracking}

O rastreamento pode ser visualizado nos relatórios de entrega e na **[!UICONTROL Edit > Tracking]** guia da entrega e do serviço.

A configuração de rastreamento é a mesma de uma entrega de email. Para obter mais informações, consulte [esta seção](../../delivery/using/monitoring-a-delivery.md).

>[!NOTE]
>
>No modelo de **[!UICONTROL Tweet]** entrega, o rastreamento é ativado por padrão.

>[!IMPORTANT]
>
>Não podemos diferenciar entre robôs que analisam tweets e usuários que estão realmente clicando.

### Envio da prova {#sending-the-proof}

Recomendamos enviar uma prova de sua publicação antes da entrega final para obter uma renderização exata da publicação em uma página de teste privada do Twitter. Para obter mais informações sobre como criar uma conta privada do Twitter, consulte [Criar uma conta de teste no Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). As etapas para selecionar o destino da prova são detalhadas em [Selecionar o destino da prova](#selecting-the-target-of-the-proof).

A entrega da prova é idêntica às entregas por email. Consulte [esta seção](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Envio da mensagem {#sending-the-message}

1. Depois que o conteúdo for aprovado, clique no **[!UICONTROL Send]** botão.
1. Selecione **[!UICONTROL Deliver as soon as possible]** e clique no **[!UICONTROL Analyze]** botão.

   >[!NOTE]
   >
   >A **[!UICONTROL Postpone the delivery]** opção permite adiar a entrega para uma data posterior.

   ![](assets/social_twitter_delivery_012.png)

1. Quando a análise estiver concluída, verifique o resultado.
1. Clique em **[!UICONTROL Confirm delivery]** e em **[!UICONTROL Yes]**.

![](assets/social_facebook_delivery_016.png)

## Envio de mensagens diretas aos assinantes {#sending-direct-messages-to-subscribers}

### Princípio operacional {#operating-principle}

O **[!UICONTROL Synchronize Twitter accounts]** fluxo de trabalho (consulte [Sincronizar contas](../../social/using/configuring-publishing-on-twitter.md#synchronizing-twitter-accounts)do Twitter) recupera a lista de assinantes do Twitter para que você possa enviá-los mensagens diretas. Os seguidores recuperados são armazenados em uma tabela específica: a tabela de visitantes. Para exibir a lista de seguidores do Twitter, vá para o **[!UICONTROL Profiles and Targets > Visitors]** nó.

![](assets/social_twitter_visitors_001.png)

>[!IMPORTANT]
>
>Para que o fluxo de trabalho recupere a lista de seguidores do Twitter, a **[!UICONTROL Synchronize Twitter accounts]** caixa deve ser marcada na tela Editar do serviço vinculado à conta. Para obter mais informações, consulte: [Delegando acesso de gravação ao Adobe Campaign](../../social/using/configuring-publishing-on-twitter.md#delegating-write-access-to-adobe-campaign).

Para cada seguidor, o Adobe Campaign recupera as seguintes informações:

* **[!UICONTROL Origin]**: nome da rede social (**Twitter** neste caso)
* **[!UICONTROL External ID]**: identificador do usuário
* **[!UICONTROL User name]**: nome da conta do usuário
* **[!UICONTROL Full name]**: nome do usuário
* **[!UICONTROL Language]**: idioma do usuário
* **[!UICONTROL Number of friends]**: número de seguidores
* **[!UICONTROL Time zone]**: fuso horário do usuário
* **[!UICONTROL Verified]**: este campo indica se o usuário tem uma conta do Twitter verificada

### Limitações {#limitations-1}

As limitações a seguir são restrições inerentes ao Twitter.

* A mensagem não pode exceder 140 caracteres.
* HTML não é suportado.
* Não é possível enviar mais de 250 mensagens diretas por dia. Para evitar exceder esse limite, é possível entregar várias ondas. As entregas em ondas são configuradas como entregas por email. Para obter mais informações, consulte [esta seção](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

### Criação de delivery {#creating-the-delivery-}

Crie uma nova entrega com base no modelo de **[!UICONTROL Tweet (Direct Message)]** entrega.

![](assets/social_twitter_delivery_010.png)

### Seleção do target principal {#selecting-the-main-target-1}

Selecione os seguidores para os quais deseja enviar sua mensagem direta.

1. Clique no **[!UICONTROL To]** link.

   ![](assets/social_twitter_delivery_016.png)

1. Clique no botão **[!UICONTROL Add]**.

   ![](assets/social_twitter_delivery_006.png)

1. Selecione um tipo de direcionamento.

   ![](assets/social_twitter_delivery_017.png)

   * Selecione **[!UICONTROL Twitter subscribers]** para enviar uma mensagem direta a todos os seguidores da conta.

      >[!IMPORTANT]
      >
      >Não é possível enviar mais de 250 mensagens por dia. Se sua conta do Twitter tem mais de 250 seguidores, recomendamos enviar em ondas. Isso envolve o mesmo processo que entregas por email. Consulte [esta seção](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

   * Selecione **[!UICONTROL Filter conditions]** para definir uma consulta e exibir seu resultado. Essa opção é a mesma para entregas por email. Consulte [esta seção](../../platform/using/defining-filter-conditions.md) para obter mais informações.

      ![](assets/social_twitter_delivery_018.png)

### Selecionar o destino da prova {#selecting-the-target-of-the-proof-1}

A **[!UICONTROL Target of the proofs]** guia permite selecionar o seguidor que receberá a prova da sua mensagem direta. O processo de seleção é o mesmo do destino principal. Consulte [Seleção do destino](#selecting-the-main-target)principal.

![](assets/social_twitter_delivery_020.png)

>[!NOTE]
>
>Se desejar enviar todas as suas provas de mensagem direta para o mesmo seguidor do Twitter, você pode salvar o destino da prova no modelo de **[!UICONTROL Tweet (Direct Message)]** entrega, acessado pelo **[!UICONTROL Resources > Templates > Delivery templates]** nó. O destino da prova será inserido por padrão para cada nova entrega.

### Definição do conteúdo da mensagem {#defining-message-content-}

Digite o conteúdo do tweet na **[!UICONTROL Content]** guia.

![](assets/social_twitter_delivery_015.png)

Campos de personalização podem ser usados da mesma forma que para entregas por email, por exemplo, para adicionar o nome do seguidor no corpo da mensagem. A personalização do conteúdo é detalhada [nesta seção](../../delivery/using/about-personalization.md).

![](assets/social_twitter_delivery_021.png)

As etapas a seguir são as mesmas para enviar um tweet a uma conta do Twitter. Consulte [Publicação em suas contas](#publishing-on-your-twitter-accounts)do Twitter.
