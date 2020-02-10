---
title: Definição do sequenciamento de páginas dos formulários web
seo-title: Definição do sequenciamento de páginas dos formulários web
description: Definição do sequenciamento de páginas dos formulários web
seo-description: null
page-status-flag: never-activated
uuid: 297fad62-d806-4bd8-9b8c-313c20344ab0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 85bf3244-6896-43e7-96b8-84c45c282fec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Definição do sequenciamento de páginas dos formulários web{#defining-web-forms-page-sequencing}

O formulário pode conter uma ou mais páginas. Ele é criado por meio de um diagrama que permite o sequenciamento de páginas e testes, execução de scripts e estágios de gravação de jump da página. O modo de construção de diagrama é igual a um workflow.

## Sobre a página anterior e a próxima página {#about-previous-page-and-next-page}

Para cada página, você pode excluir os botões **[!UICONTROL Next]** ou **[!UICONTROL Previous]** . Para fazer isso, selecione a página em questão e selecione a opção **[!UICONTROL Disable next page]** ou **[!UICONTROL Disallow returning to the previous page]** .

![](assets/s_ncs_admin_survey_no_next_page.png)

Você pode substituir esses botões por links. Consulte [Inserir conteúdo](../../web/using/static-elements-in-a-web-form.md#inserting-html-content)HTML.

## Inserção de um jump {#inserting-a-jump}

The **[!UICONTROL Jump]** object gives access to another page or another form when the user clicks **[!UICONTROL Next]**.

O destino pode ser:

* Outra página do formulário. To do this, select **[!UICONTROL Internal activity]** and then specify the desired page, as below:

   ![](assets/s_ncs_admin_jump_param1.png)

* Outro formulário. To do this, select the **[!UICONTROL Explicit]** option and specify the destination form.

   ![](assets/s_ncs_admin_jump_param2.png)

* O destino pode ser armazenado em uma variável. Nesse caso, selecione-o na lista suspensa, conforme mostrado abaixo:

   ![](assets/s_ncs_admin_jump_param3.png)

* The **[!UICONTROL Comment]** tab lets you enter information that will be visible by the operator when they click the object in the diagram.

   ![](assets/s_ncs_admin_survey_jump_comment.png)

## Example: accessing another form according to a parameter of the URL {#example--accessing-another-form-according-to-a-parameter-of-the-url}

No exemplo a seguir, queremos configurar um formulário web que, quando aprovado, exibirá outro formulário designado por um parâmetro da URL. Para fazer isso, siga as etapas abaixo:

1. Insert a jump at the end of a form: this replaces the **[!UICONTROL End]** box.

   ![](assets/s_ncs_admin_survey_jump_sample1.png)

1. Nas propriedades do formulário, adicione um parâmetro (**próximo**) armazenado em uma variável local (**próximo**). As variáveis locais são detalhadas em [Armazenamento de dados em uma variável](../../web/using/web-forms-answers.md#storing-data-in-a-local-variable)local.

   ![](assets/s_ncs_admin_survey_jump_sample2.png)

1. Edit the **[!UICONTROL Jump]** object, select the **[!UICONTROL Stored in a variable]** option and select the **next** variable from the drop-down box.

   ![](assets/s_ncs_admin_survey_jump_sample3.png)

1. A URL do delivery deve incluir o nome interno do formulário de destino, por exemplo:

   ```
   https://[myserver]/webForm/APP62?&next=APP22
   ```

   When the user clicks the **[!UICONTROL Approve]** button, form **APP22** is displayed.

## Inserção de um link para outra página do formulário {#inserting-a-link-to-another-page-of-the-form}

Você pode inserir links para outras páginas do formulário. To do this, add a **[!UICONTROL Link]** type static element to the page. For more on this, refer to [Inserting a link](../../web/using/static-elements-in-a-web-form.md#inserting-a-link).

## Exibição de página condicional {#conditional-page-display}

### Exibir com base em respostas {#display-based-on-responses}

The **[!UICONTROL Test]** box lets you condition the sequencing of pages in a form. Ela permite definir várias linhas de filial, dependendo dos resultados do teste. Isso permite exibir páginas diferentes dependendo das respostas fornecidas pelos usuários.

Por exemplo, você pode exibir uma página diferente para clientes que já solicitaram online e outra para aqueles que fizeram mais de dez pedidos. To do this, in the first page of the form, insert a **[!UICONTROL Number]** type input field for the user to state how many orders they have placed.

![](assets/s_ncs_admin_survey_test_ex0.png)

Você pode armazenar essas informações em um campo do banco de dados ou usar uma variável local.

>[!NOTE]
>
>Os modos de armazenamento são detalhados nos campos [de armazenamento de](../../web/using/web-forms-answers.md#response-storage-fields)resposta.

No nosso exemplo, queremos usar uma variável:

![](assets/s_ncs_admin_survey_test_ex1.png)

No diagrama do formulário, insira uma caixa de teste para definir as condições. Para cada condição, uma nova ramificação será adicionada na saída da caixa de teste.

![](assets/s_ncs_admin_survey_test_ex2.png)

Select the **[!UICONTROL Activate the default branching]** option to add a transition for cases where none of the conditions is true. Essa opção é desnecessária se cada caso possível for coberto pelas condições definidas.

Em seguida, defina o sequenciamento de página quando uma ou outra das condições for verdadeira, por exemplo:

![](assets/s_ncs_admin_survey_test_ex3.png)

### Exibir com base em parâmetros {#display-based-on-parameters}

Você também pode personalizar o sequenciamento de página de acordo com os parâmetros de inicialização do formulário web ou de acordo com os valores armazenados no banco de dados. Consulte Parâmetros [do URL do](../../web/using/defining-web-forms-properties.md#form-url-parameters)formulário.

## Adição de scripts {#adding-scripts}

The **[!UICONTROL Script]** object lets you enter a JavaScript script directly, for example to modify the value of a field, retrieve data from the database, or call an Adobe Campaign API.

## Personalização da página final {#personalizing-the-end-page}

Você deve colocar uma página final no final do diagrama. The end page is displayed when the user clicks the **[!UICONTROL Approve]** button in the Web form.

To personalize this page, double-click **[!UICONTROL End]** and enter the content of the page in the central editor.

![](assets/s_ncs_admin_survey_end_page_edit.png)

* Você pode copiar e colar conteúdo HTML existente. To do this, click **[!UICONTROL Display source code]** and insert the HTML code.
* Você pode usar uma URL externa; para fazer isso, selecione a opção correspondente e digite a URL da página a ser exibida.

