---
product: campaign
title: Introdução ao canal de SMS
description: Introdução ao canal de SMS
feature: SMS
role: User
exl-id: 6fc2ab09-8ea7-4865-88ad-bd45eee68958
TQID: https://experienceleague.adobe.com/bk-HUOGv3u60NzOnXD0huo74lBJJuiBOaOJeGmPa2E4
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 484
ht-degree: 100%

---

# Introdução ao canal de SMS{#sms-channel}

Use o Adobe Campaign para enviar mensagens de texto aos seus clientes em seus dispositivos móveis. Você pode criar, personalizar e visualizar mensagens em formato de texto no editor de SMS.

O SMS é um canal direto e altamente eficaz para alcançar usuários onde quer que estejam. Com altas taxas de abertura e entrega quase instantânea, o SMS é ideal para alertas urgentes, atualizações transacionais e mensagens promocionais concisas. Use o SMS para complementar a estratégia entre canais e fornecer comunicação impactante em tempo real. Saiba como configurar e usar o canal de SMS de maneira eficaz na [documentação do Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=pt-BR){target=_blank}.

Como parte da transição do Campaign v7 para o v8, o conjunto de documentações do Campaign Classic foi simplificado e reorganizado. Os recursos comuns agora estão disponíveis apenas no conjunto de documentações do Campaign v8.

>[!BEGINTABS]

>[!TAB Documentação do canal de SMS]

Para saber mais sobre o canal de SMS, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=pt-BR){target=_blank}.


[![imagem](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=pt-BR){target=_blank}


>[!TAB Criação da entrega de SMS]

Conheça as principais etapas relacionadas à criação de entregas de SMS **na documentação do Campaign v8**:

* [Visão geral do canal de SMS](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/sms/sms){target="_blank"}: saiba como enviar mensagens de texto para clientes em seus dispositivos móveis.
* [Criar uma entrega de SMS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/create-sms.html?lang=pt-BR){target="_blank"}: descubra as diferentes etapas necessárias para criar uma nova entrega de SMS.
* [Definir o conteúdo](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/sms-content.html?lang=pt-BR){target="_blank"}: saiba como personalizar o conteúdo de suas mensagens SMS.
* [Selecionar o público-alvo](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/sms-audience.html?lang=pt-BR){target="_blank"}: o destino principal é extraído do banco de dados do Adobe Campaign ou também pode ser armazenado em um arquivo externo.
* [Enviar provas de SMS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/validate-sms/sms-proofs.html?lang=pt-BR): é essencial configurar um ciclo de validação de entrega. Verifique se o conteúdo foi aprovado antes de enviá-lo para o público-alvo.
* [Enviar para o público-alvo](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/validate-sms/sms-send.html?lang=pt-BR): quando o SMS for validado, você poderá enviá-lo para o público-alvo.
* [Monitorar e rastrear um SMS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms-monitor.html?lang=pt-BR): monitore a entrega de SMS para garantir a eficiência de suas campanhas de marketing.


>[!TAB Configurações de SMS]

Consulte estas páginas para saber mais sobre as configurações de SMS. Essas páginas são específicas do Campaign v7.

* [Configuração autônoma](sms-set-up.md): saiba como configurar o canal de SMS em uma instância autônoma.
* [Configuração de mid-sourcing](sms-set-up-mid.md): descubra como enviar para um celular com servidores intermediários.
* [Conector SMS](sms-protocol.md): saiba mais sobre o protocolo e as configurações do conector SMS.
* [Configuração adicional](sms-send.md): saiba mais sobre os parâmetros avançados e outras configurações adicionais.
* [Solução de problemas](troubleshooting-sms.md): listamos uma série de possíveis problemas e suas soluções.

>[!ENDTABS]



<!--
Use Adobe Campaign to send personalized SMS messages.

Before starting sending SMS:

* Make sure recipient profiles contain at least a mobile phone in their profile.
* Learn more about the Adobe Campaign [Delivery best practices](delivery-best-practices.md).

The key steps to send a SMS are as follows:

* [Configure the SMS channel](sms-set-up.md)
* [Create a SMS delivery](sms-create.md)
* [Define the audience](sms-create.md#selecting-the-target-population)
* [Define the SMS content](sms-create.md#defining-the-sms-content)
* [Send, monitor and track SMS](sms-send.md)
* [Troubleshoot](troubleshooting-sms.md)

In addition, you need to be familiar with SMS protocol and settings. Walk through the connection set up between Adobe Campaign and a SMPP provider in [this document](sms-protocol.md)

For global information on how to create a delivery, refer to [this section](steps-about-delivery-creation-steps.md).

>[!NOTE]
>
>Adobe Campaign also lets you submit notifications on mobile terminals, via its **Adobe Campaign Mobile App Channel (NMAC)** option. 
> 
>For more on this, refer to the [Get started with mobile app channel](about-mobile-app-channel.md) section.
-->