---
title: Sobre o editor HTML do Campaign
seo-title: Sobre o editor HTML do Campaign
description: Sobre o editor HTML do Campaign
seo-description: null
page-status-flag: never-activated
uuid: 1b1d392d-4f19-4092-b57d-02051a242675
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 1ffe9f58-7258-4794-a314-524065f8a33b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Sobre o editor HTML do Campaign{#about-campaign-html-editor}

O **Editor de conteúdo digital (DCE)** é um editor de conteúdo HTML que permite criar ou modificar facilmente templates ou conteúdo em formato HTML no Adobe Campaign.

O Editor de conteúdo digital permite inserir e formatar elementos de página e associar campos de banco de dados a elementos de uma página HTML. Ele é oferecido por padrão ao criar uma página para uma aplicação web ou está disponível ao criar deliveries com base em um template no qual está ativo.

>[!NOTE]
>
>O DCE só permite que você execute as operações detalhadas nesta seção.
>
>Se quiser adicionar código JavaScript do lado do servidor, é melhor adicioná-lo em blocos de personalização. Para mais informações sobre criação e modificação dos blocos de personalização, consulte [esta página](../../delivery/using/personalization-blocks.md).

>[!CAUTION]
>
>Por motivos de privacidade, recomendamos usar HTTPS para todos os recursos externos.

## Operação geral do Editor de conteúdo {#content-editor-general-operation}

Esta seção apresenta as principais etapas para editar e carregar conteúdo editado com o DCE na estrutura de um aplicação web e no contexto de um delivery.

A operação geral é a seguinte:

![](assets/dce_schema.png)

Para criar um aplicativo Web simples, as etapas são as seguintes:

* Crie um aplicativo da Web, para obter mais informações, consulte [Criação de uma página](../../web/using/creating-a-landing-page.md)de aterrissagem,
* Select existing content or creating content from a standard template, for more on this, refer to [Template management](../../web/using/template-management.md),
* Edite e configure o conteúdo para mais informações, consulte [Edição de conteúdo](../../web/using/editing-content.md),
* Publish the Web application, for more on this, refer to [Publishing content](../../web/using/creating-a-landing-page.md#step-3---publishing-content) and [this page](../../web/using/publishing-a-web-form.md#managing-web-forms-delivery-and-tracking).

>[!NOTE]
>
>For a complete example detailing the implementation of the DCE within the framework of a Web application, refer to [Creating a landing page](../../web/using/creating-a-landing-page.md).

Para criar um delivery de email, as etapas são as seguintes:

* Crie uma entrega a partir de um modelo de tipo de email no qual o DCE está ativo,
* Selecionar conteúdo existente ou criar conteúdo a partir de um modelo padrão,
* Editar e configurar conteúdo online,
* Send the delivery, for more on this refer to [this section](../../delivery/using/communication-channels.md).

>[!NOTE]
>
>For a complete example detailing the implementation of the DCE within the framework of an email delivery, refer to [this use case](../../web/using/use-case--creating-an-email-delivery.md).

