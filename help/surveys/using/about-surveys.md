---
product: campaign
title: Introdução às pesquisas
description: Introdução às pesquisas do Campaign
feature: Surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 1f80c9967f4859f26dd2890d657f95ada6cf2087
workflow-type: ht
source-wordcount: '522'
ht-degree: 100%

---

# Introdução às pesquisas{#about-surveys}

![](../../assets/common.svg)

O Adobe Campaign inclui um módulo gráfico para definir e publicar aplicativos Web. Isso é usado para criar páginas, como um formulário de edição em uma extranet ou formulários de notificação, incluindo dados do banco de dados com tabelas, gráficos, formulários de entrada etc. Use esse recurso para criar e publicar páginas da Web nas quais os usuários possam pesquisar ou inserir informações.

O add-on opcional de **Pesquisa** permite desenvolver um novo tipo de aplicativo Web para criar e gerenciar questionários online, como formulários para adicionar ou modificar informações de perfil, para assinar ou cancelar a inscrição de um serviço de informação ou um formulário de entrada em competição. Depois que as respostas forem coletadas, elas serão armazenadas no banco de dados ou em variáveis locais. O modelo de dados pode ser estendido dinamicamente através das respostas dos questionários. Você pode exibir os resultados em tempo real, filtrar as respostas e analisá-las usando gráficos dedicados.

Este capítulo detalha como criar e gerenciar **Pesquisas**, gerenciamento de campos e páginas, modos de armazenamento e registros.

Saiba como criar sua primeira pesquisa [nesta página](getting-started-with-surveys.md).

>[!NOTE]
>
>* As etapas para criar um formulário Web padrão estão disponíveis, em detalhes, [neste documento](../../web/using/about-web-forms.md).
>
>* O gerenciamento de aplicativos Web é detalhado [neste documento](../../web/using/about-web-applications.md). Consulte este capítulo para obter mais informações.


## Escopo do recurso {#campaign-surveys-scope}

No Adobe Campaign, use as [aplicativos Web](../../web/using/about-web-forms.md) para:

* Criar formulários de várias páginas,
* Gerenciar formulários multilíngues com uma ferramenta de tradução integrada,
* Gerenciar interface gráfica, layout de página com várias colunas,
* Personalizar e definir a posição do campo,
* Exibição condicional de campos de pesquisa de acordo com as respostas,
* Exibição de página condicional,
* Informações de verificação antes da aprovação, dependendo do tipo de dados esperado (número, endereço de email, datas etc.) e campos obrigatórios,
* Enviar convites/notificações por email,
* Personalizar páginas de erros e páginas finais,
* Adicionar imagens, vídeos, links de hipertexto, captcha etc. a formulários

O módulo de criação de pesquisa opcional oferece uma interface fácil de usar e as seguintes funcionalidades adicionais:

* Extensão dinâmica do banco de dados: criação de respostas que não fazem parte do modelo de dados inicial. [Saiba mais](../../surveys/using/managing-answers.md#storing-collected-answers).
* Gerenciamento de pontuação. [Saiba mais](../../surveys/using/managing-answers.md#score-management).
* Exibição aleatória de perguntas. [Saiba mais](../../surveys/using/building-a-survey.md#adding-questions).
* Rastreamento das respostas em tempo real. [Saiba mais](../../surveys/using/publish--track-and-use-collected-data.md#response-tracking).
* Geração de relatórios dedicados. [Saiba mais](../../surveys/using/publish--track-and-use-collected-data.md#reports-on-surveys).


## Etapas de implementação {#surveys-implementation-steps}

Siga as etapas abaixo para criar e entregar uma pesquisa e processar seus resultados:

1. Crie as páginas da pesquisa e seu conteúdo (campos de entrada, listas suspensas, perguntas e etc.).
1. Definição de como as respostas devem ser salvas. Uma etapa de pré-carregamento de dados pode ser inserida para pré-carregar o formulário com dados já existentes no banco de dados. Você também pode adicionar uma caixa de teste.
1. Publicar e, em seguida, enviar a pesquisa aos destinatários (por exemplo, incluir link em um delivery ou em um site).
1. Monitore as respostas e visualize os relatórios.

Para obter mais informações sobre configuração e sequenciamento dessas etapas, consulte [este documento](../../web/using/about-web-forms.md). Neste capítulo, são detalhadas somente as configurações específicas para pesquisas.

>[!CAUTION]
>
>Por motivos de privacidade, recomendamos usar HTTPS para todos os recursos externos.

## Configurações {#settings}

Por padrão, as pesquisas ficam disponíveis no nó **[!UICONTROL Resources > Online > Web Applications]** da árvore do Adobe Campaign.

As configurações são armazenadas nas seguintes pastas:

* **[!UICONTROL Administration > Configuration > Form rendering]**: contém os templates de renderização para a apresentação de formulários web (aplicações e pesquisas).
* **[!UICONTROL Resources > Templates > Web application templates]**: contém templates de formulário. Para criar um formulário, você precisa começar com um modelo.

>[!NOTE]
>
>Os detalhes das configurações estão disponíveis [neste documento](../../web/using/about-web-forms.md).
