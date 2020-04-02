---
title: Sobre as aplicações web
seo-title: Sobre as aplicações web
description: Sobre as aplicações web
seo-description: null
page-status-flag: never-activated
uuid: acfa6e5e-b503-4a1a-871e-e70007874f57
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 3af763ad-6b0d-4f4c-aed1-c5e12efd4760
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 61c7681535dc08e1d705d7d239e96c603bbad339

---


# Sobre as aplicações web{#about-web-applications}

O Adobe Campaign permite criar e publicar aplicações web dinâmicas e interativas com dados do banco de dados e conteúdo adaptado aos direitos do usuário conectado. É possível criar páginas, como um formulário de edição em uma extranet ou formulários de notificação, incluindo dados do banco de dados com tabelas, gráficos, formulários de entrada, etc. Essa funcionalidade permite criar e publicar páginas da Web em que os usuários podem pesquisar ou inserir informações.

Pode ser um formulário de subscrição contendo dados pré-carregados com informações no banco de dados do Adobe Campaign, como mostrado abaixo:

![](assets/webapp_form_sample.png)

Este capítulo fornece uma visão geral de como gerenciar as aplicações web.

>[!CAUTION]
>
>Por motivos de privacidade, recomendamos usar HTTPS para todos os recursos externos.

## Escopo do aplicativo web {#web-application-scope}

Os aplicativos web no Adobe Campaign oferecem acesso às seguintes funcionalidades:

* Criação de formulários com várias páginas. Para obter mais informações, consulte esta [página](../../web/using/about-web-forms.md).
* Gestão de pesquisa multilíngue com uma ferramenta de tradução integrada. Para obter mais informações, consulte esta [página](../../web/using/translating-a-web-application.md).
* Interface de gestão de página gráfica, layout de página com várias colunas. Para obter mais informações, consulte esta [página](../../web/using/designing-a-web-application.md).
* Personalização de renderização e posição de campo. Para obter mais informações, consulte esta [página](../../web/using/editing-content.md#adding-personalization-content).
* Exibição condicional de campos de pesquisa de acordo com as respostas. Para obter mais informações, consulte esta [página](../../web/using/form-rendering.md#defining-fields-conditional-display).
* Exibição aleatória de perguntas. Para obter mais informações, consulte esta [página](../../web/using/building-a-survey.md#adding-questions).
* Exibição de página condicional. Para obter mais informações, consulte esta [página](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).
* Verificação de informações antes da validação, dependendo do tipo de dados esperado (número, endereço de email, data, etc.) e dos campos obrigatórios. Para obter mais informações, consulte esta [página](../../web/using/form-rendering.md#defining-control-settings).
* Convites ou notificação por email. Para obter mais informações, consulte esta [página](../../web/using/publishing-a-web-form.md#delivering-a-form-via-email).
* Personalização de mensagens de erros e mensagens finais. Para obter mais informações, consulte esta [página](../../web/using/defining-web-forms-properties.md#setting-up-an-error-page).
* Uso de imagens, vídeos, links de hipertexto, captcha, etc. Para obter mais informações, consulte esta [página](../../web/using/editing-content.md).
* Monitoramento de respostas em tempo real. Para obter mais informações, consulte esta [página](../../web/using/publish--track-and-use-collected-data.md#response-tracking).

O módulo de criação **Survey** opcional oferece as seguintes funcionalidades adicionais:

* Extensão dinâmica do banco de dados: criação de respostas não incluídas no template de dados inicial. Para obter mais informações, consulte esta [página](../../web/using/managing-answers.md#storing-collected-answers).
* Geração de relatórios dedicados. Para obter mais informações, consulte esta [página](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys).

Em comparação às aplicações Web, as pesquisas têm uma interface gráfica simplificada com um número reduzido de controles de edição.

>[!NOTE]
>
>As pesquisas estão detalhadas [nesta seção](../../web/using/about-surveys.md).
>
>As funcionalidades gerais de formulários web no Adobe Campaign estão detalhadas [nesta seção](../../web/using/about-web-forms.md).

## Implementação do aplicativo web {#web-application-implementation}

Para criar e publicar uma aplicação web, você deve:

1. Crie o conteúdo (campos, listas, tabelas, gráficos, etc.).

   Você também pode exibir a seção que detalha os campos disponíveis para formulários: todos esses campos também estão disponíveis para aplicações web. Essas informações estão disponíveis [nesta página](../../web/using/adding-fields-to-a-web-form.md).

1. Conforme necessário, você pode adicionar pré-carregamento, testar e salvar etapas e configurar o sistema de controle de acesso (principalmente dentro da estrutura de uma publicação extranet).
1. Publique a aplicação web para torná-la disponível em uma extranet ou no Adobe Campaign.

## Configuração inicial do aplicativo web {#web-application-initial-configuration}

Web application are created via the **[!UICONTROL Web Applications]** link in the **[!UICONTROL Campaigns]** and **[!UICONTROL Profiles and targets]** tabs.

Web applications are stored in the **[!UICONTROL Resources > Online > Web Applications]** node of the Adobe Campaign tree. As configurações estão divididas nas seguintes pastas:

* **[!UICONTROL Administration > Configuration > Form renderings]**: contém os modelos de renderização para a apresentação de formulário da Web (aplicativos e pesquisas). O template permite gerar o formulário. Ele também usa uma folha de estilos CSS. Essa folha de estilos pode ser sobrecarregada no nível do template. Para obter mais informações, consulte [esta página](../../web/using/form-rendering.md#selecting-the-form-rendering-template).
* **[!UICONTROL Resources > Templates > Web application templates]**: contém modelos de formulário. Para criar um formulário ou uma aplicação web, você deve começar em um template.

## Templates de aplicação web {#web-application-templates}

Por padrão, o Adobe Campaign fornece um template por aplicação web disponível.

>[!NOTE]
>
>Você pode converter uma aplicação web existente em um template. Para fazer isso, selecione o formulário e clique com o botão direito do mouse. Select **[!UICONTROL Actions > Save as template...]**.

You can create new templates via the **[!UICONTROL Resources > Templates > Web Application templates]** node of the Adobe Campaign tree.

O assistente de criação permite selecionar as opções que você deseja habilitar, conforme mostrado abaixo.

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>As aplicações disponíveis dependem das opções e dos módulos. Verifique o contrato de licença.

