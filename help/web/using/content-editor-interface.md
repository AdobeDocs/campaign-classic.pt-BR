---
title: Interface do editor de conteúdo
seo-title: Interface do editor de conteúdo
description: Interface do editor de conteúdo
seo-description: null
page-status-flag: never-activated
uuid: b108ea74-ae2c-4e47-bee8-12070927ba89
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
dc-title: </strong> and
discoiquuid: 20c64d31-c2ed-4bc9-9f0e-46f2e0c08c88
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 707352334144df86ae82aa51d595ae6bc751d1f2

---


# Interface do editor de conteúdo{#content-editor-interface}

## Janela de edição {#editing-window}

A janela de edição do DCE está dividida em três seções diferentes. Elas permitem visualizar, modificar e verificar o status do conteúdo.

![](assets/dce_decoupe_window_nb.png)

1. A seção **superior** é uma área de exibição para mensagens do usuário. Essas mensagens indicam o status da aplicação web ou o delivery sendo criado, bem como avisos e mensagens de erro relacionadas ao conteúdo. Para obter mais informações, consulte os status [de conteúdo](../../web/using/content-editing-best-practices.md#html-content-statuses)HTML.
1. A seção à **esquerda** da janela é a área para edição de conteúdo. Nessa área, o usuário pode interagir diretamente com o conteúdo usando a barra de ferramentas pop-up: insira um link em uma imagem, altere a fonte, exclua um campo etc. For more on this refer to [Editing forms](../../web/using/editing-content.md#editing-forms).
1. A seção à **direita** da janela é a área do painel de controle. Essa área agrupa as diferentes opções para o editor, especialmente aquelas relacionadas à configuração do cabeçalho da página e as opções gerais para um bloco: adicionar uma borda, vincular um campo de banco de dados a uma zona de entrada, acessar as propriedades da página da Web etc. Para obter mais informações, consulte as opções [](#global-options) Globais e [Edição de conteúdo](../../web/using/editing-content.md) .

## Opções globais {#global-options}

A seção superior direita do editor permite que você acesse opções globais que possibilitam controlar o conteúdo que está sendo criado no momento.

![](assets/dce_global_options.png)

Ela tem quatro ícones:

![](assets/dce_icons_sidebar.png)

* The **Display/Hide blocks** icon lets you display blue frames around the content blocks (corresponding to the `<div>` HTML tag).

* O ícone **Escolher outro conteúdo** permite que o usuário carregue o novo conteúdo de um template (template existente ou template pronto para uso).

   ![](assets/dce_popup_templatechoice.png)

   >[!CAUTION]
   >
   >O conteúdo selecionado substitui o conteúdo atual.

* O ícone **Salvar como template** permite salvar o conteúdo atual como template. Você deve inserir o rótulo e o nome interno do template. Os modelos são armazenados no **[!UICONTROL Resources > Templates > Content templates]** nó.

   ![](assets/dce_popup_savetemplate.png)

   Depois de salvo, o template está disponível e pode ser selecionado ao criar o novo conteúdo.

   ![](assets/dce_create_fromtemplate.png)

* O ícone **Propriedades da página** permite selecionar informações de conteúdo na parte superior da página HTML.

   ![](assets/dce_popup_headerhtml.png)

   >[!NOTE]
   >
   >This information corresponds to the **`<title>`** and **`<meta>`** HTML tags on the page.
   >
   >As palavras-chave devem ser separadas por vírgulas.

## Opções de bloco {#block-options}

A seção à direita do editor agrupa as principais opções que permitem que você atue de acordo com o conteúdo. Para exibir essas opções, você deve selecionar um bloco: a natureza dessas opções depende do bloco selecionado.

![](assets/dce_right_section.png)

É possível:

* Determine a exibição de um ou vários blocos, consulte [Definindo uma condição](../../web/using/editing-content.md#defining-a-visibility-condition)de visibilidade,
* Defina as bordas e os quadros, consulte [Adicionar uma borda e um plano de fundo](../../web/using/editing-content.md#adding-a-border-and-background),
* Defina os atributos da imagem (tamanho, legenda), consulte [Editar propriedades](../../web/using/editing-content.md#editing-image-properties)da imagem,
* Vincule o banco de dados a um elemento de formulário (zona de entrada, caixa de seleção); consulte [Alteração das propriedades de dados de um formulário](../../web/using/editing-content.md#changing-the-data-properties-for-a-form),
* Torne uma parte de um formulário obrigatória, consulte [Alterar as propriedades de dados de um formulário](../../web/using/editing-content.md#changing-the-data-properties-for-a-form),
* Defina uma ação para um botão e consulte [Adicionar uma ação a um botão](../../web/using/editing-content.md#adding-an-action-to-a-button).

## Barra de ferramentas Conteúdo {#content-toolbar}

A barra de ferramentas é um **elemento pop-up** da interface do DCE que apresenta funções diferentes de acordo com o bloco selecionado.

>[!CAUTION]
>
>Certas funções de barra de ferramentas permitem formatar o conteúdo HTML. No entanto, se a página contiver uma folha de estilos CSS, as **instruções** da folha de estilos podem provar a **prioridade** sobre as instruções especificadas com a barra de ferramentas.

