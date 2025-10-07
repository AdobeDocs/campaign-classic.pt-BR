---
product: campaign
title: Introdução ao canal de aplicativo móvel
description: Introdução ao canal de aplicativo para dispositivos móveis no Adobe Campaign
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: a1e9fec0e9c85bf25b79e24a7432dfb45bd1a0cb
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 43%

---

# Introdução ao canal de aplicativo móvel{#about-mobile-app-channel}

Com o Adobe Campaign, crie entregas de notificação por push para enviar mensagens personalizadas aos usuários do aplicativo móvel.

As notificações por push permitem que você envolva os usuários no iOS e no Android em tempo real. Ao enviar atualizações, anúncios ou promoções, é possível controlar o conteúdo, o tempo e o direcionamento. Saiba como configurar e usar o canal de push, gerenciar assinaturas, integrar com APNs e FCM e personalizar mensagens na [documentação do Adobe Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/emails/email){target=_blank}.

Como parte da iniciativa de promoção do Campaign v8, a documentação do Campaign Classic foi reorganizada. Os recursos comuns agora estão disponíveis apenas no conjunto de documentações do Campaign v8.

>[!BEGINTABS]

>[!TAB Documentação do canal por push]

Para saber mais sobre o canal de notificações por push, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target=_blank}.

[![imagem](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target=_blank}


>[!TAB Criação de entrega por push]

Saiba mais sobre as principais etapas relacionadas à criação de delivery por push na documentação do Campaign v8:

* [Criar uma notificação por push](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html#push-create){target="_blank"}: conheça as diferentes etapas necessárias para criar uma entrega por push.
* [Enviar e monitorar a notificação por push](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html#push-test){target="_blank"}: saiba como validar, enviar e controlar suas entregas.
* [Crie uma entrega por push avançada do Android](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-android.html){target="_blank"}: saiba como criar e configurar notificações por push avançadas para dispositivos Android.
* [Crie uma entrega de push avançada do iOS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-ios.html){target="_blank"}: saiba como projetar e configurar notificações de push avançadas para dispositivos iOS no Adobe Campaign v8.


>[!TAB Parâmetros de push]

Consulte estas páginas para saber mais sobre parâmetros de push na documentação do Campaign v8:

* [Pré-requisitos de configuração](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#before-starting){target="_blank"}: saiba como definir permissões e configurar seu aplicativo.
* [Configurar a propriedade de inicialização](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#launch-property){target="_blank"}: saiba como configurar uma propriedade de marca móvel na Coleção de dados da Adobe Experience Platform para habilitar notificações por push.
* [Configurar serviços por push para serviços móveis](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#push-service){target="_blank"}: configure os serviços por push da iOS e da Android no Adobe para habilitar notificações por push direcionadas para os usuários do aplicativo móvel.
* [Configurar a extensão na propriedade móvel](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#configure-extension){target="_blank"}: integre a extensão do Campaign à propriedade móvel para habilitar notificações por push e gerenciar interações de usuário com eficiência.

>[!ENDTABS]


As informações a seguir são específicas do Campaign Classic.

+++ **Instalação do pacote**

![](assets/do-not-localize/how-to-video.png) [Saiba como instalar o pacote de aplicativo para dispositivos móveis em vídeo](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=pt-BR#sending-messages)

Como um cliente híbrido/hospedado, entre em contato com a equipe de [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) para acessar o canal de notificação por push no Campaign.

Como cliente local, você precisa instalar um pacote integrado.

>[!CAUTION]
>
>Saiba mais sobre os pacotes integrados do Campaign, as práticas recomendadas e as recomendações [nesta página](../../installation/using/installing-campaign-standard-packages.md).

As etapas de instalação são:

1. Acesse o assistente de importação de pacotes do **[!UICONTROL Tools > Advanced > Import package]** no console do cliente do Adobe Campaign.

   ![](assets/package_ios.png)

1. Selecione **[!UICONTROL Install a standard package]**.

1. Na lista que aparece, marque **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Clique em **[!UICONTROL Next]** e, em seguida, em **[!UICONTROL Start]** para começar a instalação do pacote.

   Depois que os pacotes forem instalados, a barra de progresso mostrará **100%** e você poderá ver a seguinte mensagem nos registros de instalação: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** a janela de instalação.

Quando essa etapa estiver concluída, você poderá configurar seus aplicativos Android e iOS. Consulte a [documentação](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target="_blank"} do Campaign v8.

+++

+++ **Solução de problemas**

Se o dispositivo móvel estiver conectado ao wi-fi e você não estiver recebendo notificações, verifique se as portas FCM/APNS não estão bloqueadas pelo firewall.

**Android**: o dispositivo móvel conecta-se aos servidores FCM nas portas 5228 a 5230. Portanto, você deve configurar o firewall para que ele autorize a conexão com o FCM. As portas que devem ser abertas são: 5228 (a mais usada), 5229 e 5230.

**iOS**:

Conector HTTP/2: é necessário permitir a comunicação de e para os seguintes servidores:

* api.push.apple.com: porta 443
* api.development.push.apple.com: porta 443

>[!NOTE]
>
>Para obter mais informações sobre os dois conectores, consulte a [documentação](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html){target="_blank"} do Campaign v8.

+++
