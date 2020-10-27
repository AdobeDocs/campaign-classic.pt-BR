---
title: 'Configuração do aplicativo móvel no Adobe Campaign '
description: Saiba como start com a configuração do aplicativo móvel
page-status-flag: never-activated
uuid: aff1a4a0-34e7-4ce0-9eb3-30a8de1380f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 7b5a1ad6-da5a-4cbd-be51-984c07c8d0b3
translation-type: tm+mt
source-git-commit: fd75f7f75e8e77d7228233ea311dd922d100417c
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 57%

---


# Introdução à configuração do aplicativo

Nesta seção, é possível encontrar uma amostra de configuração com base em uma empresa que vende pacotes de feriados online. Seu aplicativo móvel (Neotrips) está disponível para os clientes em duas versões: Neotrips para Android e Neotrips para iOS.

Para enviar notificações por push no Adobe Campaign, é necessário:

* Crie um serviço de informação do tipo **[!UICONTROL Mobile application]** para o aplicativo para dispositivos móveis Neotrips. Consulte [esta seção para iOS](../../delivery/using/configuring-the-mobile-application.md#configuring-ios-service). e [esta seção para Android](../../delivery/using/configuring-the-mobile-application-android.md#configuring-android-service).
* Adicione as versões iOS e Android do aplicativo a este serviço.
* Crie um delivery para iOS e Android. [Consulte esta página](../../delivery/using/creating-notifications.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Acesse a guia **[!UICONTROL Subscriptions]** do serviço para exibir a lista de assinantes do serviço, ou seja, todas as pessoas que instalaram o aplicativo nos próprios celulares e concordaram em receber as notificações.

## Instalação do pacote {#installing-package-ios}

Como cliente híbrido/hospedado, entre em contato com a equipe de Atendimento ao cliente da Adobe para acessar o canal de notificação por push na Campanha.

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
