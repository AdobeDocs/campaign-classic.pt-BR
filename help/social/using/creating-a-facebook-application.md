---
solution: Campaign Classic
product: campaign
title: Criação de um aplicativo do Facebook
description: Criação de um aplicativo do Facebook
audience: social
content-type: reference
topic-tags: configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 100%

---


# Criação de um aplicativo do Facebook{#creating-a-facebook-application}

Graças aos aplicativos Web, o Social Marketing permite exibir um conteúdo personalizado nos seus aplicativos do Facebook, facilitando a aquisição de prospectos por meio dessa rede social. Para obter mais exemplos de aplicativos Web do tipo Facebook, consulte [Exemplos de aplicativos do Facebook](../../social/using/examples-of-facebook-apps.md).

>[!NOTE]
>
>Também é possível integrar o Adobe Campaign a um aplicativo do Facebook desenvolvido por um parceiro. Nesse caso, não há necessidade de usar o aplicativo web do Adobe Campaign para adquirir os perfis do Facebook. Para obter mais informações, consulte [Configuração de contas externas](#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

Aplique as seguintes etapas de configuração:

1. Crie um ou mais aplicativos do Facebook. Para obter mais informações, consulte: [Criação de um aplicativo do Facebook](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application).
1. Digite os links **[!UICONTROL terms of service]** e **[!UICONTROL Privacy policy]** que serão exibidos na tela de solicitação de permissão do Facebook. Para obter mais informações, consulte: [Inserir os links dos Termos de serviço e da Política de privacidade](#entering-the-terms-of-service-and-privacy-policy-links).
1. Para cada aplicativo do Facebook, crie uma conta externa do tipo **[!UICONTROL Facebook Connect]**. Para obter mais informações, consulte: [Configuração de contas externas](#configuring-external-accounts).
1. Para cada aplicativo do Facebook, crie um aplicativo Web do tipo Facebook no Adobe Campaign. Para obter mais informações, consulte: [Criação de um aplicativo web tipo Facebook](#creating-a-facebook-type-web-application).
1. Configure os aplicativos do Facebook para que sejam exibidos como guias na sua página do Facebook. Para obter mais informações, consulte: [Configuração das guias do Facebook](#configuring-facebook-tabs).

## Configuração de contas externas {#configuring-external-accounts}

Para cada aplicativo do Facebook, é necessário criar uma conta externa do tipo **[!UICONTROL Facebook Connect]**.

Esta etapa requer o acesso ao console do Adobe Campaign e a um navegador da Internet conectado à conta do Facebook usada na administração da página:

* **Facebook**: selecione o aplicativo criado anteriormente ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)) e selecione a guia **[!UICONTROL Settings]** > **[!UICONTROL Basic]**.

   ![](assets/social_webapp_fb_008.png)

   >[!NOTE]
   >
   >Se a seção **[!UICONTROL Facebook Web Games]** não for exibida, clique no botão **[!UICONTROL Add Platform]**, na parte inferior da página, e selecione **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: acesse o nó **[!UICONTROL Administration > Platform > External accounts]** da árvore e clique em **[!UICONTROL New]**.

   ![](assets/social_webapp_fb_005.png)

1. Digite um rótulo, um nome interno e selecione o tipo **[!UICONTROL Facebook Connect]** .

   ![](assets/social_webapp_fb_006.png)

1. Selecione um modo de hospedagem do aplicativo: **[!UICONTROL hosted by a partner]** ou **[!UICONTROL hosted by this instance]**.

   ![](assets/social_webapp_fb_012.png)

   **Aplicativo hospedado por um parceiro**

   É possível integrar o Adobe Campaign com um aplicativo do Facebook desenvolvido por um parceiro. Nesse caso, não há necessidade de usar os aplicativos Web do Adobe Campaign para adquirir os perfis do Facebook. Quando o usuário do Facebook instala o aplicativo, uma chave (token de acesso) é gerada. O parceiro encaminha esse token de acesso para o Adobe Campaign pelo chamado de um serviço da Web. O Adobe Campaign usa esse token para fazer logon no banco de dados do Facebook e coletar os dados compartilhados pelo usuário por meio do aplicativo.

   >[!NOTE]
   >
   >Os parâmetros do serviço da Web estão detalhados no arquivo WSDL disponível aqui: **`https://<Instance name>/nl/jsp/schemawsdl.jsp?schema=nms:visitor`**

   Para integrar o aplicativo de terceiros ao Adobe Campaign, é necessário copiar o conteúdo dos campos **[!UICONTROL App ID]** e **[!UICONTROL App Secret]** do Facebook e colá-los nos campos **[!UICONTROL Application ID]** e **[!UICONTROL Application secret]** do console.

   ![](assets/social_facebook_external_account_013.png)

   **Aplicativo hospedado por esta instância**

   Para hospedar o aplicativo nesta instância (se não houver um aplicativo de terceiros), é possível usar os aplicativos Web do Adobe Campaign para adquirir perfis do Facebook. Para obter mais informações, consulte [Exemplos de aplicativos do Facebook](../../social/using/examples-of-facebook-apps.md).

   No console do Adobe Campaign, copie o endereço contido no campo **[!UICONTROL Secure Canvas URL]** e o cole no campo **[!UICONTROL Facebook Web games (https)]** no Facebook (na seção **[!UICONTROL Facebook Web Games]**).

   ![](assets/social_facebook_external_account_009.png)

   >[!IMPORTANT]
   >
   >Evite o uso do URL inseguro nas circunstância.

   No Facebook, copie o conteúdo dos campos **[!UICONTROL App ID]** e o **[!UICONTROL App Secret]** e cole-o nos campos **[!UICONTROL Application ID]** e **[!UICONTROL Application secret]** do console.

   ![](assets/social_facebook_external_account_008.png)

1. No Facebook, clique no botão **[!UICONTROL Save Changes]** na parte inferior da página.
1. No console do Adobe Campaign, clique no botão **[!UICONTROL Subscribe]** para habilitar o Adobe Campaign e recuperar os dados em tempo real sempre que um fã fizer o check-in por meio desse aplicativo. Para obter mais informações, consulte: [Exemplos de aplicativos do Facebook](../../social/using/examples-of-facebook-apps.md).

   ![](assets/social_webapp_fb_013.png)

## Inserção dos links de Termos de serviço e Política de privacidade{#entering-the-terms-of-service-and-privacy-policy-links}

É altamente recomendável adicionar os links **[!UICONTROL Terms of service]** e **[!UICONTROL Privacy policy]** que devem ser exibidos na tela de solicitação de permissão do Facebook.

![](assets/social_fb_terms_of_services_001.png)

As etapas de configuração são as seguintes:

1. Digite o seguinte endereço: [https://developers.facebook.com/apps](https://developers.facebook.com/apps) e depois selecione o aplicativo do Facebook.
1. Selecione a guia **[!UICONTROL Settings > Basic]** e insira os campos **[!UICONTROL Privacy Policy URL]** e **[!UICONTROL Terms of Service URL]**.

   ![](assets/social_fb_terms_of_services.png)

## Criação de um aplicativo Web do tipo Facebook{#creating-a-facebook-type-web-application}

O aplicativo do Facebook do Adobe Campaign permite exibir o conteúdo personalizado no seu aplicativo do Facebook. Para cada aplicativo do Facebook, é necessário criar um aplicativo Web no Adobe Campaign. Para criar um aplicativo Web do Facebook, proceda da seguinte maneira:

1. Vá para o universo **[!UICONTROL Social networks]**, clique no link **[!UICONTROL Applications]** e no botão **[!UICONTROL Create]**.

   ![](assets/social_webapp_001.png)

1. Selecione um template de aplicativo Web do Facebook na lista e insira o rótulo.

   ![](assets/social_webapp_002.png)

   >[!NOTE]
   >
   >Por padrão, há quatro templates de aplicativos Web do Facebook oferecidos:
   >
   >* **[!UICONTROL New Facebook application]**: selecione este template para começar a partir de um aplicativo em branco.
   >* **[!UICONTROL Pre-entered form]**: aplicativo do Facebook com um formulário e um botão &quot;Facebook login&quot; que permite que os usuários preencham automaticamente os campos usando os dados do perfil. Isso permite que os usuários preencham o formulário mais rapidamente e que as marcas obtenham informações de melhor qualidade.
   >* **[!UICONTROL "Canvas page" competition]**: aplicativo do Facebook que é exibido na tela para obter uma experiência visual melhor para os usuários.
   >* **[!UICONTROL "Page Tab" competition]**: aplicativo do Facebook totalmente integrado nas guias da página da marca.


1. No campo **[!UICONTROL Application]**, informe a conta externa vinculada ao aplicativo do Facebook. Para obter mais informações, consulte: [Configuração de contas externas](#configuring-external-accounts).

   ![](assets/social_webapp_005.png)

1. Selecione a guia **[!UICONTROL Edit]** e edite o aplicativo Web. Para obter mais informações, consulte: [Exemplos de aplicativos do Facebook](../../social/using/examples-of-facebook-apps.md).

   ![](assets/social_webapp_003.png)

1. Quando o aplicativo Web está concluído, selecione a guia **[!UICONTROL Dashboard]** e, em seguida, clique em **[!UICONTROL Publish]** para publicar online.

   ![](assets/social_webapp_004.png)

## Configuração de guias do Facebook{#configuring-facebook-tabs}

É possível configurar os aplicativos do Facebook para serem exibidos como guias da sua página do Facebook. Para fazer isso, siga as etapas abaixo:

1. Selecione o aplicativo do Facebook ([https://developers.facebook.com/apps](https://developers.facebook.com/apps)) e selecione a guia **[!UICONTROL Settings > Basic]**.

   ![](assets/social_webapp_fb_008.png)

1. Na parte inferior da página, clique no botão **[!UICONTROL Add Platform]** e selecione **[!UICONTROL Page Tab]**.

   ![](assets/social_webapp_fb_008bis.png)

1. No campo **[!UICONTROL Page Tab Name]** da seção **[!UICONTROL Page Tab]**, digite o rótulo como deseja que apareça na página do Facebook.

   ![](assets/social_webapp_fb_001.png)

1. No campo **[!UICONTROL Secure Page Tab URL]**, digite o URL público, que pode ser acessado por meio da guia **[!UICONTROL Dashboard]** do aplicativo Web. Para obter mais informações sobre como criar aplicativos Web do tipo Facebook, consulte [Criação de um aplicativo Web do tipo Facebook](#creating-a-facebook-type-web-application).

   ![](assets/social_webapp_fb_002.png)

1. No **[!UICONTROL Dashboard]** do aplicativo Web, clique no link **[!UICONTROL Add a page tab]**.

   ![](assets/social_webapp_fb_0010.png)

1. Selecione a página do Facebook que deve ser adicionada a guia e clique em **[!UICONTROL Add Page Tab]**.

   ![](assets/social_webapp_fb_0011.png)

