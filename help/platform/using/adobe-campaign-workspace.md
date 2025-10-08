---
product: campaign
title: Workspace do Adobe Campaign
description: Saiba como usar e personalizar o workspace do Campaign
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 5f689679-7148-4abd-a9bf-185854c64b13
source-git-commit: 0db6f107d2c161b07f42dcf7a932d319130b31e0
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 92%

---

# Workspace do Adobe Campaign{#adobe-campaign-workspace}

## Explorar a interface do Adobe Campaign {#about-adobe-campaign-interface}

Depois de se conectar ao banco de dados, você acessará a home page do Adobe Campaign, um painel de controle formado por links e atalhos que permitem acessar recursos, dependendo da sua instalação, bem como as configurações gerais da plataforma.

Na seção central da home page, você pode usar links para acessar o portal de documentação on-line do Campaign, o fórum e o site de suporte.

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

Saiba mais sobre o [uso da interface web](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

### Idiomas {#languages}

O idioma é selecionado ao instalar a instância do Adobe Campaign Classic.

![](assets/language.png)

Você pode escolher entre cinco idiomas diferentes:

* Inglês (Reino Unido)
* Inglês (EUA)
* Francês
* Alemão
* Japonês

O idioma escolhido para a instância do Adobe Campaign Classic pode afetar os formatos de data e hora. Para obter mais informações, consulte a [documentação do Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.

Para obter mais informações sobre como criar uma instância, consulte esta [página](../../installation/using/creating-an-instance-and-logging-on.md).

>[!CAUTION]
>
>O idioma não pode ser alterado após a criação da instância.

## Elementos básicos de navegação {#navigation-basics}

### Procurar páginas {#browsing-pages}

As várias funcionalidades da plataforma são divididas em recursos principais: use os links exibidos na seção superior da interface para acessá-las.

![](assets/overview_home.png)

A lista de recursos principais que você pode acessar depende dos pacotes e dos complementos instalados e dos seus direitos de acesso.

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

O explorer do Adobe Campaign é acessível por meio do ícone da barra de ferramentas. Ele permite que você acesse todos os recursos do Adobe Campaign, as telas de configuração e uma visão mais detalhada de alguns dos elementos da plataforma.

Para saber mais sobre o explorador do Adobe Campaign, consulte estas páginas na documentação do Campaign v8 (console):

* [Visão geral da interface do usuário do Campaign](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/new/campaign-ui#ac-explorer-ui){target=_blank}

* [Configurações da interface do Campaign](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/config/configuration/ui-settings){target=_blank}

* [Gerenciar pastas e modos de exibição no explorador](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/config/configuration/folders-and-views){target=_blank}.


## Trabalhar com listas {#manage-and-customize-lists}

No console do cliente do Campaign, os dados são exibidos em listas. Você pode adaptar essas listas às suas necessidades. Por exemplo, é possível adicionar colunas, filtrar dados, contar registros, salvar e compartilhar suas configurações.

>[!NOTE]
>
>Para saber como gerenciar e personalizar listas no Adobe Campaign, consulte a [documentação do Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/config/configuration/ui-settings#customize-lists){target=_blank}.

## Gerenciar enumerações{#managing-enumerations}

Uma enumeração (também chamada de lista discriminada) é uma lista predefinida de valores que você pode usar para preencher determinados campos. As enumerações ajudam a padronizar valores de campos, tornando a inserção de dados mais consistente e simplificando as consultas.

Quando definidos, os valores são exibidos em uma lista suspensa. Um valor pode ser selecionado diretamente ou inserido por meio da inserção preditiva, que sugere e conclui as inserções correspondentes. Alguns campos incluem enumerações predefinidas, e enumerações adicionais podem ser criadas, se necessário.

Saiba como **trabalhar com enumerações** na [documentação do Adobe Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}.

## Tutorial em vídeo {#video}

Este vídeo apresenta o espaço de trabalho do Campaign Classic.

>[!VIDEO](https://video.tv.adobe.com/v/39535?quality=12&captions=por_br)
