---
product: campaign
title: Deliveries entre canais
description: Saiba mais sobre deliveries entre canais
feature: Workflows, Channels Activity
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
source-git-commit: e454cc29038b4eab9fad1dcb46813fc8e1a83db1
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 100%

---

# Entregas entre canais{#cross-channel-deliveries}

![](../../assets/common.svg)

Entregas entre canais estão disponíveis na guia **[!UICONTROL Deliveries]** de atividades do fluxo de trabalho da campanha.

Os vários canais disponíveis são:

* [Email](../../delivery/using/about-email-channel.md)
* [Correspondência direta](../../delivery/using/about-direct-mail-channel.md)
* [Celular](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/publishing-on-twitter.md) (somente Campaign Classic v7)
* [Facebook](../../social/using/publishing-on-facebook.md) (somente Campaign Classic v7)
* [iOS](../../delivery/using/create-notifications-ios.md)
* [Android](../../delivery/using/create-notifications-android.md)

Selecionar o modelo no qual deseja basear a entrega e definir seu conteúdo.

Você pode especificar um target para o upstream de entrega de fluxo de trabalho usando as diferentes atividades de direcionamento.

No exemplo abaixo, vamos criar um fluxo de trabalho para enviar um email ou SMS a assinantes de notificação por push e, em seguida, uma notificação por push uma semana depois. Para fazer isso:

1. Crie uma campanha.
1. Na guia **[!UICONTROL Targeting and workflows]** da campanha, adicione uma **[!UICONTROL Query]** ao workflow.
1. Configure seu query. Por exemplo, aqui selecionamos os recipients que assinaram notificações por push como o target dimension.

   >[!NOTE]
   >
   >Para as notificações por push, use a dimensão de direcionamento dos **aplicativos de assinante**.

   ![](assets/cross_channel_delivery_1.png)

1. Adicione as condições de filtro ao seu query. Nesse caso, selecionamos recipients com um número de celular ou endereço de email.

   ![](assets/cross_channel_delivery_2.png)

1. Adicione uma atividade **[!UICONTROL Split]** ao workflow para dividir recipients com um número de celular e aqueles com um endereço de email.
1. Na guia **[!UICONTROL Delivery]**, selecione um workflow para cada target.

   Crie seu delivery da mesma forma que com um assistente de delivery comum clicando duas vezes na atividade de delivery no seu workflow. Para obter mais informações, consulte esta [página](../../delivery/using/about-email-channel.md).

   ![](assets/cross_channel_delivery_3.png)

1. Adicione e configure uma atividade **[!UICONTROL Wait]** para os recipients não receberem muitos deliveries de uma vez.
1. Adicione uma atividade **[!UICONTROL Split]** para dividir os assinantes de aplicativos móveis iOS ou Android.

   Selecione um serviço para cada um dos sistemas operacionais. Para obter mais informações sobre criação de serviços, consulte esta [página](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. Selecione e configure um delivery de aplicativo móvel para cada um dos sistemas operacionais.

   ![](assets/cross_channel_delivery_5.png)
