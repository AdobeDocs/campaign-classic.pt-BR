---
product: campaign
title: Introdução à personalização
description: Saiba como personalizar mensagens e usar conteúdo condicional no Campaign
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Personalization
role: User
exl-id: 555082a2-1b62-4aa4-b80c-77b1a1ef9491
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: ht
source-wordcount: '147'
ht-degree: 100%

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
