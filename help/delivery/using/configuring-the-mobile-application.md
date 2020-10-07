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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1519'
ht-degree: 100%

---


# Configuração do aplicativo móvel no Adobe Campaign {#configuring-the-mobile-application-in-adobe-campaign}

Encontre abaixo a amostra da configuração baseada em uma empresa que vende online pacotes de viagens. Seu aplicativo móvel (Neotrips) está disponível para os clientes em duas versões: Neotrips para Android e Neotrips para iOS. Para configurar o aplicativo móvel no Adobe Campaign, é necessário:

* Crie um serviço de informação do tipo **[!UICONTROL Mobile application]** para o aplicativo para dispositivos móveis Neotrips.
* Adicione as versões iOS e Android do aplicativo a este serviço.
* Crie um delivery para iOS e Android.

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Acesse a guia **[!UICONTROL Subscriptions]** do serviço para exibir a lista de assinantes do serviço, ou seja, todas as pessoas que instalaram o aplicativo nos próprios celulares e concordaram em receber as notificações.

## Configuração do aplicativo para dispositivos móveis com iOS {#configuring-the-mobile-application-ios}

>[!CAUTION]
>
>O aplicativo deve ter sido configurado para ações Push ANTES de qualquer integração ao Adobe Campaign SDK.
>
>Se esse não for o caso, consulte [esta página](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/).

### Etapa 1: instalação do pacote {#installing-package-ios}

1. Acesse o assistente de importação do pacote do **[!UICONTROL Tools > Advanced > Package import...]** no console do cliente Adobe Campaign.

   ![](assets/package_ios.png)

1. Selecione **[!UICONTROL Install a standard package]**.

1. Na lista que aparece, marque **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Clique em **[!UICONTROL Next]** e, em seguida, em **[!UICONTROL Start]** para começar a instalação do pacote.

   Depois que os pacotes forem instalados, a barra de progresso mostrará **100%** e você poderá ver a seguinte mensagem nos registros de instalação: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** a janela de instalação.

### Etapa 2: configuração da conta externa d iOS {#configuring-external-account-ios}

Para iOS, dois conectores estão disponíveis:

* O conector binário do iOS envia notificações no servidor binário APNS herdado.
* O conector HTTP/2 do iOS envia notificações para o HTTP/2 APNS.

Para escolher qual conector deseja usar, siga estas etapas:

1. Vá para **[!UICONTROL Administration > Platform > External accounts]**.
1. Selecione a conta externa **[!UICONTROL iOS routing]**.
1. Na guia **[!UICONTROL Connector]**, preencha o campo **[!UICONTROL Access URL of the connector]**:

   Para iOS HTTP2: http://localhost:8080/nms/jsp/iosHTTP2.jsp

   ![](assets/nmac_connectors.png)

   >[!NOTE]
   >
   > Você também pode configurá-lo assim: https://localhost:8080/nms/jsp/ios.jsp, mas recomendamos que você use a versão 2 do conector.

1. Clique em **[!UICONTROL Save]**.

O conector iOS está configurado. Você pode começar a criar seu serviço.

### Etapa 3: configuração do serviço iOS {#configuring-ios-service}

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

1. Selecione um dos ícones prontos do campo **[!UICONTROL Application icon]** para personalizar o aplicativo para dispositivos móveis em seu serviço.

1. Clique no link **[!UICONTROL Enter the certificate...]** e, em seguida, selecione o certificado de autenticação e insira a senha fornecida pelo desenvolvedor de aplicativos para dispositivos móveis. Você pode clicar em **[!UICONTROL Test the connection]** para ter certeza de que ele é bem-sucedido.

   >[!NOTE]
   >
   >A Apple exige certificados diferentes para versões de Desenvolvimento e Produção de um mesmo aplicativo para dispositivos móveis. Você precisará configurar os dois aplicativos separados no Adobe Campaign.

   ![](assets/nmac_ios_4.png)

1. Clique em **[!UICONTROL Next]** para configurar o aplicativo de produção e siga as mesmas etapas descritas acima.

   ![](assets/nmac_ios_5.png)

1. Clique em **[!UICONTROL Finish]**. Seu aplicativo iOS está pronto para ser usado no Campaign Classic.

### Etapa 4: criação de uma notificação avançada do iOS {#creating-ios-delivery}

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

## Configuração do aplicativo para dispositivos móveis com Android {#configuring-the-mobile-application-android}

### Etapa 1: instalação do pacote {#installing-package-android}

1. Acesse o assistente de importação do pacote do **[!UICONTROL Tools > Advanced > Package import...]** no console do cliente Adobe Campaign.

   ![](assets/package_ios.png)

1. Selecione **[!UICONTROL Install a standard package]**.

1. Na lista que aparece, marque **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Clique em **[!UICONTROL Next]** e, em seguida, em **[!UICONTROL Start]** para começar a instalação do pacote.

   Depois que os pacotes forem instalados, a barra de progresso mostrará **100%** e você poderá ver a seguinte mensagem nos registros de instalação: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** a janela de instalação.

### Etapa 2: configuração da conta externa Android {#configuring-external-account-android}

Para Android, dois conectores estão disponíveis:

* O conector V1 que permite uma conexão por MTA filho.
* O conector V2 que permite conexões simultâneas com o servidor FCM para melhorar o throughput.

Para escolher qual conector deseja usar, siga estas etapas:

1. Vá para **[!UICONTROL Administration > Platform > External accounts]**.
1. Selecione a conta externa **[!UICONTROL Android routing]**.
1. Na guia **[!UICONTROL Connector]**, preencha o campo **[!UICONTROL JavaScript used in the connector]**:

   Para Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > Você também pode configurá-lo assim: https://localhost:8080/nms/jsp/androidPushConnector.js, mas recomendamos que você use a versão 2 do conector.

   ![](assets/nmac_connectors3.png)

1. Para Android V2, um parâmetro adicional está disponível no arquivo de configuração do Adobe Server (serverConf.xml):

   * **maxGCMConnectPerChild**: Limite máximo de solicitações HTTP paralelas para o FCM iniciado por cada servidor filho (8 por padrão).

### Etapa 3: configuração do serviço Android {#configuring-android-service}

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

1. Selecione **[!UICONTROL Create an Android application]**.

   ![](assets/nmac_android.png)

1. Insira um **[!UICONTROL Label]**.

1. Verifique se a mesma **[!UICONTROL Integration key]** está definida no Adobe Campaign e no código do aplicativo por meio do SDK. Para obter mais informações, consulte: [Integração do SDK do Campaign ao aplicativo móvel](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md).

   >[!NOTE]
   >
   > O **[!UICONTROL Integration key]** é totalmente personalizável com o valor da string, mas precisa ser exatamente o mesmo especificado no SDK.

1. Selecione um dos ícones prontos do campo **[!UICONTROL Application icon]** para personalizar o aplicativo para dispositivos móveis em seu serviço.

1. Inserir as configurações de conexão do aplicativo: insira a chave do projeto fornecida pelo desenvolvedor do aplicativo para dispositivos móveis.

1. Como opção, você pode enriquecer um conteúdo de mensagem de push com alguns **[!UICONTROL Application variables]** se necessário. Eles são totalmente personalizáveis e uma parte da carga da mensagem é enviada para o dispositivo móvel.

   No exemplo a seguir, adicionamos **title**, **imageURL** e **iconURL** para criar notificações por push avançadas e, em seguida, fornecemos ao aplicativo a imagem, o título e o ícone que serão exibidos na notificação.

   ![](assets/nmac_android_2.png)

1. Clique em **[!UICONTROL Finish]** e em **[!UICONTROL Save]**. Seu aplicativo Android agora está pronto para ser usado no Campaign Classic.

Por padrão, o Adobe Campaign salva uma chave no campo **[!UICONTROL User identifier]** (@userKey) da tabela **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]**. Essa chave permite vincular uma subscrição a um recipient. Para coletar dados adicionais (como uma chave de reconciliação complexa), é necessário aplicar a seguinte configuração:

1. Crie uma extensão do schema **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** e defina os novos campos.
1. Defina o mapeamento na guia **[!UICONTROL Subscription parameters]**.
   >[!CAUTION]
   >
   >Verifique se os nomes da configuração da guia **[!UICONTROL Subscription parameters]** são iguais aos do código do aplicativo móvel. Consulte a seção [Integrating Campaign SDK into the mobile application](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md).

### Etapa 4: criar uma notificação avançada do Android {#creating-android-delivery}

Em seguida, é necessário criar um novo delivery e vinculá-lo ao aplicativo para dispositivos móveis criado.

1. Vá até **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Clique em **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Selecione **[!UICONTROL Deliver on Android (android)]** na lista suspensa **[!UICONTROL Delivery template]**. Adicione um **[!UICONTROL Label]** ao delivery.

1. Clique em **[!UICONTROL To]** para definir a população como target. Por padrão, o target mapping **[!UICONTROL Subscriber application]** é aplicado. Clique em **[!UICONTROL Add]** para selecionar o serviço criado anteriormente.

   ![](assets/nmac_android_7.png)

1. Na janela **[!UICONTROL Target type]**, selecione Assinantes de um aplicativo Android para dispositivos móveis e clique em **[!UICONTROL Next]**.

1. Na lista suspensa **[!UICONTROL Service]**, selecione o serviço criado anteriormente, depois o aplicativo e clique em **[!UICONTROL Finish]**.
Os **[!UICONTROL Application variables]** são adicionados automaticamente, dependendo do que foi adicionado durante as etapas de configuração.

   ![](assets/nmac_android_6.png)

1. Edite a notificação avançada.

   ![](assets/nmac_android_5.png)

1. Clique em **[!UICONTROL Save]** e envie o delivery.

A imagem e a página da web devem ser exibidas na notificação por push quando recebida nos dispositivos Android móveis dos subscritos.

![](assets/nmac_android_4.png)
