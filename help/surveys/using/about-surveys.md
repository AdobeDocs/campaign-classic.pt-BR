---
product: campaign
title: Introdução às pesquisas
description: Introdução às pesquisas do Campaign
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 86963746d3de3396963d221ddbd1ef7d89733d2f
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 48%

---

# Introdução às pesquisas{#about-surveys}

O Adobe Campaign inclui um módulo gráfico para definir e publicar aplicações Web. Isso é usado para criar páginas, como um formulário de edição em uma extranet ou formulários de notificação, incluindo dados do banco de dados com tabelas, gráficos, formulários de entrada, etc. Use esse recurso para criar e publicar páginas da Web nas quais os usuários possam pesquisar ou inserir informações.

O complemento opcional **Survey** permite criar um novo tipo de aplicação web para criar e gerenciar questionários online, como formulários para adicionar ou modificar informações de perfil, para subscrever-se ou cancelar a subscrição de um serviço de informação ou um formulário de entrada de competição. Depois que as respostas forem coletadas, elas serão armazenadas no banco de dados ou em variáveis locais. O modelo de dados pode ser estendido dinamicamente através das respostas dos questionários. Você pode exibir os resultados em tempo real, filtrar as respostas e analisá-las usando gráficos dedicados.

Este capítulo detalha como criar e gerenciar **Pesquisas**, gerenciamento de campo e página, modos de armazenamento e registros.

[!DNL :bulb:] Saiba como criar sua primeira pesquisa  [nesta página](getting-started-with-surveys.md).

>[!NOTE]
>
>* As etapas detalhadas para criar um formulário Web padrão estão disponíveis em [este documento](../../web/using/about-web-forms.md).
   >
   >
* O gerenciamento de aplicações web é detalhado em [this document](../../web/using/about-web-applications.md). Consulte este capítulo para obter mais informações.


## Escopo do recurso {#campaign-surveys-scope}

No Adobe Campaign, use [Aplicações Web](../../web/using/about-web-forms.md) para:

* Criar formulários de várias páginas,
* Gerencie formulários multilíngues com uma ferramenta de tradução integrada,
* Gerenciar interface gráfica, layout de página com várias colunas,
* Adicionar personalização e definir a posição do campo,
* Exibição da condição de campos de pesquisa de acordo com as respostas,
* Exibição da página de condição,
* Verifique as informações antes da aprovação, dependendo do tipo de dados esperado (número, endereço de email, datas, etc.) e campos obrigatórios,
* Enviar convites/notificações por email,
* Personalizar páginas de erros e páginas finais,
* Adicione imagens, vídeos, links de hipertexto, captcha, etc., em formulários

O módulo de criação de pesquisa opcional oferece uma interface de usuário fácil de usar e as seguintes funcionalidades adicionais:

* Extensão dinâmica do banco de dados: criação de respostas que não fazem parte do modelo de dados inicial. [Saiba mais](../../surveys/using/managing-answers.md#storing-collected-answers).
* Gestão de pontuação. [Saiba mais](../../surveys/using/managing-answers.md#score-management).
* Exibição aleatória de perguntas. [Saiba mais](../../surveys/using/building-a-survey.md#adding-questions).
* Acompanhamento das respostas em tempo real. [Saiba mais](../../surveys/using/publish--track-and-use-collected-data.md#response-tracking).
* Geração de relatórios dedicados. [Saiba mais](../../surveys/using/publish--track-and-use-collected-data.md#reports-on-surveys).


## Etapas de implementação {#surveys-implementation-steps}

Siga as etapas abaixo para criar e entregar uma pesquisa e processar seus resultados:

1. Crie as páginas da pesquisa e seu conteúdo (campos de entrada, listas suspensas, perguntas e etc.).
1. Defina como as respostas serão salvas. Uma etapa de pré-carregamento de dados pode ser inserida para pré-carregar o formulário com dados já existentes no banco de dados. Você também pode adicionar uma caixa de teste.
1. Publicar e, em seguida, enviar a pesquisa aos destinatários (por exemplo, incluir link em um delivery ou em um site).
1. Monitore as respostas e visualize os relatórios.

Para obter mais informações sobre configuração e sequenciamento dessas etapas, consulte [este documento](../../web/using/about-web-forms.md). Neste capítulo são detalhadas somente as configurações específicas para pesquisas.

>[!CAUTION]
>
>Por motivos de privacidade, recomendamos usar HTTPS para todos os recursos externos.

## Configurações {#settings}

Por padrão, as pesquisas estão disponíveis no nó **[!UICONTROL Resources > Online > Web Applications]** da árvore do Adobe Campaign.

As configurações são armazenadas nas seguintes pastas:

* **[!UICONTROL Administration > Configuration > Form rendering]**: contém os templates de renderização para a apresentação de formulários web (aplicações e pesquisas).
* **[!UICONTROL Resources > Templates > Web application templates]**: contém templates de formulário. Para criar um formulário, você precisa começar com um template.

>[!NOTE]
>
>Os detalhes das configurações estão disponíveis em [this document](../../web/using/about-web-forms.md).
