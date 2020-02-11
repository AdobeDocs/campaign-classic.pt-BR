---
title: Renderização do formulário
seo-title: Renderização do formulário
description: Renderização do formulário
seo-description: null
page-status-flag: never-activated
uuid: 714ce201-5535-4fde-b388-1605ac54edcb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 669635bd-868b-4550-b075-6294ccb71297
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Renderização do formulário{#form-rendering}

## Seleção do template de renderização do formulário {#selecting-the-form-rendering-template}

As configurações de formulário permitem que você selecione o template usado para gerar as páginas. To access them, click the **[!UICONTROL Settings]** button in the form detail toolbar, and select the **[!UICONTROL Rendering]** tab. Há vários templates (folhas de estilos) disponíveis por padrão.

![](assets/s_ncs_admin_survey_rendering_select.png)

A seção inferior do editor permite exibir uma renderização do template selecionado.

O recurso de zoom permite editar o template selecionado.

![](assets/s_ncs_admin_survey_render_edit.png)

É possível modificar ou substituir esses templates. To do this, click the **[!UICONTROL Page layout...]** link and personalize the information.

![](assets/s_ncs_admin_survey_render_edit_param.png)

É possível:

* Alterar a imagem usada como um logotipo e adaptar seu tamanho,
* Especificar também o caminho para acessar a imagem de pré-visualização quando os usuários selecionam esse template de renderização.

The **[!UICONTROL Headers/Footers]** tab lets you change the information displayed in the headers and footers of each form page using this template.

![](assets/s_ncs_admin_survey_render_edit_header.png)

Each line of the **[!UICONTROL Page headers]** and **[!UICONTROL Page footers]** section corresponds to a line in the HTML page. Click **[!UICONTROL Add]** to create a new line.

Select an existing line and click the **[!UICONTROL Detail]** button to personalize it.

![](assets/s_ncs_admin_survey_render_edit_header_detail.png)

Você pode alterar o conteúdo da linha, adicionar bordas e alterar os atributos da fonte por meio das guias relevantes. Clique em **[!UICONTROL OK]** para confirmar essas alterações.

The **[!UICONTROL Position]** fields let you define the position of elements in the page header and footer.

![](assets/s_ncs_admin_survey_render_edit_header_position.png)

>[!NOTE]
>
>Os modelos de renderização são armazenados no **[!UICONTROL Administration > Configuration > Form rendering]** nó.\
>Para obter mais informações, consulte [Personalizar renderização de formulário](#customizing-form-rendering)

## Personalização da renderização do formulário {#customizing-form-rendering}

### Alteração do layout dos elementos {#changing-the-layout-of-elements}

Você pode sobrecarregar a folha de estilos de cada elemento do formulário (campos de entrada, imagens, botões de opção, etc.).

To do this, use the **[!UICONTROL Advanced]** tab.

![](assets/s_ncs_admin_survey_advanced_tab.png)

Ela permite que você defina as seguintes propriedades:

* **[!UICONTROL Label position]**: consulte [Definição da posição dos rótulos](../../web/using/defining-web-forms-layout.md#defining-the-position-of-labels),
* **[!UICONTROL Label format]**: Quebra de texto ou quebra automática de linha,
* **[!UICONTROL Number of cells]** : consulte [Posicionamento dos campos na página](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page),
* **[!UICONTROL Horizontal alignment]** (Esquerda, Direita, Centralizada) e **[!UICONTROL Vertical alignment]** (Alto, Baixo, Médio),
* **[!UICONTROL Width]** da zona: isso pode ser expresso como uma porcentagem ou em ems, pontos ou pixels (valor padrão),
* Maximum **[!UICONTROL Length]**: Maximum number of characters allowed (for Text, Number and Password type controls),
* **[!UICONTROL Lines]**: número de linhas para uma zona de **[!UICONTROL Multi-line text]** tipo,
* **[!UICONTROL Style inline]**: permite que você sobrecarregue a folha de estilos CSS com configurações adicionais. Esses são separados usando os caracteres **;** como mostrado no exemplo abaixo:

   ![](assets/s_ncs_admin_survey_advanced_tab_inline.png)

### Definição de cabeçalhos e rodapés {#defining-headers-and-footers}

Os campos são sequenciados em uma estrutura de árvore cuja raiz tem o mesmo nome que a página. Selecione para modificar o nome.

The title of the window must be entered in the **[!UICONTROL Page]** tab of the form property window. Você também pode adicionar um conteúdo definido ao cabeçalho e ao rodapé da página (essas informações serão exibidas em todas as páginas). This content is entered in the matching sections of the **[!UICONTROL Texts]** tab, as shown below:

![](assets/s_ncs_admin_survey_titles_config.png)

### Adição de elementos ao cabeçalho HTML {#adding-elements-to-html-header}

É possível inserir elementos adicionais no cabeçalho HTML de uma página de formulário. To do this, enter the elements in the **[!UICONTROL Header]** tab of the relevant page.

Isso permite que você faça referência a um ícone que será exibido na barra de título da página, por exemplo.

![](assets/webform_header_page_tab.png)

## Definição das configurações de controle {#defining-control-settings}

Quando o usuário preenche o formulário, uma verificação é automaticamente executada em determinados campos, dependendo do formato ou da configuração. This lets you make certain fields mandatory (refer to [Defining mandatory fields](#defining-mandatory-fields)) or check the format of the data entered (refer to [Checking data format](#checking-data-format)). As verificações são realizadas durante a aprovação da página (clicando em um link ou botão que permite uma transição de saída).

### Definição de campos obrigatórios {#defining-mandatory-fields}

Para tornar determinados campos obrigatórios, selecione essa opção ao criar o campo.

![](assets/s_ncs_admin_survey_required_field.png)

Se o usuário aprovar essa página sem ter inserido o campo, a seguinte mensagem será exibida:

![](assets/s_ncs_admin_survey_required_default_msg.png)

You can personalize this message by clicking the **[!UICONTROL Personalize this message]** link.

![](assets/s_ncs_admin_survey_required_custom_msg.png)

Se o usuário aprovar essa página sem ter inserido o campo, a seguinte mensagem será exibida:

![](assets/s_ncs_admin_survey_required_custom_msg2.png)

### Verificação do formato de dados {#checking-data-format}

Para verificar se os valores são armazenados em um campo existente do banco de dados, as regras do campo de armazenamento serão aplicadas.

Para verificações de formulário cujos valores são armazenados em uma variável, as regras de aprovação dependem do formato da variável.

For example, if you create a **[!UICONTROL Number]** check to store the client number, as shown below:

![](assets/s_ncs_admin_survey_choose_format.png)

O usuário deve inserir um inteiro no campo de formulário.

## Definição da exibição condicional de campos {#defining-fields-conditional-display}

Você pode configurar a exibição de campos na página a ser exibida com base nos valores escolhidos pelo usuário. Isso pode ser aplicado a um campo ou grupo de campos (quando eles são agrupados em um container).

For each element of the page, the **[!UICONTROL Visibility]** section lets you define the display conditions.

![](assets/s_ncs_admin_survey_condition_edit.png)

As condições podem se referir ao valor dos campos ou variáveis do banco de dados.

Na janela de seleção de campo, você pode escolher entre os seguintes dados:

![](assets/s_ncs_admin_survey_condition_select.png)

* A árvore principal contém os parâmetros do contexto de formulário. Os parâmetros padrão incluem o Identificador (que corresponde ao identificador criptografado do recipient), Idioma e Origem.

   Para obter mais informações, consulte esta [página](../../web/using/defining-web-forms-properties.md#form-url-parameters).

* The **[!UICONTROL Recipients]** sub-tree contains the input fields inserted into the form and stored in the database.

   Para obter mais informações, consulte [Armazenamento de dados no banco de dados](../../web/using/web-forms-answers.md#storing-data-in-the-database).

* The **[!UICONTROL Variables]** sub-tree contains the available variables for this form. Para obter mais informações, consulte [Armazenamento de dados em uma variável](../../web/using/web-forms-answers.md#storing-data-in-a-local-variable)local.

Para obter mais informações, consulte o caso de uso disponível aqui: [Exibindo opções diferentes dependendo dos valores](../../web/using/use-cases--web-forms.md#displaying-different-options-depending-on-the-selected-values)selecionados.

You can also condition the display of form pages using the **[!UICONTROL Test]** object. Para obter mais informações, consulte esta [página](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).

## Importação dos elementos de um formulário existente {#importing-elements-from-an-existing-form}

É possível importar campos ou containers de outros formulários web. Isso permite criar uma biblioteca de blocos reutilizáveis que serão inseridos em formulários, como o bloco de endereços, a área de subscrição do boletim informativo, etc.

Para importar um elemento para um formulário, siga as etapas abaixo:

1. Edit the page which you want to insert one or more elements into, then click **[!UICONTROL Import an existing block]** in the toolbar.

   ![](assets/s_ncs_admin_survey_import_block.png)

1. Selecione o formulário web que contém os campos a serem importados e escolha os containers e campos a serem importados.

   ![](assets/s_ncs_admin_survey_import_block_selection.png)

   >[!NOTE]
   >
   >The **[!UICONTROL Edit link]** icon to the right of the source form name lets you view the selected Web form.

1. Clique em **[!UICONTROL Ok]** para confirmar a inserção.

   ![](assets/s_ncs_admin_survey_import_block_rendering.png)

