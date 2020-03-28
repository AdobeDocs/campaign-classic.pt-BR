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
translation-type: ht
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

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

* Criação de formulários com várias páginas,
* Gestão de pesquisa multilíngue com uma ferramenta de tradução integrada,
* Interface de gestão de página gráfica, layout de página com várias colunas,
* Personalização de renderização e posição de campo,
* Exibição condicional de campos de pesquisa de acordo com as respostas,
* Exibição aleatória de perguntas,
* Exibição de página condicional,
* Verificação de informações antes da validação, dependendo do tipo de dados esperado (número, endereço de email, data, etc.) e dos campos obrigatórios,
* Convites ou notificação por email,
* Personalização de mensagens de erros e mensagens finais,
* Uso de imagens, vídeos, links de hipertexto, captcha, etc.
* Monitoramento de respostas em tempo real.

O módulo de criação **Survey** opcional oferece as seguintes funcionalidades adicionais:

* Extensão dinâmica do banco de dados: criação de respostas não incluídas no template de dados inicial,
* Geração de relatórios dedicados.

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

Os aplicativos web são criados por meio do link **[!UICONTROL Web Applications]** nas guias **[!UICONTROL Campaigns]** e **[!UICONTROL Profiles and targets]**.

Os aplicativos web são armazenados no nó **[!UICONTROL Resources > Online > Web Applications]** da árvore do Adobe Campaign. As configurações estão divididas nas seguintes pastas:

* **[!UICONTROL Administration > Configuration > Form renderings]**: contém os templates de renderização para a apresentação do formulário Web (aplicativos e pesquisas). O template permite gerar o formulário. Ele também usa uma folha de estilos CSS. Essa folha de estilos pode ser sobrecarregada no nível do template. Para obter mais informações, consulte [esta página](../../web/using/form-rendering.md#selecting-the-form-rendering-template).
* **[!UICONTROL Resources > Templates > Web application templates]**: contém templates de formulário. Para criar um formulário ou uma aplicação web, você deve começar em um template.

## Templates de aplicação web {#web-application-templates}

Por padrão, o Adobe Campaign fornece um template por aplicação web disponível.

>[!NOTE]
>
>Você pode converter uma aplicação web existente em um template. Para fazer isso, selecione o formulário e clique com o botão direito do mouse. Selecione **[!UICONTROL Actions > Save as template...]**.

Você pode criar novos templates no nó **[!UICONTROL Resources > Templates > Web Application templates]** da árvore do Adobe Campaign.

O assistente de criação permite selecionar as opções que você deseja habilitar, conforme mostrado abaixo.

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>As aplicações disponíveis dependem das opções e dos módulos. Verifique o contrato de licença.

