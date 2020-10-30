---
title: Sobre pesquisas
seo-title: Sobre pesquisas
description: Sobre pesquisas
seo-description: null
page-status-flag: never-activated
uuid: 31a07a48-2ebb-4b51-ae24-382f3ce3f04a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: ef7d9b16-506a-409c-a578-000b88cd17a2
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '586'
ht-degree: 100%

---


# Sobre pesquisas{#about-surveys}

O Adobe Campaign inclui um módulo gráfico para definir e publicar aplicações Web. Ele é usado para criar páginas, como um formulário de edição em uma extranet ou formulários de notificação, incluindo dados do banco de dados com tabelas, gráficos, formulários de entrada, etc. Essa funcionalidade permite criar e publicar páginas da Web em que os usuários podem pesquisar ou inserir informações.

O módulo opcional de **Pesquisa** permite criar um novo tipo de aplicação Web para criar e gerenciar questionários online, como formulários para adicionar ou modificar informações de perfil, para subscrever-se ou cancelar a subscrição de um serviço de informação ou um formulário de entrada de competição. Depois que as respostas forem coletadas, elas serão armazenadas no banco de dados ou em variáveis locais. O modelo de dados pode ser estendido dinamicamente através das respostas dos questionários. Você pode exibir os resultados em tempo real, filtrar as respostas e analisá-las usando gráficos dedicados.

Este capítulo detalha o método de criação e gestão de **Pesquisas**, de campo e de páginas, modos de armazenamento e registros.

As etapas para criar um formulário Web padrão são detalhadas [nesta seção](../../web/using/about-web-forms.md).

A gestão de aplicações Web é detalhada [nesta seção](../../web/using/about-web-applications.md). Consulte este capítulo para obter mais informações.

>[!CAUTION]
>
>Por motivos de privacidade, recomendamos usar HTTPS para todos os recursos externos.

## Escopo das pesquisas do Campaign{#campaign-surveys-scope}

No Adobe Campaign, aplicações Web em geral permitem acessar as seguintes funcionalidades:

* Criação de formulários com várias páginas,
* Gestão de pesquisa multilíngue com uma ferramenta de tradução integrada,
* Interface de gestão de página gráfica, layout de página com várias colunas,
* Personalização de renderização e posição de campo,
* Exibição condicional de campos de pesquisa de acordo com as respostas,
* Exibição de página condicional,
* Informações de verificação antes da aprovação, dependendo do tipo de dados esperado (número, endereço de email, datas, etc.) e campos obrigatórios,
* Notificações/convites por email,
* Personalização de mensagens de erros e mensagens finais,
* Uso de imagens, vídeos, links de hipertexto, captcha, etc.

>[!NOTE]
>
>Todas as configurações vinculadas aos formulários Web são detalhadas [nesta seção](../../web/using/about-web-forms.md). Consulte este documento para obter detalhes sobre conceitos e funcionalidades de formulários Web usando o Adobe Campaign.

O módulo de criação de pesquisa opcional (**Pesquisa**) oferece as seguintes funcionalidades adicionais:

* Extensão dinâmica do banco de dados: criação de respostas que não fazem parte do modelo de dados inicial. Para obter mais informações, consulte [Armazenamento de respostas coletadas](../../web/using/managing-answers.md#storing-collected-answers).
* Gestão de pontuação. Para obter mais informações, consulte [Gestão de pontuação](../../web/using/managing-answers.md#score-management).
* Exibição aleatória de perguntas. Para obter mais informações, consulte [Adicionar questões](../../web/using/building-a-survey.md#adding-questions).
* Acompanhamento das respostas em tempo real. Para obter mais informações, consulte [Rastreamento de respostas](../../web/using/publish--track-and-use-collected-data.md#response-tracking).
* Geração de relatórios dedicados. Para obter mais informações, consulte [Relatórios de pesquisa](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys).

Em comparação às aplicações Web, as pesquisas têm uma interface gráfica simplificada com um número reduzido de controles de edição.

## Etapas de implementação de pesquisas {#surveys-implementation-steps}

Siga as etapas abaixo para criar e entregar uma pesquisa e processar seus resultados:

1. Crie as páginas da pesquisa e seu conteúdo (campos de entrada, listas suspensas, perguntas e etc.).
1. Defina como as respostas serão salvas.

   Uma etapa de pré-carregamento de dados pode ser inserida para pré-carregar o formulário com dados já existentes no banco de dados. Você também pode adicionar uma caixa de teste.

1. Publicar e, em seguida, enviar a pesquisa aos destinatários (por exemplo, incluir link em um delivery ou em um site).
1. Monitore as respostas e visualize os relatórios.

Para obter mais informações sobre configuração e sequenciamento dessas etapas, consulte [esta seção](../../web/using/about-web-forms.md). Neste capítulo são detalhadas somente as configurações específicas para pesquisas.

## Configuração de pesquisas {#surveys-configuration}

As pesquisas são armazenadas no nó **[!UICONTROL Resources > Online > Web Applications]** da árvore do Adobe Campaign. As configurações são encontradas nas seguintes pastas:

* **[!UICONTROL Administration > Configuration > Form rendering]**: contém os templates de renderização para a apresentação de formulários web (aplicações e pesquisas).
* **[!UICONTROL Resources > Templates > Web application templates]**: contém templates de formulário. Para criar um formulário, você precisa começar com um template.

>[!NOTE]
>
>As informações de configuração estão disponíveis [nesta seção](../../web/using/about-web-forms.md).

