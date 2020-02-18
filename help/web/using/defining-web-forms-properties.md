---
title: Definição das propriedades dos formulários web
seo-title: Definição das propriedades dos formulários web
description: Definição das propriedades dos formulários web
seo-description: null
page-status-flag: never-activated
uuid: 2fb0952a-5f73-48f5-b344-e3247cefca62
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 36953eb5-3296-4796-9352-945121bbdc69
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7a0d82dfc6dc50026214d7d3b1094d45ffadbc03

---


# Definição das propriedades dos formulários web{#defining-web-forms-properties}

Os formulários web são completamente configuráveis e personalizáveis para atender aos seus requisitos. Os parâmetros devem ser inseridos na janela de propriedades.

The properties window is accessible via the **[!UICONTROL Properties]** button in the toolbar of the Web form. Essa janela permite que você acesse um intervalo de configurações específicas ao formulário web. Algumas configurações podem resultar da configuração do template.

![](assets/s_ncs_admin_survey_properties_general.png)

## Propriedades gerais do formulário {#overall-form-properties}

In the **[!UICONTROL General]** tab of the properties window, you can modify the **Label** of the form. É extremamente recomendável não alterar o **nome Interno**.

![](assets/s_ncs_admin_survey_properties_general_tab.png)

O template de formulário é escolhido durante a criação do formulário. Ele não pode ser alterado posteriormente. Para obter mais informações sobre como criar e gerenciar modelos de formulário, consulte [Uso de um modelo](../../web/using/using-a-web-form-template.md)de formulário da Web.

## Armazenamento de dados do formulário {#form-data-storage}

Por padrão, os campos de formulários web são armazenados na tabela de recipients. You can change the table used by selecting a new table from the **[!UICONTROL Document type]** field. The **[!UICONTROL Zoom]** icon lets you view the content of the selected table.

Por padrão, as respostas são armazenadas na **[!UICONTROL Answer to a recipient form]** tabela.

## Configuração de uma página de erro {#setting-up-an-error-page}

Você pode configurar uma página de erro: essa página será exibida caso ocorra erros durante a execução do formulário.

A página de erro é definida na guia correspondente da janela de propriedades do formulário.

Por padrão, ela mostra as seguintes informações:

![](assets/s_ncs_admin_survey_default_error_page.png)

The content of the strings displayed is defined in the **[!UICONTROL Error page]** tab of the properties window. The **[!UICONTROL HTML]** tab displays the rendering and the **[!UICONTROL Texts]** tab lets you modify the text strings and add some text if necessary:

![](assets/s_ncs_admin_survey_error_page.png)

## Localização do formulário {#form-localization}

The **[!UICONTROL Localization]** tab lets you select the design and display languages for the Web form.

See [Translating a web form](../../web/using/translating-a-web-form.md).

## Navegação e renderização de formulários {#form-browsing-and-rendering}

The **[!UICONTROL Rendering]** tab lets you define the type of browsing between pages of the Web form and the rendering template used.

Você pode escolher navegar por meio de links ou botões.

![](assets/s_ncs_admin_survey_wz_02_navig_type.png)

Os botões são os elementos de navegação por padrão. Eles permitem executar as seguintes ações:

* Approve the current page and display the next page by clicking **[!UICONTROL Next]**. Esse botão é exibido em todas as páginas, exceto o último.
* Display the previous page by clicking **[!UICONTROL Previous]**. Esse botão é exibido em todas as páginas, exceto o primeiro.
* Save the form responses by clicking the **[!UICONTROL Approve]** button. Esse botão só é exibido na última página.

Esses elementos são exibidos na parte inferior de cada página. Suas posições podem ser alteradas. Para fazer isso, você deve modificar a folha de estilos.

>[!NOTE]
>
>It&#39;s possible to hide the **[!UICONTROL Previous]** button on some pages. To do this, go to the concerned page and check the **[!UICONTROL Disallow returning to the previous page]** option. Essa opção é acessível quando a raiz da árvore de página é selecionada.

The **[!UICONTROL Template]** field of the **[!UICONTROL Rendering]** tab lets you select a theme from those available.

Themes are saved in the **[!UICONTROL Administration>Configuration>Form rendering]** node of the tree. See [Selecting the form rendering template](../../web/using/form-rendering.md#selecting-the-form-rendering-template)

Uma renderização de amostra é exibida na parte inferior da janela de propriedades. The **[!UICONTROL Edit link]** icon lets you view the configuration for the selected theme.

![](assets/s_ncs_admin_survey_properties_render.png)

## Textos no formulário {#texts-in-the-form}

The **[!UICONTROL Page]** tab lets you define the content of the form header and footer. See [Defining headers and footers](../../web/using/form-rendering.md#defining-headers-and-footers).

Também permite gerenciar traduções. See [Translating a web form](../../web/using/translating-a-web-form.md).

## Acessibilidade do formulário {#accessibility-of-the-form}

A Web form is accessible to users if it is **[!UICONTROL Online]** and if the current date is within its validity period. The status of the form is modified during the publication stage (see [Publishing a form](../../web/using/publishing-a-web-form.md#publishing-a-form)). The status is displayed in the **Project** section of the **[!UICONTROL General]** tab of the properties window.

O período de validade vai da **[!UICONTROL Start]** data até a **[!UICONTROL End date]**. Se nenhuma data for especificada nesses campos, o formulário terá validade permanente.

![](assets/s_ncs_admin_survey_properties_date.png)

>[!NOTE]
>
>Se o formulário estiver fechado e, portanto, seu período de validade não tiver sido atingido ou expirado, ou se ele tiver sido fechado pelo operador do Adobe Campaign, uma mensagem será exibida quando o usuário tentar acessá-lo. Você pode personalizar esta mensagem clicando em **[!UICONTROL Personalize the message displayed if the form is closed...]**.

## Controle de acesso ao formulário {#form-access-control}

Por padrão, o acesso aos formulários web é realizado no modo anônimo: todos os operadores que acessam o formulário recebem os direitos de operador do WebApp.

Você pode habilitar o controle de acesso para a exibição do formulário, por exemplo, ao entregar um formulário em um site da Intranet para autenticar usuários. To do this, display the **[!UICONTROL Properties]** window of the concerned form and click the **[!UICONTROL Enable access control]** option, as shown below:

![](assets/s_ncs_admin_survey_access_ctrl.png)

Quando a página for acessada, o seguinte formulário de autenticação será exibido:

![](assets/s_ncs_admin_survey_access_login.png)

O login e a senha são aqueles usados pelos operadores do Adobe Campaign. Para obter mais informações, consulte [esta seção](../../platform/using/access-management.md).

The **[!UICONTROL Use a specific account]** option lets you limit the read or write permission of the operator who accesses the form. Use a caixa suspensa para selecionar um operador ou grupo de operadores que estará encarregado de conceder essas permissões.

![](assets/s_ncs_admin_survey_access_op_select.png)

## Parâmetros da URL do formulário {#form-url-parameters}

É possível incluir parâmetros adicionais na URL de um formulário para personalizar seu conteúdo e inicializar um contexto (idioma, ID do recipient criptografada, empresa, fórmula calculada armazenada em uma variável, etc.). Isso permite que você dê acesso a um formulário por meio de várias URLs diferentes e personalize o conteúdo da página com base no valor do(s) parâmetro(s) indicado(s) na URL.

Por padrão, o Adobe Campaign oferece parâmetros para pré-visualizar o formulário e verificar erros. Você pode criar novas configurações vinculadas ao formulário, que pode usar os valores de um campo no banco de dados ou de uma variável local.

## Parâmetros padrão {#standard-parameters}

Os seguintes parâmetros estão disponíveis por padrão:

* **id** para indicar o identificador criptografado.
* **lang** para alterar o idioma de exibição.
* **origin** para especificar a origem do entrevistado.
* **_uuid** permite a exibição de formulário antes da publicação e do rastreamento de erros. Esse parâmetro é para uso interno (criação e depuração): quando você acessa o formulário web por meio dessa URL, os registros criados não são levados em consideração no rastreamento (relatórios). The origin is forced to the **[!UICONTROL Adobe Campaign]** value.

   Ele é usado com os parâmetros **_preview** e/ou **_debug**:

   **_preview** para exibir a última versão salva. Esse parâmetro deve ser usado somente na fase de teste.

   **_debug** para exibir o rastreamento da entrada de dados ou calculada nas páginas do formulário. Isso é usado para obter mais informações sobre erros, incluindo uma vez que o formulário foi publicado.

   >[!CAUTION]
   >
   >When the form is displayed via a URL with the **_uuid** parameter, the value of the **[!UICONTROL origin]** parameter is forced to **Adobe Campaign**.

## Adição de parâmetros {#adding-parameters}

Parameters can be added via the **[!UICONTROL Parameters...]** tab in the Properties window of the form. Eles podem ser obrigatórios, conforme mostrado abaixo:

![](assets/s_ncs_admin_survey_properties_param.png)

Você deve especificar um local de armazenamento a partir do qual o valor do parâmetro será recuperado. To do this, select one of the storage options and then click the **[!UICONTROL Storage]** tab to select the field or the variable concerned. As opções de armazenamento são detalhadas nos campos [de armazenamento de](../../web/using/web-forms-answers.md#response-storage-fields)resposta.

O status do entrevistado (0, 1 ou qualquer outro valor) pode então ser adicionado ao URL para acessar o formulário. Essas informações podem ser reutilizadas nas páginas do formulário ou em uma caixa de teste. As páginas exibidas podem ser condicionadas com base no valor do contexto, conforme mostrado abaixo:

1. Home page para clientes (**status=1**):

   ![](assets/s_ncs_admin_survey_test_client.png)

1. Home page para clientes potenciais (**status=0**):

   ![](assets/s_ncs_admin_survey_test_prospect.png)

1. Home page para outros perfis (por exemplo, **status=12**):

   ![](assets/s_ncs_admin_survey_test_other.png)

Para configurar este formulário, crie uma caixa de teste e coloque-a no início do diagrama, conforme mostrado abaixo:

![](assets/s_ncs_admin_survey_test.png)

A caixa de teste permite configurar as condições de sequenciamento de página:

![](assets/s_ncs_admin_survey_test_box.png)

