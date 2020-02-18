---
title: Criação de um aplicativo do Facebook
seo-title: Criação de um aplicativo do Facebook
description: Criação de um aplicativo do Facebook
seo-description: null
page-status-flag: never-activated
uuid: f02129b9-6f64-41ee-8b56-d85211a58f69
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: c1d880bb-256e-451c-8c52-198711907f8e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2e18121e4094bc4cb215e5471091810df56b3ef5

---


# Criação de um aplicativo do Facebook{#creating-a-facebook-application}

Graças aos aplicativos da Web, o Social Marketing permite exibir conteúdo personalizado em seus aplicativos do Facebook, facilitando a aquisição de perspectivas por meio dessa rede social. Para obter mais exemplos de aplicativos da Web do tipo Facebook, consulte [Exemplos de aplicativos](../../social/using/examples-of-facebook-apps.md)do Facebook.

>[!NOTE]
>
>Também é possível integrar o Adobe Campaign a um aplicativo do Facebook desenvolvido por um parceiro. Nesse caso, não há necessidade de usar o aplicativo da Web Adobe Campaign para adquirir perfis do Facebook. For more on this, refer to [Configuring external accounts](#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

Aplique as seguintes etapas de configuração:

1. Crie um ou mais aplicativos do Facebook. Para obter mais informações, consulte: [Criação de um aplicativo](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application)do Facebook.
1. Digite os links **[!UICONTROL terms of service]** e **[!UICONTROL Privacy policy]** a serem exibidos na tela de solicitação de permissão do Facebook. Para obter mais informações, consulte: [Inserir os links](#entering-the-terms-of-service-and-privacy-policy-links)dos Termos de serviço e da Política de privacidade.
1. Para cada aplicativo do Facebook, crie um **[!UICONTROL Facebook Connect]** tipo de conta externa. For more on this, refer to: [Configuring external accounts](#configuring-external-accounts).
1. Para cada aplicativo do Facebook, crie um aplicativo da Web tipo Facebook no Adobe Campaign. Para obter mais informações, consulte: [Criação de um aplicativo](#creating-a-facebook-type-web-application)da Web tipo Facebook.
1. Configure seus aplicativos do Facebook para que sejam exibidos como guias na sua página do Facebook. For more on this, refer to: [Configuring Facebook tabs](#configuring-facebook-tabs).

## Configuração de contas externas {#configuring-external-accounts}

For each Facebook application, you need to create a **[!UICONTROL Facebook Connect]** type external account.

Esta etapa requer acesso ao console do Adobe Campaign e a um navegador da Internet conectado à conta do Facebook que você usa para a administração da página:

* **Facebook**: selecione o aplicativo criado anteriormente ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)) e selecione a guia **[!UICONTROL Settings]** > **[!UICONTROL Basic]** .

   ![](assets/social_webapp_fb_008.png)

   >[!NOTE]
   >
   >Se a **[!UICONTROL Facebook Web Games]** seção não for exibida, clique no **[!UICONTROL Add Platform]** botão, na parte inferior da página, e selecione **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: vá para o **[!UICONTROL Administration > Platform > External accounts]** nó da árvore e clique em **[!UICONTROL New]**.

   ![](assets/social_webapp_fb_005.png)

1. Insira um rótulo e um nome interno e selecione o **[!UICONTROL Facebook Connect]** tipo.

   ![](assets/social_webapp_fb_006.png)

1. Selecione um modo de hospedagem para o aplicativo: **[!UICONTROL hosted by a partner]** ou **[!UICONTROL hosted by this instance]**.

   ![](assets/social_webapp_fb_012.png)

   **Aplicativo hospedado por um parceiro**

   É possível integrar o Adobe Campaign a um aplicativo do Facebook desenvolvido por um parceiro. Nesse caso, não há necessidade de usar os aplicativos da Web do Adobe Campaign para adquirir perfis do Facebook. Quando o usuário do Facebook instala o aplicativo, uma chave (token de acesso) é gerada. O parceiro encaminha esse token de acesso para o Adobe Campaign chamando um serviço da Web. O Adobe Campaign usa esse token para fazer logon no banco de dados do Facebook e coletar os dados compartilhados pelo usuário por meio do aplicativo.

   >[!NOTE]
   >
   >Os parâmetros do serviço Web estão detalhados no arquivo WSDL disponível aqui: **`https://<Instance name>/nl/jsp/schemawsdl.jsp?schema=nms:visitor`**

   Para integrar o aplicativo de terceiros ao Adobe Campaign, é necessário copiar o conteúdo dos campos do **[!UICONTROL App ID]** e do Facebook e colá-lo nos campos **[!UICONTROL App Secret]** e **[!UICONTROL Application ID]** **[!UICONTROL Application secret]** do console.

   ![](assets/social_facebook_external_account_013.png)

   **Aplicativo hospedado por esta instância**

   Se quiser hospedar o aplicativo nesta instância (se você não tiver um aplicativo de terceiros), use os aplicativos da Web do Adobe Campaign para adquirir perfis do Facebook. Para obter mais informações, consulte [Exemplos de aplicativos](../../social/using/examples-of-facebook-apps.md)do Facebook.

   No console do Adobe Campaign, copie o endereço contido no **[!UICONTROL Secure Canvas URL]** campo e cole-o no **[!UICONTROL Facebook Web games (https)]** campo do Facebook (na **[!UICONTROL Facebook Web Games]** seção).

   ![](assets/social_facebook_external_account_009.png)

   >[!IMPORTANT]
   >
   >Você não deve usar o URL inseguro em nenhuma circunstância.

   No Facebook, copie o conteúdo dos campos **[!UICONTROL App ID]** e **[!UICONTROL App Secret]** e cole-o nos campos **[!UICONTROL Application ID]** e **[!UICONTROL Application secret]** no console.

   ![](assets/social_facebook_external_account_008.png)

1. No Facebook, clique no **[!UICONTROL Save Changes]** botão na parte inferior da página.
1. No console do Adobe Campaign, clique no **[!UICONTROL Subscribe]** botão para ativar o Adobe Campaign para recuperar os dados em tempo real sempre que um fã fizer check-in por meio deste aplicativo. Para obter mais informações, consulte: [Exemplos de aplicativos](../../social/using/examples-of-facebook-apps.md)do Facebook.

   ![](assets/social_webapp_fb_013.png)

## Inserção dos links de Termos de serviço e Política de privacidade {#entering-the-terms-of-service-and-privacy-policy-links}

É altamente recomendável adicionar os links **[!UICONTROL Terms of service]** e **[!UICONTROL Privacy policy]** , que serão exibidos na tela de solicitação de permissão do Facebook.

![](assets/social_fb_terms_of_services_001.png)

Os estágios de configuração são os seguintes:

1. Digite o seguinte endereço: [https://developers.facebook.com/apps](https://developers.facebook.com/apps)e selecione o aplicativo do Facebook.
1. Selecione a **[!UICONTROL Settings > Basic]** guia e insira os campos **[!UICONTROL Privacy Policy URL]** e **[!UICONTROL Terms of Service URL]** .

   ![](assets/social_fb_terms_of_services.png)

## Criação de um aplicativo da Web tipo Facebook {#creating-a-facebook-type-web-application}

O aplicativo Adobe Campaign Facebook permite exibir conteúdo personalizado em seu aplicativo do Facebook. Para cada aplicativo do Facebook, é necessário criar um aplicativo da Web no Adobe Campaign. Para criar um aplicativo da Web do Facebook, proceda da seguinte maneira:

1. Vá para o **[!UICONTROL Social networks]** universo, clique no **[!UICONTROL Applications]** link e depois no **[!UICONTROL Create]** botão.

   ![](assets/social_webapp_001.png)

1. Selecione um modelo de aplicativo da Web do Facebook na lista e insira o rótulo.

   ![](assets/social_webapp_002.png)

   >[!NOTE]
   >
   >Há quatro modelos de aplicativos da Web do Facebook oferecidos por padrão:
   >
   >* **[!UICONTROL New Facebook application]**: selecione este modelo se quiser começar de um aplicativo em branco.
   >* **[!UICONTROL Pre-entered form]**: Aplicativo do Facebook com um formulário e um botão de &quot;logon do Facebook&quot; que permite que os usuários preencham automaticamente os campos do formulário usando os dados de seu perfil. Isso permite que os usuários preencham o formulário mais rapidamente e que as marcas obtenham informações de melhor qualidade.
   >* **[!UICONTROL "Canvas page" competition]**: Aplicativo do Facebook que é exibido na tela para obter uma melhor experiência visual para os usuários.
   >* **[!UICONTROL "Page Tab" competition]**: Aplicativo do Facebook totalmente integrado nas guias da página da marca.


1. No **[!UICONTROL Application]** campo, informe a conta externa vinculada ao aplicativo do Facebook. For more on this, refer to: [Configuring external accounts](#configuring-external-accounts).

   ![](assets/social_webapp_005.png)

1. Selecione a **[!UICONTROL Edit]** guia e edite o aplicativo da Web. Para obter mais informações, consulte: [Exemplos de aplicativos](../../social/using/examples-of-facebook-apps.md)do Facebook.

   ![](assets/social_webapp_003.png)

1. Quando o aplicativo da Web estiver concluído, selecione a **[!UICONTROL Dashboard]** guia e clique **[!UICONTROL Publish]** para publicar online.

   ![](assets/social_webapp_004.png)

## Configuração de guias do Facebook {#configuring-facebook-tabs}

Você pode configurar seus aplicativos do Facebook para serem exibidos como guias na sua página do Facebook. Para fazer isso, siga as etapas abaixo:

1. Selecione o aplicativo do Facebook ([https://developers.facebook.com/apps](https://developers.facebook.com/apps)) e selecione a **[!UICONTROL Settings > Basic]** guia.

   ![](assets/social_webapp_fb_008.png)

1. Na parte inferior da página, clique no **[!UICONTROL Add Platform]** botão e selecione **[!UICONTROL Page Tab]**.

   ![](assets/social_webapp_fb_008bis.png)

1. No **[!UICONTROL Page Tab Name]** campo da seção **[!UICONTROL Page Tab]** , insira o rótulo como deseja que ele apareça na página do Facebook.

   ![](assets/social_webapp_fb_001.png)

1. No **[!UICONTROL Secure Page Tab URL]** campo, insira o URL público do aplicativo da Web, que pode ser acessado por meio da **[!UICONTROL Dashboard]** guia do aplicativo da Web. Para obter mais informações sobre como criar aplicativos da Web do tipo Facebook, consulte [Criar um aplicativo](#creating-a-facebook-type-web-application)da Web do tipo Facebook.

   ![](assets/social_webapp_fb_002.png)

1. Na parte superior **[!UICONTROL Dashboard]** do aplicativo da Web, clique no **[!UICONTROL Add a page tab]** link.

   ![](assets/social_webapp_fb_0010.png)

1. Selecione a página do Facebook à qual deseja adicionar a guia e clique em **[!UICONTROL Add Page Tab]**.

   ![](assets/social_webapp_fb_0011.png)

