---
title: Configuração do aplicativo móvel no Adobe Campaign
seo-title: Configuração do aplicativo móvel no Adobe Campaign
description: Configuração do aplicativo móvel no Adobe Campaign
seo-description: null
page-status-flag: never-activated
uuid: aff1a4a0-34e7-4ce0-9eb3-30a8de1380f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 7b5a1ad6-da5a-4cbd-be51-984c07c8d0b3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a358da7c499b5ee780563b4aef0eb2f4463186cf

---


# Configuração do aplicativo móvel no Adobe Campaign {#configuring-the-mobile-application-in-adobe-campaign}

Encontre abaixo a amostra da configuração baseada em uma empresa que vende online pacotes de viagens. Seu aplicativo móvel (Neotrips) está disponível para seus clientes em duas versões: Neotrips para Android e Neotrips para iOS. Para configurar o aplicativo móvel no Adobe Campaign, é necessário:

* Create a **[!UICONTROL Mobile application]** type information service for the Neotrips mobile application.
* Adicione as versões iOS e Android do aplicativo a este serviço.
* Crie uma entrega para iOS e Android.

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Go to the **[!UICONTROL Subscriptions]** tab of the service to view the list of subscribers to the service, i.e. all people who have installed the application on their mobile and agreed to receive notifications.

## Configuração do aplicativo móvel com iOS {#configuring-the-mobile-application-ios}

>[!CAUTION]
>
>O aplicativo deve ter sido configurado para ações Push ANTES de qualquer integração ao Adobe Campaign SDK.
>
>If this is not the case, please refer to [this page](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/).

### Etapa 1: Instalação do pacote {#installing-package-ios}

1. Acesse o assistente de importação de pacote **[!UICONTROL Tools > Advanced > Package import...]** no console do cliente Adobe Campaign.

   ![](assets/package_ios.png)

1. Select **[!UICONTROL Install a standard package]**.

1. Na lista exibida, marque **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Clique em **[!UICONTROL Next]** e, em seguida, **[!UICONTROL Start]** para iniciar a instalação do pacote.

   Depois que os pacotes são instalados, a barra de progresso mostra **100%** e você pode ver a seguinte mensagem nos registros de instalação: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** a janela de instalação.

### Etapa 2: Configuração da conta externa do iOS {#configuring-external-account-ios}

Para iOS, dois conectores estão disponíveis:

* O conector binário do iOS envia notificações no servidor binário APNS herdado.
* O conector HTTP/2 do iOS envia notificações para o HTTP/2 APNS.

Para escolher qual conector deseja usar, siga estas etapas:

1. Vá para **[!UICONTROL Administration > Platform > External accounts]**.
1. Selecione a conta **[!UICONTROL iOS routing]** externa.
1. Na **[!UICONTROL Connector]** guia, preencha o **[!UICONTROL Access URL of the connector]** campo:

   Para iOS HTTP2: http://localhost:8080/nms/jsp/iosHTTP2.jsp

   ![](assets/nmac_connectors.png)

   >[!NOTE]
   >
   > Você também pode configurá-lo como segue https://localhost:8080/nms/jsp/ios.jsp, mas recomendamos que você use a versão 2 do conector.

1. Clique em **[!UICONTROL Save]**.

Seu conector iOS agora está configurado. Você pode começar a criar seu serviço.

### Etapa 3: Configuração do serviço iOS {#configuring-ios-service}

1. Vá para o **[!UICONTROL Profiles and Targets > Services and subscriptions]** nó e clique em **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Defina um **[!UICONTROL Label]** e um **[!UICONTROL Internal name]**.
1. Vá para o **[!UICONTROL Type]** campo e selecione **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >The default **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** target mapping is linked to the recipients table. If you want to use a different target mapping, you need to create a new target mapping and enter it in the **[!UICONTROL Target mapping]** field of the service. Para obter mais informações sobre como criar o target mapping, consulte o [Guia de configuração](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Em seguida, clique no **[!UICONTROL Add]** botão para selecionar o tipo de aplicativo.

   ![](assets/nmac_service_2.png)

1. A janela a seguir é exibida. Selecione **[!UICONTROL Create an iOS application]** e comece inserindo o **[!UICONTROL Label]**.

   ![](assets/nmac_ios_2.png)

1. Como opção, você pode enriquecer um conteúdo de mensagem de push com alguns **[!UICONTROL Application variables]** se necessário. Eles são totalmente personalizáveis e uma parte da carga da mensagem enviada para o dispositivo móvel.
No exemplo a seguir, adicionamos **mediaURl** e **mediaExt** para criar notificações por push avançadas e, em seguida, fornecemos ao aplicativo a imagem a ser exibida na notificação.

   ![](assets/nmac_ios_3.png)

1. A **[!UICONTROL Subscription parameters]** guia permite que você defina o mapeamento com uma extensão do **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** esquema.

   >[!NOTE]
   >
   >Certifique-se de não usar o mesmo certificado para a versão de desenvolvimento (sandbox) e a versão de produção do aplicativo.

1. A **[!UICONTROL Sounds]** guia permite que você especifique um som para reproduzir. Clique **[!UICONTROL Add]** e preencha **[!UICONTROL Internal name]** o campo que deve conter o nome do arquivo incorporado no aplicativo ou o nome do som do sistema.

1. Clique em **[!UICONTROL Next]** para iniciar a configuração do aplicativo de desenvolvimento.

1. Make sure the same **[!UICONTROL Integration key]** is defined in Adobe Campaign and in the application code via the SDK. Para obter mais informações, consulte: [Integração do SDK de campanha ao aplicativo](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)móvel. Essa chave de integração, específica para cada aplicativo, permite vincular o aplicativo móvel à plataforma do Adobe Campaign.

   >[!NOTE]
   >
   > O **[!UICONTROL Integration key]** é totalmente personalizável com o valor da string, mas precisa ser exatamente o mesmo especificado no SDK.

1. Selecione um dos ícones prontos do **[!UICONTROL Application icon]** campo para personalizar o aplicativo móvel em seu serviço.

1. Click the **[!UICONTROL Enter the certificate...]** link then select the authentication certificate and enter the password that was provided by the mobile application developer. Você pode clicar **[!UICONTROL Test the connection]** para ter certeza de que é bem-sucedido.

   >[!NOTE]
   >
   >A Apple exige certificados diferentes para versões de Desenvolvimento e Produção de um mesmo aplicativo móvel. Você precisará configurar os dois aplicativos separados no Adobe Campaign.

   ![](assets/nmac_ios_4.png)

1. Clique em **[!UICONTROL Next]** para começar a configurar o aplicativo de produção e siga as mesmas etapas descritas acima.

   ![](assets/nmac_ios_5.png)

1. Clique em **[!UICONTROL Finish]**. Seu aplicativo iOS está pronto para ser usado no Campaign Classic.

### Etapa 4: Criação de uma notificação avançada do iOS {#creating-ios-delivery}

Com o iOS 10 ou superior, é possível gerar notificações ricas. O Adobe Campaign pode enviar notificações usando variáveis que permitirão ao dispositivo exibir uma notificação rica.

Agora é necessário criar uma nova entrega e vinculá-la ao aplicativo móvel que você criou.

1. Vá até **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Clique em **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Selecione **[!UICONTROL Deliver on iOS (ios)]** na lista **[!UICONTROL Delivery template]** suspensa. Adicione um anúncio **[!UICONTROL Label]** à sua entrega.

1. Clique em **[!UICONTROL To]** para definir a população a ser direcionada. Por padrão, o mapeamento de **[!UICONTROL Subscriber application]** destino é aplicado. Clique **[!UICONTROL Add]** para selecionar o serviço criado anteriormente.

   ![](assets/nmac_ios_9.png)

1. Na **[!UICONTROL Target type]** janela, selecione **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** e clique em **[!UICONTROL Next]**.

1. Na **[!UICONTROL Service]** lista suspensa, selecione o serviço criado anteriormente, depois o aplicativo que deseja direcionar e clique em **[!UICONTROL Finish]**.
Os **[!UICONTROL Application variables]** são adicionados automaticamente, dependendo do que foi adicionado durante as etapas de configuração.

   ![](assets/nmac_ios_6.png)

1. Edite sua notificação avançada.

   ![](assets/nmac_ios_7.png)

1. Marque a **[!UICONTROL Mutable content]** caixa na janela de notificação de edição para permitir que o aplicativo móvel baixe o conteúdo de mídia.

1. Click **[!UICONTROL Save]** and send your delivery.

A imagem e a página da Web devem ser exibidas na notificação por push quando recebidas nos dispositivos iOS móveis dos assinantes.

![](assets/nmac_ios_8.png)

## Configuração do aplicativo móvel com Android {#configuring-the-mobile-application-android}

### Etapa 1: Instalação do pacote {#installing-package-android}

1. Acesse o assistente de importação de pacote **[!UICONTROL Tools > Advanced > Package import...]** no console do cliente Adobe Campaign.

   ![](assets/package_ios.png)

1. Select **[!UICONTROL Install a standard package]**.

1. Na lista exibida, marque **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Clique em **[!UICONTROL Next]** e, em seguida, **[!UICONTROL Start]** para iniciar a instalação do pacote.

   Depois que os pacotes são instalados, a barra de progresso mostra **100%** e você pode ver a seguinte mensagem nos registros de instalação: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** a janela de instalação.

### Etapa 2: Configuração da conta externa Android {#configuring-external-account-android}

Para Android, dois conectores estão disponíveis:

* O conector V1 que permite uma conexão por MTA filho.
* O conector V2 que permite conexões simultâneas com o servidor FCM para melhorar o throughput.

Para escolher qual conector deseja usar, siga estas etapas:

1. Vá para **[!UICONTROL Administration > Platform > External accounts]**.
1. Selecione a conta **[!UICONTROL Android routing]** externa.
1. Na **[!UICONTROL Connector]** guia, preencha o **[!UICONTROL JavaScript used in the connector]** campo:

   Para Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > Você também pode configurá-lo como segue https://localhost:8080/nms/jsp/androidPushConnector.js, mas recomendamos que você use a versão 2 do conector.

   ![](assets/nmac_connectors3.png)

1. Para Android V2, um parâmetro adicional está disponível no arquivo de configuração do Adobe Server (serverConf.xml):

   * **maxGCMConnectPerChild**: Limite máximo de solicitações HTTP paralelas ao FCM iniciadas por cada servidor filho (8 por padrão).

### Etapa 3: Configuração do serviço Android {#configuring-android-service}

1. Vá para o **[!UICONTROL Profiles and Targets > Services and subscriptions]** nó e clique em **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Defina um **[!UICONTROL Label]** e um **[!UICONTROL Internal name]**.
1. Vá para o **[!UICONTROL Type]** campo e selecione **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >The default **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** target mapping is linked to the recipients table. If you want to use a different target mapping, you need to create a new target mapping and enter it in the **[!UICONTROL Target mapping]** field of the service. Para obter mais informações sobre como criar o target mapping, consulte o [Guia de configuração](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Em seguida, clique no **[!UICONTROL Add]** botão para selecionar o tipo de aplicativo.

   ![](assets/nmac_service_2.png)

1. Select **[!UICONTROL Create an Android application]**.

   ![](assets/nmac_android.png)

1. Insira um **[!UICONTROL Label]**.

1. Make sure the same **[!UICONTROL Integration key]** is defined in Adobe Campaign and in the application code via the SDK. Para obter mais informações, consulte: [Integração do SDK de campanha ao aplicativo](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)móvel.

   >[!NOTE]
   >
   > O **[!UICONTROL Integration key]** é totalmente personalizável com o valor da string, mas precisa ser exatamente o mesmo especificado no SDK.

1. Selecione um dos ícones prontos do **[!UICONTROL Application icon]** campo para personalizar o aplicativo móvel em seu serviço.

1. Digite as configurações de conexão do aplicativo: digite a chave do projeto fornecida pelo desenvolvedor do aplicativo móvel.

1. Como opção, você pode enriquecer um conteúdo de mensagem de push com alguns **[!UICONTROL Application variables]** se necessário. Eles são totalmente personalizáveis e uma parte da carga da mensagem enviada para o dispositivo móvel.

   No exemplo a seguir, adicionamos **título**, **imageURL** e **iconURL** para criar notificações por push avançadas e, em seguida, fornecemos ao aplicativo a imagem, o título e o ícone a serem exibidos na notificação.

   ![](assets/nmac_android_2.png)

1. Clique em **[!UICONTROL Finish]** e em **[!UICONTROL Save]**. Seu aplicativo Android agora está pronto para ser usado no Campaign Classic.

Por padrão, o Adobe Campaign salva uma chave no campo **[!UICONTROL User identifier]** (@userKey) da **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** tabela. Essa chave permite vincular uma subscrição a um recipient. Para coletar dados adicionais (como uma chave de reconciliação complexa), é necessário aplicar a seguinte configuração:

1. Create an extension of the **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** schema and define the new fields.
1. Defina o mapeamento na **[!UICONTROL Subscription parameters]** guia.
   >[!CAUTION]
   >
   >Make sure the configuration names in the **[!UICONTROL Subscription parameters]** tab are the same as those in the mobile application code. Consulte a seção [Integração do SDK de campanha à seção do aplicativo](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md) móvel.

### Etapa 4: Criar uma notificação avançada do Android {#creating-android-delivery}

Agora é necessário criar uma nova entrega e vinculá-la ao aplicativo móvel que você criou.

1. Vá até **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Clique em **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Selecione **[!UICONTROL Deliver on Android (android)]** na lista **[!UICONTROL Delivery template]** suspensa. Adicione um anúncio **[!UICONTROL Label]** à sua entrega.

1. Clique em **[!UICONTROL To]** para definir a população a ser direcionada. Por padrão, o mapeamento de **[!UICONTROL Subscriber application]** destino é aplicado. Clique **[!UICONTROL Add]** para selecionar o serviço criado anteriormente.

   ![](assets/nmac_android_7.png)

1. Na **[!UICONTROL Target type]** janela, selecione Assinantes de um aplicativo Android para dispositivos móveis e clique em **[!UICONTROL Next]**.

1. Na **[!UICONTROL Service]** lista suspensa, selecione o serviço criado anteriormente, depois o aplicativo e clique em **[!UICONTROL Finish]**.
Os **[!UICONTROL Application variables]** são adicionados automaticamente, dependendo do que foi adicionado durante as etapas de configuração.

   ![](assets/nmac_android_6.png)

1. Edite sua notificação avançada.

   ![](assets/nmac_android_5.png)

1. Click **[!UICONTROL Save]** and send your delivery.

A imagem e a página da web devem ser exibidas na notificação por push quando recebida nos dispositivos Android móveis dos subscritos.

![](assets/nmac_android_4.png)
