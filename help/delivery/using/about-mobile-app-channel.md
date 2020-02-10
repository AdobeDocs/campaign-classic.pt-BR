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
source-git-commit: c581f22261af7e083f6bd47e603d17d2d71e7ce6

---


# Sobre o canal de aplicativo móvel{#about-mobile-app-channel}

>[!CAUTION]
>
>Este documento detalha o processo de integração de seu aplicativo móvel com a plataforma Adobe Campaign. Ele não fornece informações sobre como criar o aplicativo móvel ou como configurá-lo para gerenciar notificações. Se desejar mais informações sobre isso, consulte a documentação oficial da Apple ([https://developer.apple.com/](https://developer.apple.com/)) e do Android ([https://developer.android.com/index.html](https://developer.android.com/index.html)).

As seções abaixo fornecem informações específicas para o canal do aplicativo móvel. For global information on how to create a delivery, refer to [this section](../../delivery/using/steps-about-delivery-creation-steps.md).

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
>* Verifique se as notificações enviadas para um aplicativo móvel estão em conformidade com os pré-requisitos e condições especificados pela Apple (Serviços de Notificação por Push da Apple) e pelo Google (Google Cloud Messaging).
>* Aviso: em alguns países, a lei exige que você informe os usuários sobre os tipos de dados coletados nos aplicativos móveis e a finalidade do seu processamento. Você deve verificar a legislação.


The **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt) workflow updates notification unsubscriptions on mobile devices. Para obter mais informações sobre este workflow, consulte o[guia de Workflows](../../workflow/using/mobile-app-channel.md).

O Adobe Campaign é compatível com o APNS binário e HTTP/2. For more details on the configuration steps, refer to the [Connectors](../../delivery/using/setting-up-mobile-app-channel.md#connectors) section.
