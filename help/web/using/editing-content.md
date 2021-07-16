---
product: campaign
title: Edição de conteúdo
description: Edição de conteúdo
audience: web
content-type: reference
topic-tags: editing-html-content
exl-id: 968430d6-b1dd-47f8-8b31-39aaa18bc05c
source-git-commit: 360fd1ed8970c17c0687eaca0a4c1960d6f5838c
workflow-type: ht
source-wordcount: '1214'
ht-degree: 100%

---

# Edição de conteúdo{#editing-content}

## Definição de uma condição de visibilidade {#defining-a-visibility-condition}

É possível especificar uma condição de visibilidade em um elemento de página da Web: esse elemento será visível somente se a condição for respeitada.

Para adicionar uma condição de visibilidade, selecione um bloco e insira a condição no campo **[!UICONTROL Visibility condition]** com o editor de expressão.

![](assets/dce_add_condition.png)

>[!NOTE]
>
>A edição de expressão avançada é apresentada [nesta página](../../platform/using/defining-filter-conditions.md#list-of-functions).

![](assets/dce_popup_visibilitycondition.png)

Essas condições adotam a sintaxe da expressão XTK (por exemplo, **ctx.recipient.@email != &quot;&quot;** or **ctx.recipient.@status==&quot;0&quot;**). Por padrão, todos os campos são visíveis.

>[!NOTE]
>
>Blocos dinâmicos não visíveis, como menus suspensos, não podem ser editados.

## Adição de uma borda e um fundo {#adding-a-border-and-background}

Você pode adicionar uma **borda** a um bloco selecionado. As bordas são definidas usando três opções: estilo, tamanho e cor.

![](assets/dce_popup_border.png)

Você também pode definir uma **cor de plano de fundo** selecionando uma cor no gráfico de cores.

![](assets/dce_popup_background.png)

## Edição de formulários {#editing-forms}

### Alteração das propriedades dos dados de um formulário {#changing-the-data-properties-for-a-form}

Você pode vincular campos de banco de dados à zona de entrada, ao botão de opção ou aos blocos de tipo de caixa de seleção.

![](assets/dce_sidebar_field.png)

>[!NOTE]
>
>Os campos padrão são aqueles no schema de armazenamento da aplicação web.

O **campo** zona de entrada permite selecionar um campo de banco de dados com o campo de formulário.

Por padrão, os campos oferecidos são aqueles na tabela **nms:recipient**.

![](assets/dce_field_selection.png)

A opção de **campo Obrigatório** permite autorizar a aprovação da página somente se o usuário tiver preenchido o campo. Se um campo obrigatório não for preenchido, uma mensagem de erro será exibida.

Para botões de opção e caixas de seleção, é **necessária uma configuração adicional**.

Na verdade, se o template usado não contiver um valor por padrão, você deve preenchê-lo no editor.

Para fazer isso:

* Clique no ícone **[!UICONTROL Edit]**.

   ![](assets/dce_sidebar_options.png)

* Insira o valor da lista discriminada (definido pelo campo selecionado) no campo **[!UICONTROL Value]**.

   ![](assets/dce_sidebar_completeoptionradio.png)

### Modificação de campos de formulário {#modifying-form-fields}

Campos de formulário como botões de opção, zonas de entrada, listas suspensas, etc. podem ser modificados nas barras de ferramentas.

Isso significa que é possível:

* Exclua o bloco que contém os campos de formulário usando o ícone **[!UICONTROL Delete]**.
* Duplique o campo selecionado criando um novo bloco usando o ícone **[!UICONTROL Duplicate]**.
* Edite a janela **[!UICONTROL Form data]** para vincular um campo de banco de dados à zona de formulário, usando o ícone **[!UICONTROL Edit]**.

   ![](assets/dce_toolbar_formblock_edition.png)

## Adição de uma ação a um botão {#adding-an-action-to-a-button}

Quando o usuário clica em um botão, você pode definir uma ação associada. Para fazer isso, selecione a ação a ser executada da lista suspensa.

![](assets/dce_sidebar_button.png)

As opções disponíveis são as seguintes:

* **[!UICONTROL Refresh]**: atualiza a página atual.
* **[!UICONTROL Next page]** : cria um link para a próxima página no aplicativo web.
* **[!UICONTROL Previous page]**: cria um link para a página anterior no aplicativo web.

>[!NOTE]
>
>O valor **[!UICONTROL None]** permite que o botão não seja ativado.

Você pode modificar o rótulo vinculado ao botão no campo correspondente.

## Adição de um link {#adding-a-link}

Você pode inserir um link em qualquer elemento de página: imagem, palavra, grupo de palavras, bloco de texto, etc.

Para fazer isso, selecione o elemento, então use o primeiro ícone do menu pop-up.

![](assets/dce_insertlink_icon.png)

Esse ícone permite acessar todos os tipos de links disponíveis.

![](assets/dce_insertlink_menu.png)

Blocos de personalização e campos só podem ser inseridos em blocos de tipo de texto.

>[!NOTE]
>
>Para cada tipo de link, você pode configurar o modo de abertura: selecione a janela de público alvo na lista suspensa **Público-alvo.** Esse valor corresponde à tag **`<target>`** HTML.
>
>A lista de **público alvo** disponíveis é a seguinte:
>
>* Outro (IFrame)
>* Janela superior (_top)
>* Janela pai (_parent)
>* Nova janela (_blank)
>* Janela atual (_self)
>* Comportamento do navegador padrão
>



### Vincular a uma URL {#link-to-a-url}

A opção **Vincular a uma URL externa** permite abrir qualquer URL do conteúdo de origem.

![](assets/dce_toolbar_imgblock_externallink.png)

Digite o endereço de link em questão no campo **URL.** O campo URL deve ser populado da seguinte maneira: **https://www.myURL.com**.

### Vinculação a um aplicativo Web {#link-to-a-web-application}

A opção **Link para uma aplicação web** permite acessar uma aplicação web do Adobe Campaign.

![](assets/dce_toolbar_imgblock_appweb.png)

Selecione a aplicação web no campo correspondente.

A lista de aplicativos web sugeridos corresponde aos aplicativos disponíveis no nó **[!UICONTROL Resources > Online > Web Applications]**.

### Vincular a uma ação {#link-to-an-action}

O **Link que define uma opção de ação** permite configurar uma ação ao clicar em um elemento de origem.

![](assets/dce_toolbar_imgblock_action.png)

>[!NOTE]
>
>As ações disponíveis são detalhadas na seção [Adding an action to a button](#adding-an-action-to-a-button).

### Excluir um link {#delete-a-link}

Quando um link é inserido, a barra de ferramentas oferece dois novos ícones: **Editar link** e **Interromper o link** que permitem interagir com o link criado.

* **[!UICONTROL Edit link]** permite exibir uma janela com todos os parâmetros do link.
* **[!UICONTROL Break the link]** permite excluir o link, após confirmação, e todos os parâmetros relacionados.

>[!NOTE]
>
>Se o link for excluído, o conteúdo ainda será mantido.

## Alteração de atributos de fonte {#changing-font-attributes}

Ao selecionar um elemento de texto, é possível modificar os atributos de fonte (estilo, formato).

![](assets/dce_toolbar_txt.png)

As opções disponíveis são as seguintes:

* Ícone **Enlarge font**: aumenta o tamanho do texto selecionado (adicione `<span style="font size:">`)
* Ícone **Reduce font**: reduz o tamanho do texto selecionado (adicione `<span style="font size:">`)
* Ícone **Bold**: coloca o texto selecionado em negrito (quebra de texto automática com a tag `<strong> </strong>`)
* Ícone **Italic**: coloca o texto selecionado em itálico (quebra texto automática com a `<em> </em>` tag)
* Ícone **Underline**: coloca o texto selecionado em sublinhado (quebra de texto automática com a `<span style="text-decoration: underline;">` tag)
* Ícone **Align left**: alinha o texto à esquerda do bloco selecionado (adicione style=&quot;text-align: left;&quot;)
* Ícone **Center**: centraliza o texto do bloco selecionado (adicione style=&quot;text-align: center;&quot;)
* Ícone **Align right**: alinha o texto à direita do bloco selecionado (adicione style=&quot;text-align: right;&quot;)
* Ícone **Change the background color**: permite alterar a cor do plano de fundo do bloco selecionado (adicione style=&quot;background-color: rgba(170, 86, 255, 0.87))
* Ícone **Change text color**: permite alterar a cor do texto do bloco selecionado ou apenas o texto selecionado (`<span style="color: #CODE">`)

>[!NOTE]
>
>* Ícone **Delete**: exclui o bloco e todo o conteúdo.
>
>* Ícone **Duplicate**: duplica o bloco e todos os estilos relacionados ao bloco.


## Gerenciamento de imagens e animações {#managing-images-and-animations}

O Editor de conteúdo digital permite trabalhar em **qualquer tipo de imagem** compatível com os navegadores.

>[!CAUTION]
>
>Os arquivos externos não devem ser chamados em uma tag **script** da página HTML. Esses arquivos não serão importados para o servidor do Adobe Campaign.

### Adição/exclusão/duplicação de uma imagem {#adding---deleting---duplicating-an-image}

Para inserir uma imagem, selecione um bloco tipo Imagem e clique no ícone Imagem. ****

![](assets/dce_insert_image.png)

Selecione um arquivo de imagem salvo localmente.

![](assets/dce_popup_imgupload.png)

O ícone **Delete** exclui a tag ![]() contendo a imagem.

O ícone **Duplicate** duplica a tag ![]()e seu conteúdo.

>[!CAUTION]
>
>Quando você duplica uma imagem, os identificadores relacionados à nova imagem são excluídos.

### Edição de propriedades da imagem {#editing-image-properties}

Ao selecionar um bloco contendo uma imagem, você acessa as seguintes propriedades:

* **Caption** permite definir a legenda vinculada à imagem (corresponde ao atributo HTML **alt** ).
* **Dimensions** permite especificar o tamanho da imagem, em pixels.

   ![](assets/dce_popup_imgsize.png)

## Adição de conteúdo de personalização {#adding-personalization-content}

### Inserção de um campo de personalização {#inserting-a-personalization-field}

A opção **Campo de personalização** do ícone de inserção permite adicionar um campo de banco de dados ao conteúdo, como o nome do recipient. Essa opção só está disponível para blocos tipo texto.

![](assets/dce_toolbar_textblock_persofield.png)

Por padrão, os campos oferecidos são da tabela **[!UICONTROL Recipient]**. Quando necessário, edite as propriedades da aplicação web para selecionar outra tabela.

O nome do campo aparece no editor, destacado em amarelo. Ele será substituído pelo perfil do recipient de destino quando a personalização for gerada (por exemplo, ao pré-visualizar uma landing page).

Um exemplo é apresentado na seção [Inserting a personalization field](creating-a-landing-page.md#inserting-a-personalization-field).

### Inserção de um bloco de personalização {#inserting-a-personalization-block}

A opção de **Bloco de personalização** permite inserir blocos dinâmicos e personalizados no conteúdo. Por exemplo, você pode adicionar um logotipo ou uma mensagem de saudação. Não está disponível para blocos tipo texto.

![](assets/dce_toolbar_textblock_persoblock.png)

Depois de inserido, o nome do bloco de personalização aparece no editor, realçado em amarelo. Ele é adaptado automaticamente ao perfil do recipient quando a personalização é gerada.

Para obter mais informações sobre os blocos de personalização integrados e como customizá-los, consulte [esta página](../../delivery/using/personalization-blocks.md).
