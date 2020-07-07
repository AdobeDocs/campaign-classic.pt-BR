---
title: Criar notificações
seo-title: Criar notificações
description: Criar notificações
seo-description: null
page-status-flag: never-activated
uuid: fb1862df-e616-4147-a642-dc867bc983b5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 345af5c2-c852-4086-8ed0-ff3e7e402e04
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c830d40cef836533c5104901d03a07e7cf96d3d6
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 100%

---


# Criar notificações{#creating-notifications}

Esta seção detalha os elementos específicos para o delivery de notificações iOS e Android. Os conceitos globais sobre a criação de delivery são apresentados [nesta seção](../../delivery/using/steps-about-delivery-creation-steps.md).

Comece criando um novo delivery.

![](assets/nmac_delivery_1.png)

## Envio de notificações no iOS {#sending-notifications-on-ios}

1. Selecione o modelo de delivery **[!UICONTROL Deliver on iOS]**.

   ![](assets/nmac_delivery_ios_1.png)

1. Para definir o target da notificação, clique no link **[!UICONTROL To]** e, em seguida, clique em **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >O processo detalhado ao selecionar a população do target de um delivery é apresentado [nesta seção](../../delivery/using/steps-defining-the-target-population.md).
   >
   >Para obter mais informações sobre o uso de campos de personalização, consulte [Sobre a personalização](../../delivery/using/about-personalization.md).
   >
   >Para obter mais informações sobre a inclusão de uma lista de propagação, consulte [Sobre seed addresses](../../delivery/using/about-seed-addresses.md).

1. Selecione **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**, depois o serviço relevante para o aplicativo móvel (Neotrips, neste caso) e clique na versão iOS do aplicativo.

   ![](assets/nmac_delivery_ios_3.png)

1. Selecione o tipo de notificação: **[!UICONTROL Alert]**, **[!UICONTROL Badge]**, ou **[!UICONTROL Alert and badge]** ou **[!UICONTROL Silent Push]**.

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >O modo de **Silent Push** está disponível no iOS 7. Isso permite que uma notificação &quot;silenciosa&quot; seja enviada a um aplicativo móvel. O usuário não está ciente da chegada da notificação. Ele é transferido diretamente para o aplicativo.

1. No campo **[!UICONTROL Title]**, insira o rótulo do título que deve aparecer na notificação. Isso só aparecerá na lista disponível no centro de notificações. Este campo permite a definição do valor do parâmetro **title** da carga de notificação iOS.

1. Se o conector HTTP/2 é usado, é possível adicionar um subtítulo (valor do parâmetro de **subtitle** da carga de notificação do iOS). Consulte a seção [Configuração do aplicativo móvel no Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md) .

1. Em seguida, insira o **[!UICONTROL Message]** e o **[!UICONTROL Value of the badge]** baseado no tipo de notificação escolhido.

   ![](assets/nmac_delivery_ios_5.png)

   >[!NOTE]
   >
   >Os tipos de notificação **[!UICONTROL Badge]** e **[!UICONTROL Alert and badge]** permitem modificar o valor da notificação (o número acima do logotipo do aplicativo móvel). Para atualizar a notificação, basta inserir 0 como valor. Se o campo estiver vazio, o valor da notificação não será alterado.

1. Clique no ícone **[!UICONTROL Insert emoticon]** para inserir emoticons à notificação via push. Para personalizar a lista de emoticons, consulte [personalização da lista de emoticons](../../delivery/using/customizing-emoticon-list.md)

1. O **[!UICONTROL Action button]** permite definir um rótulo para o botão de ação que aparece nas notificações de alerta (campo **action_loc_key** da carga). Se o aplicativo iOS gerencia cadeias de caracteres localizáveis (**Localizable.strings**), digite a chave correspondente nesse campo. Se o aplicativo não gerencia o texto localizável, insira o rótulo que você deseja visualizar no botão de ação. Para mais informações sobre strings localizáveis, consulte a [Apple documentation](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW1) .
1. No campo **[!UICONTROL Play a sound]**, selecione o som a ser reproduzido pelo terminal móvel quando a notificação for recebida.

   >[!NOTE]
   >
   >Os sons devem ser incluídos no aplicativo e definidos quando o serviço for criado. Consulte [Configuração da conta externa do iOS](../../delivery/using/configuring-the-mobile-application.md#configuring-external-account-ios).

1. No campo **[!UICONTROL Application variables]**, insira o valor de cada variável. As variáveis do aplicativo permitem definir o comportamento de notificação: por exemplo, é possível configurar uma tela de aplicativo específica para ser exibida quando o usuário ativar a notificação.

   >[!NOTE]
   >
   >As variáveis do aplicativo devem ser definidas no código do aplicativo móvel e inseridas durante a criação do serviço. Para obter mais informações, consulte a[Configuração do aplicativo móvel no Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

1. Quando a notificação estiver configurada, clique na guia **[!UICONTROL Preview]** para visualizar a notificação.

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >O estilo de notificação (banner ou alerta) não é definido no Adobe Campaign. Isso depende da configuração selecionada pelo usuário nas configurações do iOS. No entanto, o Adobe Campaign permite a visualização de cada tipo de estilo de notificação. Clique na seta na parte inferior direita para alternar entre os estilos.
   >
   >A pré-visualização utiliza a aparência e comportamento do iOS 10.

Para enviar uma prova e o delivery final, use o mesmo processo que os deliveries de email.

Após enviar as mensagens, você pode monitorar e rastrear seus deliveries. Para obter mais informações, consulte essas seções.

* [Notificação por push em quarentena](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [Monitoramento de uma entrega](../../delivery/using/monitoring-a-delivery.md)
* [Noções básicas sobre falhas de entrega](../../delivery/using/understanding-delivery-failures.md)

## Enviar notificações no Android {#sending-notifications-on-android}

1. Comece a partir do **[!UICONTROL Deliver on Android (android)]** template de delivery.

   ![](assets/nmac_delivery_android_1.png)

1. Para definir o target da notificação, clique no link **[!UICONTROL To]** e, em seguida, clique em **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_android_2.png)

1. Selecione **[!UICONTROL Subscribers of an Android mobile application]**, escolha o serviço relevante para seu aplicativo móvel (Neotrips, neste caso) e selecione a versão Android do aplicativo.

   ![](assets/nmac_delivery_android_3.png)

1. Em seguida, insira o conteúdo da notificação.

   ![](assets/nmac_delivery_android_4.png)

1. Clique no ícone **[!UICONTROL Insert emoticon]** para inserir emoticons à notificação via push. Para personalizar a lista de emoticons, consulte [personalização da lista do emoticon](../../delivery/using/defining-interactive-content.md)

1. No campo **[!UICONTROL Application variables]**, insira o valor de cada variável. As variáveis do aplicativo permitem definir o comportamento de notificação: por exemplo, é possível configurar uma tela de aplicativo específica para ser exibida quando o usuário ativar a notificação.

   >[!NOTE]
   >
   >As variáveis do aplicativo devem ser definidas no código do aplicativo móvel e inseridas durante a criação do serviço. Para obter mais informações, consulte a[Configuração do aplicativo móvel no Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

1. Quando a notificação estiver configurada, clique na guia **[!UICONTROL Preview]** para visualizar a notificação.

   ![](assets/nmac_intro_1.png)

Para enviar uma prova e o delivery final, use o mesmo processo que os deliveries de email.

O processo detalhado da validação e envio de um delivery é apresentado nas seções abaixo:

* [Validando o dleivery](../../delivery/using/steps-validating-the-delivery.md)
* [Enviando o delivery](../../delivery/using/steps-sending-the-delivery.md)

Após enviar as mensagens, você pode monitorar e rastrear seus deliveries. Para obter mais informações, consulte essas seções.

* [Notificação por push em quarentena](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [Monitoramento de uma entrega](../../delivery/using/monitoring-a-delivery.md)
* [Noções básicas sobre falhas de entrega](../../delivery/using/understanding-delivery-failures.md)
