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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# Sobre o canal de aplicativo móvel{#about-mobile-app-channel}

>[!CAUTION]
>
>Este documento detalha o processo de integração de seu aplicativo móvel com a plataforma Adobe Campaign. Ele não fornece informações sobre como criar o aplicativo móvel ou como configurá-lo para gerenciar notificações. If you would like further information on this, refer to the official Apple [documentation](https://developer.apple.com/) and Android [documentation](https://developer.android.com/index.html).

As seções abaixo fornecem informações específicas para o canal do aplicativo móvel.

For global information on how to create a delivery, refer to [this section](../../delivery/using/steps-about-delivery-creation-steps.md).

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
>* É necessário verificar se as notificações enviadas para um aplicativo móvel são compatíveis com os pré-requisitos e condições especificados pela Apple (Apple Push Notification Service) e Google (Firebase Cloud Messaging).
>* Aviso: em alguns países, a lei exige que você informe os usuários sobre os tipos de dados coletados nos aplicativos móveis e a finalidade do seu processamento. Você deve verificar a legislação.


The **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt) workflow updates notification unsubscriptions on mobile devices. Para obter mais informações sobre este workflow, consulte o[guia de Workflows](../../workflow/using/mobile-app-channel.md).

O Adobe Campaign é compatível com o APNS binário e HTTP/2. Para obter mais detalhes sobre as etapas de configuração, consulte a seção [Configuração de um aplicativo móvel no Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md) .

## Caminho dos dados {#data-path}

Os schemas a seguir detalham as etapas que permitem que um aplicativo móvel troque dados com o Adobe Campaign. Esse processo envolve três entidades:

* o aplicativo móvel
* o serviço de notificação: APNS (Serviço de notificação por push da Apple) para Apple e FCM (Firebase Cloud Messaging) para Android
* Adobe Campaign

As três principais etapas do processo de notificação são: registro do aplicativo no Adobe Campaign (coleção de assinaturas), deliveries e rastreamento.

### Etapa 1: Coleção de assinatura {#step-1--subscription-collection}

O aplicativo móvel é baixado pelo usuário da App Store ou do Google Play. Este aplicativo contém as configurações de conexão (certificado do iOS e chave do projeto para Android) e a chave de integração. Na primeira vez que o aplicativo é aberto, (dependendo da configuração), o usuário pode ser solicitado a inserir informações de registro (@userKey: email ou número de conta por exemplo). Ao mesmo tempo, o aplication solicita ao serviço de notificações para coletar um ID de notificação (ID de envio). Todas essas informações (configurações de conexão, chave de integração, identificador de notificação, userKey) são enviadas ao Adobe Campaign.

![](assets/nmac_register_view.png)

### Etapa 2: Entrega {#step-2--delivery}

Os profissionais de marketing miram os assinantes de aplicativos. O processo de delivery envia as configurações de conexão para o serviço de notificação (certificado iOS e chave do projeto para Android), a ID de notificação (ID de envio) e o conteúdo da notificação. O serviço de notificação envia notificações para os terminais de destino.

Estas informações estão disponíveis no Adobe Campaign:

* Somente Android: número de dispositivos que exibem a notificação (impressões)
* Android e iOS: número de cliques na notificação

![](assets/nmac_delivery_view.png)

O servidor do Adobe Campaign deve ser capaz de entrar em contato com o servidor APNS nas seguintes portas:

* 2195 (envio) e 2186 (serviço de feedback) para conector binário do iOS
* 443 para conector HTTP/2 do iOS

Para verificar se funciona corretamente, use os seguintes comandos:

* Para testes:

   ```
   telnet gateway.sandbox.push.apple.com
   ```

* Na produção:

   ```
   telnet gateway.push.apple.com
   ```

Se um conector binário do iOS for usado, o MTA e o servidor Web deverão ser capazes de contatar o APNS na porta 2195 (enviando), o servidor de workflow deve ser capaz de contatar o APNS na porta 2196 (serviço de feedback).

Se um conector HTTP/2 do iOS for usado, o MTA, o servidor Web e o workflow devem ser capazes de contatar o APNS na porta 443.

