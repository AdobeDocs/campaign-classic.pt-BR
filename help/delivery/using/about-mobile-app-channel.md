---
title: Sobre o canal do aplicativo móvel no Adobe Campaign Classic
description: Esta seção fornece informações gerais específicas para o canal do aplicativo móvel no Adobe Campaign Classic.
page-status-flag: never-activated
uuid: e8d26b33-dc7c-4abd-956a-92f419a117e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 6b3fe8b9-dae6-4f8e-83e1-3376c0fe72a5
translation-type: tm+mt
source-git-commit: fd75f7f75e8e77d7228233ea311dd922d100417c
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 82%

---


# Sobre o canal de aplicativo móvel{#about-mobile-app-channel}

>[!CAUTION]
>
>Este documento detalha o processo de integração de seu aplicativo móvel com a plataforma Adobe Campaign. Ele não fornece informações sobre como criar o aplicativo móvel ou como configurá-lo para gerenciar notificações. Se desejar mais informações sobre isso, consulte a [documentação](https://developer.apple.com/) oficial da Apple e a [documentação](https://developer.android.com/index.html) do Android.

As seções abaixo fornecem informações específicas para o canal do aplicativo móvel.

Para informações gerais sobre como criar um delivery, consulte [esta seção](../../delivery/using/steps-about-delivery-creation-steps.md).

O **Mobile App Channel** permite usar a plataforma Adobe Campaign para enviar notificações personalizadas para terminais iOS e Android por meio de aplicativos. Dois canais de delivery estão disponíveis:

* Um canal iOS que permite enviar notificações para dispositivos móveis Apple.

   ![](assets/nmac_intro_2.png)

* Um canal Android que permite enviar mensagens de dados para dispositivos móveis Android.

   ![](assets/nmac_intro_1.png)

Correspondendo a esses dois canais, há duas atividades de delivery nos workflows de campanha:

![](assets/nmac_intro_3.png)

>[!NOTE]
>
>Dois templates de mensagens transacionais também estão disponíveis para o sistema de mensagens transacionais.

É possível definir o comportamento do aplicativo para quando o usuário ativar a notificação para exibir a tela correspondente ao contexto do aplicativo. Por exemplo:

* Uma notificação é enviada ao cliente para avisá-lo que seu pacote deixou o depósito. Ativar a notificação abre uma página com informações sobre o delivery.
* O usuário adicionou itens ao carrinho, mas deixou o aplicativo sem concluir a compra. Uma notificação é enviada, informando que o carrinho foi abandonado. Quando ativarem a notificação, o item é exibido na tela.

>[!CAUTION]
>
>* Verifique se as notificações enviadas para um aplicativo para dispositivos móveis estão em conformidade com os pré-requisitos e condições especificados pela Apple (Serviços de Notificação por Push da Apple) e pelo Google (Firebase Cloud Messaging).
>* Aviso: em alguns países, a lei exige que você informe os usuários sobre os tipos de dados coletados nos aplicativos móveis e a finalidade do seu processamento. Você deve verificar a legislação.


O workflow **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt) atualiza a notificação de cancelamentos de subscrições em dispositivos móveis. Para obter mais informações sobre este workflow, consulte o[guia de Workflows](../../workflow/using/mobile-app-channel.md).

A Adobe Campaign é compatível com aplicativos binários e HTTP/2. Para obter mais detalhes sobre as etapas de configuração, consulte [Configuração de um aplicativo para dispositivos móveis na seção Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

## Caminho dos dados {#data-path}

Os schemas a seguir detalham as etapas que permitem que um aplicativo móvel troque dados com o Adobe Campaign. Esse processo envolve três entidades:

* o aplicativo móvel
* o serviço de notificação: APNs (Apple Push Notification Service) para Apple e FCM (Firebase Cloud Messaging) para Android
* Adobe Campaign

As três principais etapas do processo de notificação são: registro do aplicativo no Adobe Campaign (coleção de assinaturas), deliveries e rastreamento.

### Etapa 1: Coleção de subscrição {#step-1--subscription-collection}

O aplicativo móvel é baixado pelo usuário da App Store ou do Google Play. Este aplicativo contém as configurações de conexão (certificado do iOS e chave do projeto para Android) e a chave de integração. Na primeira vez que o aplicativo é aberto, (dependendo da configuração), o usuário pode ser solicitado a inserir informações de registro (@userKey: email ou número de conta por exemplo). Ao mesmo tempo, o aplication solicita ao serviço de notificações para coletar um ID de notificação (ID de envio). Todas essas informações (configurações de conexão, chave de integração, identificador de notificação, userKey) são enviadas ao Adobe Campaign.

![](assets/nmac_register_view.png)

### Etapa 2 - Delivery {#step-2--delivery}

Os profissionais de marketing miram os assinantes de aplicativos. O processo de delivery envia as configurações de conexão para o serviço de notificação (certificado iOS e chave do projeto para Android), a ID de notificação (ID de envio) e o conteúdo da notificação. O serviço de notificação envia notificações para os terminais de destino.

Estas informações estão disponíveis no Adobe Campaign:

* Somente Android: número de dispositivos que exibem a notificação (impressões)
* Android e iOS: número de cliques na notificação

![](assets/nmac_delivery_view.png)

O servidor Adobe Campaign deve poder entrar em contato com o servidor APNs nas seguintes portas:

* 2195 (envio) e 2186 (serviço de feedback) para conector binário do iOS
* 443 para conector HTTP/2 do iOS

   >[!NOTE]
   >
   > A partir da versão 20.3 da Campanha, o conector binário herdado do iOS será descontinuado. Se estiver usando esse conector, é necessário adaptar sua implementação de acordo. [Saiba mais](https://helpx.adobe.com/campaign/kb/migrate-to-http2.html)

Para verificar se funciona corretamente, use os seguintes comandos:

* Para testes:

   ```
   telnet gateway.sandbox.push.apple.com
   ```

* Na produção:

   ```
   telnet gateway.push.apple.com
   ```

Se for usado um conector binário iOS, o MTA e o servidor Web devem poder entrar em contato com os APNs na porta 2195 (envio), o servidor de fluxo de trabalho deve poder entrar em contato com os APNs na porta 2196 (serviço de feedback).

Se um conector HTTP/2 do iOS for usado, o MTA, o servidor da Web e o servidor de fluxo de trabalho devem poder entrar em contato com os APNs na porta 443.

