---
product: campaign
title: Introdução ao canal de aplicativo móvel
description: Introdução ao canal de aplicativo para dispositivos móveis no Adobe Campaign
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: 81b47231b027a189bc8b9029b7d48939734d08ed
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 100%

---

# Introdução ao canal de aplicativo móvel{#about-mobile-app-channel}

O **Canal de aplicativo móvel** permite usar a plataforma do Adobe Campaign para enviar notificações personalizadas para terminais iOS e Android por meio de aplicativos.

Dois canais de entrega estão disponíveis:

* Um canal iOS que permite enviar notificações para dispositivos móveis Apple.

  ![](assets/nmac_intro_2.png)

* Um canal Android que permite enviar mensagens de dados para dispositivos móveis Android.

  ![](assets/nmac_intro_1.png)

  >[!IMPORTANT]
  >
  >Algumas alterações importantes no serviço Firebase Cloud Messaging (FCM) para Android serão lançadas em 2024 e poderão afetar sua implementação do Adobe Campaign. A configuração dos serviços de assinatura para mensagens por push no Android pode precisar ser atualizada para oferecer suporte a essa alteração. É recomendado verificar isso antecipadamente e tomar as devidas ações. Saiba mais nesta [nota técnica do Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=pt-BR){target="_blank"}.

Há duas atividades de entrega nos fluxos de trabalho da campanha que correspondem a esses dois canais. Dois templates de mensagens transacionais também estão disponíveis para o sistema de mensagens transacionais.

![](assets/nmac_intro_3.png)


É possível definir o comportamento do aplicativo para quando o usuário ativar a notificação para exibir a tela correspondente ao contexto do aplicativo. Por exemplo:

* Uma notificação é enviada ao cliente para avisá-lo que seu pacote deixou o depósito. Ativar a notificação abre uma página com informações sobre a entrega.
* O usuário adicionou itens ao carrinho, mas deixou o aplicativo sem concluir a compra. Uma notificação é enviada, informando que o carrinho foi abandonado. Quando ativarem a notificação, o item é exibido na tela.

>[!CAUTION]
>
>* Verifique se as notificações enviadas para um aplicativo para dispositivos móveis estão em conformidade com os pré-requisitos e condições especificados pela Apple (Serviços de Notificação por Push da Apple) e pelo Google (Firebase Cloud Messaging).
>* Aviso: em alguns países, a lei exige que você informe os usuários sobre os tipos de dados coletados nos aplicativos móveis e a finalidade do seu processamento. Você deve verificar a legislação.

O workflow **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt) atualiza a notificação de cancelamentos de subscrições em dispositivos móveis. Para obter mais informações sobre esse fluxo de trabalho, consulte a [lista de workflows técnicos](../../workflow/using/about-technical-workflows.md).

O Adobe Campaign é compatível com APNs HTTP/2. Para obter mais informações sobre as etapas de configuração, consulte [esta seção](configuring-the-mobile-application.md).

Para informações gerais sobre como criar uma entrega, consulte [esta seção](steps-about-delivery-creation-steps.md).


## Configurar canal de notificação por push {#push-notification-configuration}

Para enviar notificações por push com o Adobe Campaign, primeiro você deve configurar o ambiente e o aplicativo. Antes de começar a enviar notificações por push com o Adobe Campaign, certifique-se de que as configurações e integrações estejam definidas no aplicativo móvel e nas tags da Adobe Experience Platform. O SDK móvel da Adobe Experience Platform fornece APIs de integração do lado do cliente para dispositivos móveis por meio de SDKs compatíveis com Android e iOS. A configuração dos SDKs é realizada por meio da interface da coleção de dados para oferecer uma configuração flexível e integrações extensíveis baseadas em regras. Saiba mais na [documentação do Adobe Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/push/push-settings).


## Caminho de dados {#data-path}

Os schemas a seguir detalham as etapas que permitem que um aplicativo móvel troque dados com o Adobe Campaign. Esse processo envolve três entidades:

* o aplicativo móvel
* o serviço de notificação: APNs (Apple Push Notification Service) para Apple e FCM (Firebase Cloud Messaging) para Android
* Adobe Campaign

As três principais etapas do processo de notificação são: registro do aplicativo no Adobe Campaign (coleção de assinaturas), entregas e rastreamento.

### Etapa 1: coleção de subscrição {#step-1--subscription-collection}

O aplicativo móvel é baixado pelo usuário da App Store ou do Google Play. Este aplicativo contém as configurações de conexão (certificado do iOS e chave do projeto para Android) e a chave de integração. Na primeira vez que o aplicativo é aberto, (dependendo da configuração), o usuário pode ser solicitado a inserir informações de registro (@userKey: email ou número de conta por exemplo). Ao mesmo tempo, o aplication solicita ao serviço de notificações para coletar um ID de notificação (ID de envio). Todas essas informações (configurações de conexão, chave de integração, identificador de notificação, userKey) são enviadas ao Adobe Campaign.

![](assets/nmac_register_view.png)

### Etapa 2: entrega {#step-2--delivery}

Os profissionais de marketing miram os assinantes de aplicativos. O processo de entrega envia as configurações de conexão para o serviço de notificação (certificado iOS e chave do projeto para Android), a ID de notificação (ID de envio) e o conteúdo da notificação. O serviço de notificação envia notificações para os terminais de destino.

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
