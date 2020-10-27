---
title: Configuração do aplicativo iOS para dispositivos móveis no Adobe Campaign
description: Saiba como configurar seu aplicativo móvel para iOS
page-status-flag: never-activated
uuid: aff1a4a0-34e7-4ce0-9eb3-30a8de1380f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 7b5a1ad6-da5a-4cbd-be51-984c07c8d0b3
translation-type: tm+mt
source-git-commit: 16985c1ddcd380cfc1ca4960b35bb5e78628f464
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 66%

---


# Etapas de configuração para iOS {#configuring-the-mobile-application-in-adobe-campaign-ios}

Depois que o pacote for instalado, você poderá definir as configurações do aplicativo iOS no Adobe Campaign Classic.

>[!NOTE]
>
>Para saber como configurar seu aplicativo para Android e como criar um delivery para Android, consulte esta [seção](../../delivery/using/configuring-the-mobile-application-android.md).

## Configuring iOS external account {#configuring-external-account-ios}

Para iOS, o conector HTTP/2 do iOS envia notificações para os APNs HTTP/2.

Para configurar esse conector, siga estas etapas:

1. Vá para **[!UICONTROL Administration > Platform > External accounts]**.
1. Selecione a conta externa **[!UICONTROL iOS routing]**.
1. Na **[!UICONTROL Connector]** guia, preencha o **[!UICONTROL Access URL of the connector]** campo com o seguinte URL: ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   >[!NOTE]
   >
   > A partir da versão 20.3 da Campanha, o conector binário herdado do iOS será descontinuado. Se estiver usando esse conector, é necessário adaptar sua implementação de acordo. [Saiba mais](https://helpx.adobe.com/campaign/kb/migrate-to-http2.html)

   ![](assets/nmac_connectors.png)

1. Clique em **[!UICONTROL Save]**.

O conector iOS está configurado. Você pode começar a criar seu serviço.

## Configuração do serviço iOS {#configuring-ios-service}

>[!CAUTION]
>
>O aplicativo deve ter sido configurado para ações Push ANTES de qualquer integração ao Adobe Campaign SDK.
>
>Se esse não for o caso, consulte [esta página](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/).

1. Acesse o nó **[!UICONTROL Profiles and Targets > Services and subscriptions]** e clique em **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Defina um **[!UICONTROL Label]** e um **[!UICONTROL Internal name]**.
1. Acesse o campo **[!UICONTROL Type]** e selecione **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >O target mapping **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** padrão é vinculado à tabela de destinatários. Para utilizar um mapeamento de alvo diferente, é necessário criar um novo e inseri-lo no campo **[!UICONTROL Target mapping]** do serviço. Para obter mais informações sobre como criar o target mapping, consulte o [Guia de configuração](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Em seguida, clique no botão **[!UICONTROL Add]** para selecionar o tipo de aplicativo.

   ![](assets/nmac_service_2.png)

1. Crie seus aplicativos de desenvolvimento e produção do iOS. Para obter mais informações, consulte esta [seção](../../delivery/using/configuring-the-mobile-application.md#creating-ios-app).

## Criação de aplicativos iOS para dispositivos móveis {#creating-ios-app}

Depois de criar seu serviço, agora é necessário criar seu aplicativo iOS:

1. Em seu serviço recém-criado, clique no **[!UICONTROL Add]** botão para selecionar o tipo de aplicativo.

   ![](assets/nmac_service_2.png)

1. A janela a seguir é exibida. Selecione **[!UICONTROL Create an iOS application]** e comece inserindo o **[!UICONTROL Label]**.

   ![](assets/nmac_ios_2.png)

1. Como opção, você pode enriquecer um conteúdo de mensagem de push com alguns **[!UICONTROL Application variables]** se necessário. Eles são totalmente personalizáveis e uma parte da carga da mensagem é enviada para o dispositivo móvel.
No exemplo a seguir, adicionamos **mediaURl** e **mediaExt** para criar notificações por push avançadas e, em seguida, fornecemos ao aplicativo  a imagem que será exibida na notificação.

   ![](assets/nmac_ios_3.png)

1. A guia **[!UICONTROL Subscription parameters]** permite definir o mapeamento com uma extensão do schema **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**.

   >[!NOTE]
   >
   >Certifique-se de não usar o mesmo certificado para a versão de desenvolvimento (sandbox) e a versão de produção do aplicativo.

1. A guia **[!UICONTROL Sounds]** permite que você especifique um som para reproduzir. Clique em **[!UICONTROL Add]** e preencha o campo **[!UICONTROL Internal name]** que deve conter o nome do arquivo incorporado no aplicativo ou o nome do som do sistema.

1. Clique em **[!UICONTROL Next]** para configurar o aplicativo de desenvolvimento.

1. Verifique se a mesma **[!UICONTROL Integration key]** está definida no Adobe Campaign e no código do aplicativo por meio do SDK. Para obter mais informações, consulte: [Integração do SDK do Campaign ao aplicativo móvel](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md). Essa chave de integração, específica para cada aplicativo, permite vincular o aplicativo móvel à plataforma do Adobe Campaign.

   >[!NOTE]
   >
   > O **[!UICONTROL Integration key]** é totalmente personalizável com o valor da string, mas precisa ser exatamente o mesmo especificado no SDK.

1. Select one of the out-of-the-box icons from the **[!UICONTROL Application icon]** field to personalize mobile application in your service.

1. Selecione **[!UICONTROL Authentication mode]**. Observe que você sempre pode alterar o modo de autenticação posteriormente na **[!UICONTROL Certificate]** guia do aplicativo móvel.
   * **[!UICONTROL Certificate-based authentication]**: Clique em **[!UICONTROL Enter the certificate...]** e selecione sua chave p12 e digite a senha fornecida pelo desenvolvedor do aplicativo móvel.
   * **[!UICONTROL Token-based authentication]**: Preencha as configurações de conexão **[!UICONTROL Key ID]** e **[!UICONTROL Team ID]** selecione seu certificado p8 clicando em **[!UICONTROL Bundle ID]** **[!UICONTROL Enter the private key]**. For more on **[!UICONTROL Token-based authentication]**, refer to [Apple documentation](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apnsToken-based).

   >[!NOTE]
   >
   > O Adobe recomenda usar **[!UICONTROL Token-based authentication]** para a configuração do iOS, pois esse modo de autenticação é mais seguro e não está vinculado à expiração do certificado.

   ![](assets/nmac_ios_4.png)

1. Você pode clicar em **[!UICONTROL Test the connection]** para ter certeza de que ele é bem-sucedido.

1. Clique em **[!UICONTROL Next]** para configurar o aplicativo de produção e siga as mesmas etapas descritas acima.

   ![](assets/nmac_ios_5.png)

1. Clique em **[!UICONTROL Finish]**.

Seu aplicativo iOS está pronto para ser usado no Campaign Classic.

## Creating an iOS rich notification {#creating-ios-delivery}

Com o iOS 10 ou superior, é possível gerar notificações ricas. O Adobe Campaign pode enviar notificações usando variáveis que permitirão ao dispositivo exibir uma notificação rica.

Em seguida, é necessário criar um novo delivery e vinculá-lo ao aplicativo para dispositivos móveis criado.

1. Vá até **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Clique em **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Selecione **[!UICONTROL Deliver on iOS (ios)]** na lista suspensa **[!UICONTROL Delivery template]**. Adicione um **[!UICONTROL Label]** ao delivery.

1. Clique em **[!UICONTROL To]** para definir a população como target. Por padrão, o target mapping **[!UICONTROL Subscriber application]** é aplicado. Clique em **[!UICONTROL Add]** para selecionar o serviço criado anteriormente.

   ![](assets/nmac_ios_9.png)

1. Na janela **[!UICONTROL Target type]**, selecione **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** e clique em **[!UICONTROL Next]**.

1. Na lista suspensa **[!UICONTROL Service]**, selecione o serviço criado anteriormente e, em seguida, o aplicativo que deseja direcionar e clique em **[!UICONTROL Finish]**.
Os **[!UICONTROL Application variables]** são adicionados automaticamente, dependendo do que foi adicionado durante as etapas de configuração.

   ![](assets/nmac_ios_6.png)

1. Edite a notificação avançada.

   ![](assets/nmac_ios_7.png)

1. Marque a caixa **[!UICONTROL Mutable content]** na janela de notificação de edição para permitir que o aplicativo para dispositivos móveis baixe o conteúdo de mídia.

1. Clique em **[!UICONTROL Save]** e envie o delivery.

A imagem e a página da Web devem ser exibidas na notificação por push quando recebida nos dispositivos iOS móveis dos inscritos.

![](assets/nmac_ios_8.png)
