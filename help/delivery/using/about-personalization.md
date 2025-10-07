---
product: campaign
title: Introdução à personalização
description: Saiba como personalizar mensagens e usar conteúdo condicional no Campaign
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Personalization
role: User
exl-id: 555082a2-1b62-4aa4-b80c-77b1a1ef9491
source-git-commit: a1e9fec0e9c85bf25b79e24a7432dfb45bd1a0cb
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 81%

---

# Introdução à personalização{#about-personalization}

As mensagens entregues pelo Adobe Campaign podem ser personalizadas de várias maneiras diferentes, relacionadas ao conteúdo ou à aparência das mensagens. Essas maneiras podem ser combinadas de acordo com os critérios obtidos especialmente dos perfis do destinatário. Para entregas de email, você pode definir os elementos e as condições de personalização de uma entrega diretamente em JavaScript na guia **[!UICONTROL Source]** da mensagem. Em geral, o Adobe Campaign permite:

* Personalizar o formato da mensagem. Consulte [Conteúdo da mensagem](defining-the-email-content.md#message-content).
* Inserir campos de personalização dinâmicos. Consulte [Campos de personalização](personalization-fields.md).
* Inserir blocos de personalização predefinidos. Consulte [Blocos de personalização](personalization-blocks.md).
* Criar conteúdo condicional. Consulte a seção [Conteúdo condicional](conditional-content.md).

>[!CAUTION]
>
>As variáveis a seguir são variáveis internas que podem ser usadas para personalização, mas não devem ser modificadas: **delivery**, **message**, **dataSource**, **targetData**, **provider**, **coupon**, **couponValue** e **proposition**.


Com o Adobe Campaign, personalize seus deliveries para enviar mensagens que correspondam ao perfil e aos interesses de cada recipient.

O Personalization ajuda a tornar suas mensagens mais relevantes e envolventes. Você pode usar os dados do recipient para adaptar o conteúdo, adicionar campos dinâmicos ou exibir informações diferentes com base em condições. Saiba como configurar e usar recursos de personalização em suas entregas na [documentação do Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=pt-BR){target=_blank}.

Como parte da iniciativa de promoção do Campaign v8, a documentação do Campaign Classic foi reorganizada. Os recursos comuns agora estão disponíveis apenas no conjunto de documentações do Campaign v8.

>[!BEGINTABS]

>[!TAB Documentação de personalização de conteúdo]

Para saber mais sobre a personalização de conteúdo, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=pt-BR){target=_blank}.


[![imagem](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=pt-BR){target=_blank}


>[!TAB Criação de entregas por email]

Conheça as principais etapas relacionadas à criação de entregas de email na documentação do Campaign v8:

* [Criar uma entrega de email](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email.html?lang=pt-BR){target="_blank"}: saiba mais sobre as diferentes etapas necessárias para criar uma entrega de email.
* [Definir o conteúdo do email](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=pt-BR){target="_blank"}: defina o que o email incluirá: remetente, assunto, conteúdo, imagens.
* [Definir conteúdo interativo](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-interactive-content.html?lang=pt-BR){target="_blank"}: use o formato interativo AMP for Email para enviar emails dinâmicos.
* [Enviar emails em dispositivos móveis japoneses](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/sending-emails-on-japanese-mobiles.html?lang=pt-BR){target="_blank"}: use um dos três formatos em japonês específicos para email em dispositivos móveis.
* [Anexar arquivos a um email](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/attaching-files.html?lang=pt-BR){target="_blank"}: conheça as diferentes maneiras de anexar um ou mais arquivos a um email.


>[!TAB Parâmetros de email]

Consulte estas páginas para saber mais sobre parâmetros de email na documentação do Campaign v8:

* [Link para a mirror page](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/mirror-page.html?lang=pt-BR){target="_blank"}: configure a mirror page para garantir que seus clientes sempre tenham a melhor experiência de renderização.
* [Adicionar um endereço com CCO](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-bcc.html?lang=pt-BR){target="_blank"}: configure o Adobe Campaign para manter uma cópia dos emails enviados da sua plataforma.
* [Definir parâmetros de email adicionais](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-parameters.html?lang=pt-BR){target="_blank"}: saiba mais sobre as opções e os parâmetros disponíveis nas propriedades de entrega.

Consulte também esta [página](sending-with-enhanced-mta.md) para saber mais sobre o MTA aprimorado.

>[!ENDTABS]





<!--
Adobe Campaign lets you mass deliver personalized electronic messages to a target population.

Before starting sending emails:

* Make sure recipient profiles contain at least an email address.
* Learn more about the Adobe Campaign [Delivery best practices](delivery-best-practices.md).
* Read out these sections to learn more about Deliverability: [Deliverability management in Campaign](about-deliverability.md) and [Deliverability best practices guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=pt-BR).

The key steps to send an email are as follows:

* [Create an email delivery](creating-an-email-delivery.md)
* [Define the target population](steps-defining-the-target-population.md)
* [Define the email content](defining-the-email-content.md)
* [Send the email](sending-messages.md)
* [Monitor the delivery](about-delivery-monitoring.md)

The sections below provide information that is specific to the email channel. For global information on how to create a delivery, refer to [this section](steps-about-delivery-creation-steps.md).
-->