---
product: campaign
title: Configurar o aplicativo para dispositivos móveis no Adobe Campaign
description: Saiba como iniciar a configuração do aplicativo móvel
feature: Push
role: User, Developer
level: Intermediate, Experienced
hide: true
exl-id: 95bc07cc-8837-4511-81bc-05fad28191c9
TQID: https://experienceleague.adobe.com/cJ0deoAKq2ac-04v87YFRvwx-mqhrHyzQYxGmkvgKiY
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 330
ht-degree: 100%

---

# Introdução à configuração do aplicativo



Encontre abaixo a amostra da configuração com base em uma empresa que vende pacotes de viagem online. Seu aplicativo móvel (Neotrips) está disponível para os clientes em duas versões: Neotrips para Android e Neotrips para iOS.

Para enviar notificações por push no Adobe Campaign, é necessário:

* Criar um serviço de informação do tipo **[!UICONTROL Mobile application]** para o aplicativo para dispositivos móveis Neotrips. Consulte [esta seção para iOS](configuring-the-mobile-application.md#configuring-ios-service). e [esta seção para Android](configuring-the-mobile-application-android.md#configuring-android-service).
* Adicionar as versões iOS e Android do aplicativo a este serviço.
* Criar uma entrega para [iOS](create-notifications-ios.md) e [Android](create-notifications-android.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Acesse a guia **[!UICONTROL Subscriptions]** do serviço para exibir a lista de assinantes do serviço, ou seja, todas as pessoas que instalaram o aplicativo nos próprios celulares e concordaram em receber as notificações.

## Instalar o pacote {#installing-package-ios}

[!BADGE No local e híbrido]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=pt-BR" tooltip="Aplica-se somente a implantações locais e híbridas"}

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

Quando esta etapa for concluída, você poderá configurar seus aplicativos para Android e iOS:
Consulte estas seções:

* [Etapas de configuração para iOS](configuring-the-mobile-application.md)

* [Etapas de configuração para Android](configuring-the-mobile-application-android.md)
