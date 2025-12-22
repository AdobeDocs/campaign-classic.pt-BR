---
product: campaign
title: Workspace do Adobe Campaign
description: Saiba como usar e personalizar o workspace do Campaign
feature: Overview
role: Developer
level: Beginner
exl-id: 5f689679-7148-4abd-a9bf-185854c64b13
source-git-commit: 354fc8fd5d030ed88e2b279ba1dd3eaf2f314d53
workflow-type: ht
source-wordcount: '1166'
ht-degree: 100%

---

# Workspace do Adobe Campaign {#adobe-campaign-workspace}

## Explorar a interface do Adobe Campaign {#about-adobe-campaign-interface}

Depois de conectar-se ao banco de dados, você acessará a página inicial do Adobe Campaign. Essa página é o seu painel de controle, sendo composta por links e atalhos que permitem acessar recursos, dependendo da instalação e das configurações gerais da plataforma.

Na seção central da página inicial, você pode usar links para acessar o portal de documentação do Campaign, a comunidade e o site de atendimento ao cliente da Adobe.

![](assets/d_ncs_user_interface_home.png)

![](assets/do-not-localize/how-to-video.png) Conheça o espaço de trabalho do Campaign em [vídeo](#video)

>[!NOTE]
>
>Os recursos do Adobe Campaign disponíveis na instância dependem dos módulos e complementos instalados. Alguns deles também podem não estar disponíveis, dependendo das suas permissões e de configurações específicas.
>
>Antes de instalar qualquer módulo ou add-on, você precisa verificar o contrato de licença ou entrar em contato com o executivo da conta da Adobe.

### Acesso via web e console {#console-and-web-access}

A plataforma do Adobe Campaign pode ser acessada por meio de um console ou por meio de um navegador de Internet. Consulte os navegadores compatíveis na [matriz de compatibilidade](../../rn/using/compatibility-matrix.md#Browsers).

A interface de acesso da web é semelhante à interface do console. Em um navegador, você pode usar os mesmos recursos de navegação e exibição do console, mas é possível executar apenas um conjunto reduzido de ações em campanhas. Por exemplo, é possível visualizar e cancelar campanhas, mas não modificar campanhas. Para um determinado operador, uma campanha será exibida com as seguintes opções no console:

![No painel de uma campanha, o operador pode visualizar e cancelar uma campanha, mas também modificá-la e adicionar entregas, documentos e tarefas a ela.](assets/operation_from_console.png)

Enquanto no acesso pela web, as opções permitirão principalmente a visualização dos seguintes elementos:

![Em um navegador, o mesmo operador só pode visualizar e cancelar a campanha.](assets/operation_from_web.png)

Saiba mais sobre como usar a interface da web na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-create.html?lang=pt-BR#use-the-web-interface-){target=_blank}.

### Idiomas {#languages}

O idioma é selecionado ao instalar a instância do Adobe Campaign Classic.

![](assets/language.png)

Você pode escolher entre estes idiomas:

* Inglês (Reino Unido)
* Inglês (EUA)
* Francês
* Alemão
* Japonês

O idioma escolhido para a instância do Adobe Campaign Classic pode afetar os formatos de data e hora. Para mais informações, consulte a [documentação do Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.

Para obter mais informações sobre como criar uma instância, consulte esta [página](../../installation/using/creating-an-instance-and-logging-on.md).

>[!CAUTION]
>
>O idioma não pode ser alterado após a criação da instância.

## Elementos básicos de navegação {#navigation-basics}

As várias funcionalidades da plataforma são divididas em recursos principais: use os links exibidos na seção superior da interface para acessá-las.

![](assets/overview_home.png)

A lista de recursos principais que você pode acessar depende dos pacotes e dos complementos instalados e dos seus direitos de acesso.

### Procurar páginas {#browsing-pages}

Cada recurso inclui um conjunto de funcionalidades com base nas necessidades relacionadas à tarefa e ao contexto de uso. Por exemplo, o link **[!UICONTROL Profiles and targets]** leva você até listas de destinatários, serviços de assinatura, fluxos de trabalho de segmentação existentes e atalhos para criar esses elementos.

As listas estão disponíveis no link **[!UICONTROL Lists]** na seção à esquerda da interface **[!UICONTROL Profiles and Targets]**.

![](assets/recipient_list_overview.png)

### Usar guias {#using-tabs}

* Quando você clica em um recurso principal ou em um link, a página relevante substitui a página atual. Para voltar à página anterior, clique no botão **[!UICONTROL Back]** na barra de ferramentas. Para retornar à página inicial, clique no botão **[!UICONTROL Home]**.

  ![](assets/d_ncs_user_interface_back_home_buttons.png)

* No caso de um menu ou atalho para uma tela de exibição (como um aplicativo Web, um programa, uma entrega ou um relatório), a página correspondente é exibida em outra guia. Isso permite navegar de uma página para outra usando as guias.

  ![](assets/d_ncs_user_interface_tabs.png)

### Criar um elemento {#creating-an-element}

Cada seção de recurso principal permite procurar entre os elementos disponíveis. Para fazer isso, use os atalhos na seção **[!UICONTROL Browsing]**. O link **[!UICONTROL Other choices]** permite acessar todas as outras páginas, independentemente do ambiente.

Você pode criar um novo elemento (entrega, aplicativo da web, fluxo de trabalho, etc.) usando os atalhos na seção **[!UICONTROL Create]**, à esquerda da tela. Use o botão **[!UICONTROL Create]** acima da lista para adicionar novos elementos a ela.

Por exemplo, na página de entrega, use o botão **[!UICONTROL Create]** para criar uma nova entrega.

![](assets/d_ncs_user_interface_tab_add_del.png)


## Usar o explorer do Adobe Campaign {#using-adobe-campaign-explorer}

O explorer do Adobe Campaign é acessível por meio do ícone da barra de ferramentas. Ele permite acessar todos os recursos do Adobe Campaign, as telas de configuração e uma exibição mais detalhada de alguns dos elementos da plataforma.

Para saber mais sobre o explorador do Adobe Campaign, consulte estas páginas na **documentação do Campaign v8 (console)**:

* [Visão geral da interface do usuário do Campaign](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}

* [Configurações da IU do Campaign](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/config/configuration/ui-settings){target=_blank}

* [Gerenciar pastas e visualizações no explorer](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/config/configuration/folders-and-views){target=_blank}


## Trabalhar com dados {#work-with-data}

### Filtrar dados {#filters}

A filtragem de dados é o processo de restringir um conjunto de dados somente aos registros que correspondam a critérios específicos. Esse subconjunto pode ser usado para ações direcionadas (como atualizações ou criação de públicos-alvo) ou para análise.

Ao navegar pelo Campaign, os dados são exibidos em listas. Aplique filtros integrados para acessar rapidamente um subconjunto definido, como endereços em quarentena, destinatários não direcionados ou registros dentro de uma faixa etária ou com uma data de criação específica. Além disso, você pode criar filtros personalizados, salvá-los para uso futuro e compartilhá-los com outros usuários do Campaign.

Saiba como **acessar, criar e compartilhar filtros** na [documentação do Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/audience/create-filters){target=_blank}.

### Consultar o banco de dados{#about-queries-in-campaign}

A ferramenta de consulta está disponível em vários níveis do aplicativo e pode ser usada para definir as populações do público-alvo, segmentar clientes, extrair e filtrar logs de rastreamento, criar filtros e muito mais.

+++Sobre o editor de consultas genérico

Ela fornece um assistente dedicado, o editor de consulta genérica, acessível pelo menu **[!UICONTROL Tools > Generic query editor...]**. Esse editor permite que as consultas a banco de dados extraiam, organizem, agrupem e ordenem informações. Por exemplo, ele pode recuperar destinatários que clicaram mais de n vezes em um link de boletim informativo durante um determinado período.

O editor de query genérico centraliza todos os recursos de consulta. Ele permite criar e armazenar filtros de restrição, que podem ser reutilizados em outros contextos, como a caixa de consulta de um fluxo de trabalho de direcionamento.

![Acessar o editor de consultas e selecionar uma tabela](assets/query_editor_nveau_21.png)

+++

>[!BEGINTABS]

>[!TAB Consultar o banco de dados]

As etapas para criar uma consulta estão detalhadas na **[documentação do Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/data/query/query-editor){target=_blank}**


[![imagem](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/data/query/query-editor){target=_blank}


>[!TAB Adicionar uma consulta a um fluxo de trabalho]

Saiba mais sobre as principais etapas relacionadas à criação de consultas no contexto de um fluxo de trabalho na **[documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/automation/workflows/wf-activities/targeting-activities/query){target=_blank}**

[![imagem](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/pt-br/docs/campaign/automation/workflows/wf-activities/targeting-activities/query){target=_blank}

>[!TAB Condições de filtragem]

Para criar a sua consulta, você precisa selecionar as condições de filtragem no editor de consultas. Os recursos e casos de uso disponíveis estão detalhados na **[documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/data/query/filter-conditions){target=_blank}**

[![imagem](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/data/query/filter-conditions){target=_blank}

>[!ENDTABS]

### Gerenciar listas {#manage-and-customize-lists}

No console do cliente do Campaign, os dados são exibidos em listas. Você pode adaptar essas listas às suas necessidades. Por exemplo, é possível adicionar colunas, filtrar dados, contar registros, salvar e compartilhar suas configurações.

Saiba como **gerenciar e personalizar listas** na [documentação do Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/config/configuration/ui-settings#customize-lists){target=_blank}.

### Gerenciar enumerações{#managing-enumerations}

Uma enumeração (também chamada de lista discriminada) é uma lista predefinida de valores que você pode usar para preencher determinados campos. As enumerações ajudam a padronizar valores de campos, tornando a inserção de dados mais consistente e simplificando as consultas.

Quando definidos, os valores são exibidos em uma lista suspensa. Um valor pode ser selecionado diretamente ou inserido por meio da inserção preditiva, que sugere e conclui as inserções correspondentes. Alguns campos incluem enumerações predefinidas, e enumerações adicionais podem ser criadas, se necessário.

Saiba como **trabalhar com enumerações** na [documentação do Adobe Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}.

## Tutorial em vídeo {#video}

Este vídeo apresenta o espaço de trabalho do Campaign Classic.

>[!VIDEO](https://video.tv.adobe.com/v/39535?captions=por_br&quality=12)
