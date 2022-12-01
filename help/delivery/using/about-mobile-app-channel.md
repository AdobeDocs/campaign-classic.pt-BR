---
product: campaign
title: Introdução ao canal de aplicativo para dispositivos móveis
description: Introdução ao canal de aplicativo para dispositivos móveis no Adobe Campaign Classic
feature: Push
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 100%

---

# Introdução ao canal de aplicativo móvel{#about-mobile-app-channel}

![](../../assets/common.svg)

O **Canal de aplicativo móvel** permite usar a plataforma do Adobe Campaign para enviar notificações personalizadas para terminais iOS e Android por meio de aplicativos

>[!CAUTION]
>
>Este documento detalha o processo de integração de seu aplicativo móvel com a plataforma Adobe Campaign. Ele não fornece informações sobre como criar o aplicativo móvel ou como configurá-lo para gerenciar notificações. Se desejar mais informações sobre isso, consulte a [documentação](https://developer.apple.com/) oficial da Apple e a [documentação](https://developer.android.com/index.html) do Android.

Dois canais de delivery estão disponíveis:

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


O workflow **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt) atualiza a notificação de cancelamentos de subscrições em dispositivos móveis. Para obter mais informações sobre esse fluxo de trabalho, consulte a [lista de workflows técnicos](../../workflow/using/about-technical-workflows.md).

O Adobe Campaign é compatível com APNs HTTP/2. Para obter mais informações sobre as etapas de configuração, consulte [esta seção](configuring-the-mobile-application.md).

Para informações gerais sobre como criar um delivery, consulte [esta seção](steps-about-delivery-creation-steps.md).

## Caminho de dados {#data-path}

Os schemas a seguir detalham as etapas que permitem que um aplicativo móvel troque dados com o Adobe Campaign. Esse processo envolve três entidades:

* o aplicativo móvel
* o serviço de notificação: APNs (Apple Push Notification Service) para Apple e FCM (Firebase Cloud Messaging) para Android
* Adobe Campaign

As três principais etapas do processo de notificação são: registro do aplicativo no Adobe Campaign (coleção de assinaturas), deliveries e rastreamento.

### Etapa 1: coleção de subscrição {#step-1--subscription-collection}

O aplicativo móvel é baixado pelo usuário da App Store ou do Google Play. Este aplicativo contém as configurações de conexão (certificado do iOS e chave do projeto para Android) e a chave de integração. Na primeira vez que o aplicativo é aberto, (dependendo da configuração), o usuário pode ser solicitado a inserir informações de registro (@userKey: email ou número de conta por exemplo). Ao mesmo tempo, o aplication solicita ao serviço de notificações para coletar um ID de notificação (ID de envio). Todas essas informações (configurações de conexão, chave de integração, identificador de notificação, userKey) são enviadas ao Adobe Campaign.

![](assets/nmac_register_view.png)

### Etapa 2: entrega {#step-2--delivery}

Os profissionais de marketing miram os assinantes de aplicativos. O processo de delivery envia as configurações de conexão para o serviço de notificação (certificado iOS e chave do projeto para Android), a ID de notificação (ID de envio) e o conteúdo da notificação. O serviço de notificação envia notificações para os terminais de destino.

Estas informações estão disponíveis no Adobe Campaign:

* Somente Android: número de dispositivos que exibem a notificação (impressões)
* Android e iOS: número de cliques na notificação

![](assets/nmac_delivery_view.png)

O servidor do Adobe Campaign deve poder entrar em contato com o servidor de APNs na porta 443 para o conector HTTP/2 do iOS.

Para verificar se funciona corretamente, use os seguintes comandos:

* Para testes:

   ```
   api.development.push.apple.com:443
   ```

* Na produção:

   ```
   api.push.apple.com:443
   ```

Se um conector HTTP/2 do iOS for usado, o MTA e o servidor da web deverão ser capazes de contatar APNs na porta 443.

Se precisar usar o conector HTTP/2 do iOS por meio de um proxy, consulte esta [página](../../installation/using/file-res-management.md#proxy-connection-configuration).
