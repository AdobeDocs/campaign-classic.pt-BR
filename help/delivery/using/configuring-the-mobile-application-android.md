---
product: campaign
title: Configuração do aplicativo móvel Android no Adobe Campaign
description: Saiba como configurar seu aplicativo móvel para Android
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
index: y
internal: n
snippet: y
exl-id: 32c35e61-d0a3-478f-b73b-396e2becf7f9
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 94%

---

# Etapas de configuração para Android

Depois que o pacote for instalado, você poderá definir as configurações do aplicativo Android no Adobe Campaign Classic.

>[!NOTE]
>
>Para saber como configurar seu aplicativo para iOS e como criar um delivery para iOS, consulte esta [seção](configuring-the-mobile-application.md).

As principais etapas são:

1. [Configuração da conta externa do Android](#configuring-external-account-android)
1. [Configuração do serviço Android](#configuring-android-service)
1. [Criação do aplicativo móvel no Campaign](#creating-android-app)
1. [Extensão do esquema do aplicativo com dados adicionais](#extend-subscription-schema)

Você poderá [criar uma notificação avançada do Android](create-notifications-android.md).

## Configurar conta externa do Android {#configuring-external-account-android}

Para Android, dois conectores estão disponíveis:

* O conector V1 que permite uma conexão por MTA filho.
* O conector V2 que permite conexões simultâneas com o servidor FCM para melhorar o throughput.

Para escolher qual conector deseja usar, siga estas etapas:

1. Vá para **[!UICONTROL Administration > Platform > External accounts]**.
1. Selecione a conta externa **[!UICONTROL Android routing]**.
1. Na guia **[!UICONTROL Connector]**, preencha o campo **[!UICONTROL JavaScript used in the connector]**:

   Para Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > Você também pode configurá-lo assim: https://localhost:8080/nms/jsp/androidPushConnector.js, mas recomendamos que você use a versão 2 do conector.

   ![](assets/nmac_connectors3.png)

1. Para Android V2, um parâmetro adicional está disponível no arquivo de configuração do Adobe Server (serverConf.xml):

   * **maxGCMConnectPerChild**: Limite máximo de solicitações HTTP paralelas para o FCM iniciado por cada servidor filho (8 por padrão).

## Configurar um serviço Android {#configuring-android-service}

![](assets/do-not-localize/how-to-video.png) [Saiba como configurar um serviço Android em vídeo](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html?lang=pt-BR#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign)

1. Acesse o nó **[!UICONTROL Profiles and Targets > Services and subscriptions]** e clique em **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Defina um **[!UICONTROL Label]** e um **[!UICONTROL Internal name]**.
1. Acesse o campo **[!UICONTROL Type]** e selecione **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >O target mapping **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** padrão é vinculado à tabela de destinatários. Para utilizar um mapeamento de alvo diferente, é necessário criar um novo e inseri-lo no campo **[!UICONTROL Target mapping]** do serviço. Para obter mais informações sobre como criar o target mapping, consulte [esta seção](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Em seguida, clique no botão **[!UICONTROL Add]** para selecionar o tipo de aplicativo.

   ![](assets/nmac_service_2.png)

1. Crie seu aplicativo Android. Para obter mais informações, consulte [esta seção](configuring-the-mobile-application-android.md#creating-android-app).

## Criar o aplicativo Android para dispositivos móveis {#creating-android-app}

Depois de criar o serviço, é necessário criar o aplicativo Android:

1. Em seu serviço recém-criado, clique no botão **[!UICONTROL Add]** para selecionar o tipo de aplicativo.

   ![](assets/nmac_service_2.png)

1. Selecione **[!UICONTROL Create an Android application]** e insira um **[!UICONTROL Label]**.

   ![](assets/nmac_android.png)

1. Verifique se a mesma **[!UICONTROL Integration key]** está definida no Adobe Campaign e no código do aplicativo por meio do SDK. Para obter mais informações, consulte [esta seção](integrating-campaign-sdk-into-the-mobile-application.md).

   >[!NOTE]
   >
   > O **[!UICONTROL Integration key]** é totalmente personalizável com o valor da string, mas precisa ser exatamente o mesmo especificado no SDK.

1. Selecione o **[!UICONTROL API version]**: HTTP v1 ou HTTP (legado). Essas configurações são detalhadas [nesta seção](#select-api-version)

1. Preencha o campo **[!UICONTROL Firebase Cloud Messaging the Android connection settings]**.

1. Clique em **[!UICONTROL Finish]** e em **[!UICONTROL Save]**. Seu aplicativo Android agora está pronto para ser usado no Campaign Classic.

Por padrão, o Adobe Campaign salva uma chave no campo **[!UICONTROL User identifier]** (@userKey) da tabela **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]**. Essa chave permite vincular uma subscrição a um recipient. Para coletar dados adicionais (como uma chave de reconciliação complexa), é necessário aplicar a seguinte configuração:

### Selecione a versão da API{#select-api-version}

Depois de criar um serviço e um novo aplicativo móvel, é necessário configurar seu aplicativo móvel dependendo da versão da API escolhida.

* **A** configuração HTTP v1 é detalhada  [nesta seção](configuring-the-mobile-application-android.md#android-service-httpv1).
* **A configuração HTTP (herdada)** é detalhada  [nesta seção](configuring-the-mobile-application-android.md#android-service-http).

#### Configurar API HTTP v1{#android-service-httpv1}

Para configurar a versão da API HTTP v1, siga as etapas abaixo:

1. Na janela **[!UICONTROL Mobile application creation wizard]** selecione **[!UICONTROL HTTPV1]** no menu suspenso **[!UICONTROL API version]**.

1. Clique em **[!UICONTROL Load project json file to extract projet details...]** para carregar diretamente o arquivo de chave JSON. Para obter mais informações sobre como extrair o arquivo JSON, consulte [esta página](https://firebase.google.com/docs/admin/setup#initialize-sdk).

   Você também pode inserir manualmente os seguintes detalhes:
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. Clique em **[!UICONTROL Test the connection]** para verificar se a configuração está correta e se o servidor de marketing tem acesso ao FCM.

   >[!CAUTION]
   >
   >Para implantação de mid-sourcing, o botão **[!UICONTROL Test connection]** não verificará se o servidor MID tem acesso ao servidor FCM.

   ![](assets/nmac_android_11.png)

1. Como opção, você pode enriquecer um conteúdo de mensagem de push com alguns **[!UICONTROL Application variables]** se necessário. Eles são totalmente personalizáveis e uma parte da carga da mensagem é enviada para o dispositivo móvel.

1. Clique em **[!UICONTROL Finish]** e em **[!UICONTROL Save]**. Seu aplicativo Android agora está pronto para ser usado no Campaign Classic.

Abaixo estão os nomes de payload do FCM para personalizar ainda mais sua notificação por push:

| Tipo de mensagem | Elemento de mensagem configurável (nome da carga FCM) | Opções configuráveis (nome da carga do FCM) |
|:-:|:-:|:-:|
| mensagem de dados | N/D | validate_only |
| mensagem de notificação | title, body, android_channel_id, icon, sound, tag, color, click_action, image, ticker, sticky, visibility, notification_priority, notification_count <br> | validate_only |

<br>
<br>

#### Configurar API HTTP (legada){#android-service-http}

Para configurar a versão da API HTTP (herdada), siga as etapas abaixo:

1. Na janela **[!UICONTROL Mobile application creation wizard]** selecione **[!UICONTROL HTTP (legacy)]** no menu suspenso **[!UICONTROL API version]**.

1. Digite o **[!UICONTROL Project key]** que foi fornecido pelo desenvolvedor do aplicativo móvel.

1. Como opção, você pode enriquecer um conteúdo de mensagem de push com alguns **[!UICONTROL Application variables]** se necessário. Eles são totalmente personalizáveis e uma parte da carga da mensagem é enviada para o dispositivo móvel.

   No exemplo a seguir, adicionamos **title**, **imageURL** e **iconURL** para criar notificações por push avançadas e, em seguida, fornecemos ao aplicativo a imagem, o título e o ícone que serão exibidos na notificação.

   ![](assets/nmac_android_2.png)

1. Clique em **[!UICONTROL Finish]** e em **[!UICONTROL Save]**. Seu aplicativo Android agora está pronto para ser usado no Campaign Classic.

Abaixo estão os nomes de payload do FCM para personalizar ainda mais sua notificação por push:

| Tipo de mensagem | Elemento de mensagem configurável (nome da carga FCM) | Opções configuráveis (nome da carga do FCM) |
|:-:|:-:|:-:|
| mensagem de dados | N/D | dryRun |
| mensagem de notificação | title, body, android_channel_id, icon, sound, tag, color, click_action <br> | dryRun |

<br>

## Estender o esquema appsubscriptionRcp {#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [Saiba como estender o esquema appsubscriptionRcp em vídeo](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html?lang=pt-BR#extending-the-app-subscription-schema-to-personalize-push-notifications)

É necessário estender o **appsubscriptionRcp** para definir novos campos adicionais para armazenar parâmetros do aplicativo no banco de dados do Campaign. Esses campos serão usados para personalização, por exemplo. Para fazer isso:

1. Crie uma extensão do esquema **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** e defina os novos campos. Saiba mais sobre extensão de esquema [nesta página](../../configuration/using/about-schema-edition.md)

1. Defina o mapeamento na guia **[!UICONTROL Subscription parameters]**.

   >[!CAUTION]
   >
   >Verifique se os nomes da configuração da guia **[!UICONTROL Subscription parameters]** são iguais aos do código do aplicativo móvel. Consulte [esta seção](integrating-campaign-sdk-into-the-mobile-application.md).
