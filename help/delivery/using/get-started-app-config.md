---
solution: Campaign Classic
product: campaign
title: 'Configuração do aplicativo móvel no Adobe Campaign '
description: Saiba como iniciar a configuração do aplicativo móvel
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 1d7d48f52f69e4902eafa6806c2cd9170c21fe5a
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 92%

---


# Introdução à configuração do aplicativo

Encontre abaixo a amostra da configuração com base em uma empresa que vende pacotes de viagem online. Seu aplicativo móvel (Neotrips) está disponível para os clientes em duas versões: Neotrips para Android e Neotrips para iOS.

Para enviar notificações por push no Adobe Campaign, é necessário:

* Criar um serviço de informação do tipo **[!UICONTROL Mobile application]** para o aplicativo para dispositivos móveis Neotrips. Consulte [esta seção para iOS](../../delivery/using/configuring-the-mobile-application.md#configuring-ios-service). e [esta seção para Android](../../delivery/using/configuring-the-mobile-application-android.md#configuring-android-service).
* Adicionar as versões iOS e Android do aplicativo a este serviço.
* Criar um delivery para iOS e Android. [Consulte esta página](../../delivery/using/creating-notifications.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Acesse a guia **[!UICONTROL Subscriptions]** do serviço para exibir a lista de assinantes do serviço, ou seja, todas as pessoas que instalaram o aplicativo nos próprios celulares e concordaram em receber as notificações.

## Instalação do pacote {#installing-package-ios}

![](assets/do-not-localize/how-to-video.png) [Saiba como instalar o pacote de aplicativo móvel em vídeo](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=en#sending-messages)

Como um cliente híbrido/hospedado, entre em contato com a equipe de Atendimento ao cliente para acessar o canal de notificação por push no Campaign.

Como cliente local, é necessário executar as seguintes etapas de instalação:

1. Acesse o assistente de importação do pacote do **[!UICONTROL Tools > Advanced > Package import...]** no console do cliente Adobe Campaign.

   ![](assets/package_ios.png)

1. Selecione **[!UICONTROL Install a standard package]**.

1. Na lista que aparece, marque **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Clique em **[!UICONTROL Next]** e, em seguida, em **[!UICONTROL Start]** para começar a instalação do pacote.

   Depois que os pacotes forem instalados, a barra de progresso mostrará **100%** e você poderá ver a seguinte mensagem nos registros de instalação: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** a janela de instalação.

Quando esta etapa estiver concluída, você poderá configurar seus aplicativos Android e iOS.
Consulte estas seções:

* [Etapas de configuração para iOS](../../delivery/using/configuring-the-mobile-application.md)

* [Etapas de configuração para Android](../../delivery/using/configuring-the-mobile-application-android.md)
