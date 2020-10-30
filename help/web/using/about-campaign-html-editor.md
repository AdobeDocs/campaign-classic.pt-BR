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
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '352'
ht-degree: 100%

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

Para criar uma aplicação web simples, as etapas são estas:

* Crie uma aplicação web. Para obter mais informações, consulte [Criação de uma página inicial](../../web/using/creating-a-landing-page.md),
* Seleção de conteúdo existente ou criação de conteúdo de um template padrão. Para obter mais informações, consulte ](../../web/using/template-management.md)Gerenciamento de modelos[,
* Edite e configure o conteúdo. Para mais informações, consulte [Edição de conteúdo](../../web/using/editing-content.md),
* Publique a aplicação web. Para obter mais informações, consulte [Publicação de conteúdo](../../web/using/creating-a-landing-page.md#step-3---publishing-content) e [esta página](../../web/using/publishing-a-web-form.md#managing-web-forms-delivery-and-tracking).

>[!NOTE]
>
>Para obter um exemplo completo detalhando a implementação do DCE na estrutura de uma aplicação web, consulte [Criação de uma página inicial](../../web/using/creating-a-landing-page.md).

Para criar um delivery de email, as etapas são as seguintes:

* Crie um delivery por meio de um template de tipo de email no qual o DCE esteja ativo,
* Selecione conteúdo existente ou crie conteúdo por meio de um template padrão,
* Edite e configure conteúdo online,
* Envie o delivery. Para obter mais informações, consulte [esta seção](../../delivery/using/steps-about-delivery-creation-steps.md).

>[!NOTE]
>
>Para obter um exemplo completo detalhando a implementação do DCE na estrutura de um delivery de email, consulte [este caso de uso](../../web/using/use-case--creating-an-email-delivery.md).

