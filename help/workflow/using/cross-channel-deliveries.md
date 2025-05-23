---
product: campaign
title: Entregas entre canais
description: Saiba mais sobre entregas entre canais
feature: Workflows, Channels Activity
hide: true
hidefromtoc: true
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: ht
source-wordcount: '287'
ht-degree: 100%

---

# Entregas entre canais{#cross-channel-deliveries}



Entregas entre canais estão disponíveis na guia **[!UICONTROL Deliveries]** de atividades do fluxo de trabalho da campanha.

Os vários canais disponíveis são:

* [Email](../../delivery/using/about-email-channel.md)
* [Correspondência direta](../../delivery/using/about-direct-mail-channel.md)
* [Celular](../../delivery/using/sms-channel.md)
* [X (anteriormente conhecido como Twitter)](../../social/using/about-social-marketing.md)
* [iOS](../../delivery/using/create-notifications-ios.md)
* [Android](../../delivery/using/create-notifications-android.md)

Selecionar o modelo no qual deseja basear a entrega e definir seu conteúdo.

Você pode especificar um target para o upstream de entrega de fluxo de trabalho usando as diferentes atividades de direcionamento.

No exemplo abaixo, vamos criar um fluxo de trabalho para enviar um email ou SMS a assinantes de notificação por push e, em seguida, uma notificação por push uma semana depois. Para fazer isso:

1. Crie uma campanha.
1. Na guia **[!UICONTROL Targeting and workflows]** da campanha, adicione uma **[!UICONTROL Query]** ao workflow.
1. Configure seu query. Por exemplo, aqui selecionamos os destinatários que assinaram notificações por push como o target dimension.

   >[!NOTE]
   >
   >Para as notificações por push, use a dimensão de direcionamento dos **aplicativos de assinante**.

   ![](assets/cross_channel_delivery_1.png)

1. Adicione as condições de filtro ao seu query. Nesse caso, selecionamos destinatários com um número de celular ou endereço de email.

   ![](assets/cross_channel_delivery_2.png)

1. Adicione uma atividade **[!UICONTROL Split]** ao workflow para dividir destinatários com um número de celular e aqueles com um endereço de email.
1. Na guia **[!UICONTROL Delivery]**, selecione um workflow para cada target.

   Crie a sua entrega como feito no assistente de entrega clássico, clicando duas vezes na atividade de entrega no seu fluxo de trabalho. Para obter mais informações, consulte esta [página](../../delivery/using/about-email-channel.md).

   ![](assets/cross_channel_delivery_3.png)

1. Adicione e configure uma atividade **[!UICONTROL Wait]** para os destinatários não receberem muitas entregas de uma vez.
1. Adicione uma atividade **[!UICONTROL Split]** para dividir os assinantes de aplicativos móveis iOS ou Android.

   Selecione um serviço para cada um dos sistemas operacionais. Para obter mais informações sobre criação de serviços, consulte esta [página](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. Selecione e configure uma entrega de aplicativo móvel para cada um dos sistemas operacionais.

   ![](assets/cross_channel_delivery_5.png)
