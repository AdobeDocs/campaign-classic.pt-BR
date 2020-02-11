---
title: Inclusão de campos em um formulário web
seo-title: Inclusão de campos em um formulário web
description: Inclusão de campos em um formulário web
seo-description: null
page-status-flag: never-activated
uuid: 33c6ab85-b021-422a-a224-c9eff27e6fc0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: d63892b3-260d-45e8-b99a-1e7c78353395
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Inclusão de campos em um formulário web{#adding-fields-to-a-web-form}

Em um formulário Web, os campos permitem que os usuários insiram informações e selecionem opções. Os formulários web podem oferecer campos de entrada, campos de seleção, conteúdo estático e avançado (captchas, subscrições, etc.).

Quando o assistente é utilizado para adicionar campos, o tipo dele é automaticamente detectado com base no campo ou na variável de armazenamento selecionada. You can edit it using the **[!UICONTROL Type]** drop-down box in the **[!UICONTROL General]** tab.

![](assets/s_ncs_admin_webform_change_type.png)

Ao usar os botões na barra de ferramentas, selecione o tipo de campo que deseja adicionar.

Os seguintes tipos de campo estão disponíveis:

* Entrada de texto/número. Consulte [Adicionar campos](#adding-input-fields)de entrada.
* Seleção da lista suspensa. Consulte [Adicionar listas](#adding-drop-down-lists)suspensas.
* Múltipla escolha por meio de caixas de seleção. Consulte [Adicionar caixas de seleção](#adding-checkboxes).
* Seleção exclusiva por meio de botões de opção. Consulte [Adicionar botões](#adding-radio-buttons)de opção.
* Voto em uma grade de opções. Consulte [Adicionar grades](#adding-grids).
* Números e datas. See [Adding dates and numbers](#adding-dates-and-numbers).
* Assinatura/cancelamento de assinatura de um serviço de informações. Consulte Caixas de seleção [de assinatura](#subscription-checkboxes).
* Validação de Captcha. Consulte [Inserir um captcha](#inserting-a-captcha).
* Botão Download. [Carregamento de um arquivo](#uploading-a-file).
* Constante oculta. Consulte [Inserir uma constante](#inserting-a-hidden-constant)oculta.

Especifique o modo de armazenamento de resposta: atualize um campo no banco de dados (armazena somente o último valor salvo) ou armazene em uma variável (a resposta não é armazenada). Para obter mais informações, consulte os campos [de armazenamento de](../../web/using/web-forms-answers.md#response-storage-fields)resposta.

>[!NOTE]
>
>Por padrão, o campo é inserido na parte inferior da árvore atual. Use as setas na barra de ferramentas para movê-lo para cima ou para baixo.

## Assistente de criação do campo {#field-creation-wizard}

Para cada página do formulário, é possível adicionar um campo ao usar o primeiro botão da barra de ferramentas. To do this, go to the **[!UICONTROL Add using the wizard]** menu.

![](assets/s_ncs_admin_survey_add_field_menu.png)

Selecione o tipo de campo que deseja criar: é possível escolher a inclusão de um campo no banco de dados, uma variável ou até importar um grupo de campos criado em outro formulário e coletado em um container.

Click **[!UICONTROL Next]** and select the storage field or variable, or the container you want to import.

![](assets/s_ncs_admin_webform_wz_confirm_db.png)

Click **[!UICONTROL Finish]** to insert the selected field into the page.

![](assets/s_ncs_admin_webform_wz_insert_field.png)

## Adição de campos de entrada {#adding-input-fields}

To add an input field, click the **[!UICONTROL Input control]** button and choose the type of field you want to add.

![](assets/s_ncs_admin_webform_select_field.png)

### Tipos de campos de entrada {#types-of-input-fields}

Há cinco tipos diferentes de campos de texto que podem ser inseridos em uma página de formulário:

* **Text**: permite que o usuário insira um texto em uma linha.

   ![](assets/s_ncs_admin_survey_txt_ex.png)

* **Número**: permite que o usuário insira um número em uma linha. for more on this, refer to [Adding numbers](#adding-numbers).

   Quando a página é aprovada, o conteúdo é verificado para garantir que o valor inserido seja compatível com o campo. Para obter mais informações, consulte [Definição de configurações](../../web/using/form-rendering.md#defining-control-settings)de controle.

* **Password**: permite que o usuário insira texto em uma única linha. Durante a inserção de texto, os caracteres são substituídos por pontos:

   ![](assets/s_ncs_admin_survey_passwd_ex.png)

   >[!CAUTION]
   >
   >As senhas são armazenadas de forma não criptografada no banco de dados.

* **Multi-line text**: permite que o usuário insira texto em várias linhas.

   ![](assets/s_ncs_admin_survey_txtmulti_ex.png)

   >[!CAUTION]
   >
   >Campos de texto multilinha são campos específicos que podem conter código de fim de linha. O espaço de armazenamento deve estar associado a um campo mapeado em um elemento XML, não em um atributo XML. Para obter mais informações sobre os tipos de dados em schemas, consulte o capítulo &quot;Referência de schemas&quot; [nesta seção](../../configuration/using/about-schema-reference.md).
   >   
   >Se o módulo **Pesquisa** estiver sendo utilizado, é possível armazenar esse tipo de campo em um campo arquivado que se adapte automaticamente ao formato. Para obter mais informações, consulte [esta seção](../../web/using/about-surveys.md).

* **Enriched multi-line text**: permite que o usuário insira texto com um layout que será armazenado em formato HTML.

   ![](assets/s_ncs_admin_survey_txthtmli_ex.png)

   É possível selecionar o tipo de editor oferecido aos usuários. To do this, use the drop-down box of the **[!UICONTROL HTML editor]** field in the **[!UICONTROL Advanced]** tab.

   ![](assets/webapp_enrich_text_type.png)

   O número de ícones exibidos varia dependendo do tipo de editor. For an **[!UICONTROL Advanced]** editor, the rendering will be as follows:

   ![](assets/webapp_enrich_text_max.png)

### Configurar campos de entrada {#configure-input-fields}

Todos os campos de entrada são configurados com base no mesmo modo, utilizando as seguintes opções:

![](assets/s_ncs_admin_survey_txt_param.png)

The **[!UICONTROL General]** tab lets you enter the name of the field and attribute a default value to it if necessary.

The answer storage mode can be altered via the **[!UICONTROL Edit storage...]** link. Os valores podem ser armazenados em um campo existente do banco de dados; ou você pode escolher não salvar informações no banco de dados (use uma variável local).

>[!NOTE]
>
>Os modos de armazenamento são detalhados nos campos de armazenamento de [resposta](../../web/using/web-forms-answers.md#response-storage-fields)

The **[!UICONTROL Advanced]** tab lets you define display parameters for the field (position of labels, alignment, etc.). See [Defining web forms layout](../../web/using/defining-web-forms-layout.md).

## Adição de listas suspensas {#adding-drop-down-lists}

É possível inserir uma lista suspensa em uma página de pesquisa. Isso permite que o usuário selecione um valor com base na oferta em um menu suspenso.

![](assets/s_ncs_admin_survey_dropdown_sample.png)

To add a drop-down box to a form page, click the **[!UICONTROL Selection controls > Drop-down list]** button in the toolbar of the page editor.

![](assets/s_ncs_admin_survey_create_dropdown.png)

Selecione o modo de armazenamento de resposta e confirme sua escolha.

Define the labels and values of the list in the lower section of the **[!UICONTROL General]** tab. If the information is stored in an existing field of the database and it is an enumeration field, you can fill in the values automatically by clicking **[!UICONTROL Initialize the list of values from the database]** , as shown below:

![](assets/s_ncs_admin_survey_database_values.png)

>[!NOTE]
>
>Use as setas à direita da lista de valores para alterar sua sequência.

Se os dados estiverem armazenados em uma tabela vinculada, você poderá selecionar o campo onde os valores a serem sugeridos na lista serão salvos. For example, if you select the table of countries, click **[!UICONTROL Initialize the list of values from the database...]** and select the desired field.

![](assets/s_ncs_admin_survey_preload_values.png)

Next, click the **[!UICONTROL Load]** link to retrieve the values:

![](assets/s_ncs_admin_survey_load_button.png)

>[!CAUTION]
>
>Repita essa operação sempre que a lista for atualizada para renovar os valores na oferta.

## Adição de caixas de seleção {#adding-checkboxes}

Para selecionar uma opção, o usuário precisa usar uma caixa de seleção.

![](assets/s_ncs_admin_survey_check_box.png)

To add a checkbox to a form, click the **[!UICONTROL Selection controls > Checkbox...]** icon in the toolbar of the page editor.

Selecione o modo de armazenamento de resposta e confirme sua escolha.

Enter the label of the box in the **[!UICONTROL Label]** field of the **[!UICONTROL General]** tab.

![](assets/s_ncs_admin_survey_check_box_edit.png)

Uma caixa de seleção permite atribuir um valor ao campo de armazenamento (ou valor) dependendo se a caixa estiver ou não marcada. The **[!UICONTROL Values]** section lets you enter the value to assign if the box is checked (in the **[!UICONTROL Value]** field), and the value to assign if it is not checked (in the **[!UICONTROL Empty value]** field). Esses valores dependem do formato de armazenamento de dados.

Se o campo de armazenamento (ou variável) for booliano, o valor a ser atribuído se a caixa não estiver marcada será deduzido automaticamente. In this case, only the **[!UICONTROL Value if checked]** field is offered, as shown below:

![](assets/s_ncs_admin_survey_check_box_enum.png)

## Example: Assign a value to a field if a box is checked {#example--assign-a-value-to-a-field-if-a-box-is-checked}

Queremos inserir uma caixa de seleção em um formulário para enviar uma solicitação de manutenção, conforme mostrado abaixo:

![](assets/s_ncs_admin_survey_check_box_ex.png)

The information will be uploaded to the database and into an existing field (in this case, the **[!UICONTROL Comment]** field):

![](assets/s_ncs_admin_survey_check_box_ex_list.png)

If the &quot;Maintenance required&quot; box is checked, the **[!UICONTROL Comment]** column will contain &quot;Maintenance required&quot;. Se a caixa não estiver marcada, a coluna exibirá &quot;Manutenção não necessária&quot;. Para obter esse resultado, aplique a seguinte configuração à caixa de seleção na página do formulário:

![](assets/s_ncs_admin_survey_check_box_ex_edit.png)

## Adição de botões de opção {#adding-radio-buttons}

Os botões de opção permitem oferecer uma série de opções exclusivas aos usuários. Esses são valores diferentes para o mesmo campo.

![](assets/s_ncs_admin_survey_radio_button.png)

Você pode criar botões de opção individualmente (botões unitários) ou por uma lista de múltipla escolha, mas como o objetivo dos botões de opção é selecionar uma opção ou outra, sempre criaremos pelo menos um par de botões de opção, nunca apenas um único botão.

>[!CAUTION]
>
>Para tornar a seleção obrigatória, você precisa criar uma lista de várias opções.

### Adicionar botões únicos {#add-single-buttons}

To add a radio button to a form page, go to the **[!UICONTROL Selection controls > Radio button]** menu in the toolbar of the page editor and choose a storage mode.

![](assets/s_ncs_admin_survey_radio_button_sample.png)

Radio buttons are configured in a similar way to checkboxes (see [Adding checkboxes](#adding-checkboxes)). No entanto, nenhum valor será atribuído se a opção não estiver selecionada. Para que vários botões sejam interdependentes, ou seja, a seleção de um desmarca o outro automaticamente, eles devem ser armazenados no mesmo campo. Se eles não estiverem armazenados no banco de dados, a mesma variável local deverá ser usada para o armazenamento temporário. Consulte Campos [de armazenamento de](../../web/using/web-forms-answers.md#response-storage-fields)resposta.

### Add a list of buttons {#add-a-list-of-buttons}

To add radio buttons via a list, go to the **[!UICONTROL Selection controls>Multiple choice]** menu in the toolbar of the page editor.

![](assets/s_ncs_admin_survey_radio_button_sample2.png)

Adicione a mesma quantidade de botões de opção que houver de rótulos. A vantagem desse recurso é que você pode importar valores de um campo existente (caso de um campo discriminado) e fazer com que o usuário escolha uma opção. No entanto, o layout dos botões é menos flexível.

>[!NOTE]
>
>Os formulários Web não autorizam a seleção de vários valores. Várias seleções podem ser ativadas somente para formulários de tipo **Pesquisa.** Para obter mais informações, consulte [esta seção](../../web/using/about-surveys.md).\
>It is possible, however, to insert a **[!UICONTROL Multiple choice]** type field into a Web application; but without authorizing the selection of several values: the options offered can be selected using radio buttons.

## Adição de grades {#adding-grids}

As grades são usadas para criar páginas de votação em aplicações Web. Isso permite oferecer listas de botões de opção para responder pesquisas ou formulários Web do tipo avaliação, conforme mostrado abaixo:

![](assets/s_ncs_admin_survey_vote_param.png)

Para usar esse tipo de elemento em um formulário, crie uma grade simples e adicione uma linha para cada elemento a ser avaliado.

![](assets/s_ncs_admin_survey_vote_sample.png)

O número de botões de opção em cada linha da grade corresponde ao número de valores definidos na grade simples.

![](assets/s_ncs_admin_survey_vote_ex.png)

Somente uma opção pode ser selecionada por linha de grade.

>[!NOTE]
>
>No nosso exemplo, o rótulo da grade está oculto. Para fazer isso, vá para a **[!UICONTROL Advanced]** guia, a **[!UICONTROL Label position]** exibição é definida como **[!UICONTROL Hidden]** . See [Defining the position of labels](../../web/using/defining-web-forms-layout.md#defining-the-position-of-labels).

## Adição de datas e números {#adding-dates-and-numbers}

O conteúdo dos campos de formulário pode ser formatado para corresponder aos dados armazenados no banco de dados ou para atender a um requisito específico. Você pode criar campos adequados para a entrada de números e datas.

### Adição de datas {#adding-dates}

![](assets/s_ncs_admin_survey_date_calendar.png)

To allow the user to enter a date in a form page, select **[!UICONTROL Add input field > Date...]** in the toolbar or page editor.

Insira um rótulo para o campo e configure o modo de armazenamento de dados.

![](assets/s_ncs_admin_survey_date_edit.png)

A seção inferior da janela permite selecionar os formatos de data e hora dos valores armazenados neste campo.

![](assets/s_ncs_admin_survey_date_edit_values.png)

Você também pode escolher não exibir a data (ou hora).

As datas podem ser selecionadas por meio de um calendário ou caixas suspensas. Você também pode inseri-las diretamente no campo, mas eles precisam corresponder ao formato especificado na tela acima.

>[!NOTE]
>
>Por padrão, as datas usadas em formulários são inseridas por meio de um calendário. Para formulários multilíngues, verifique se os calendários estão disponíveis em todos os idiomas usados. See [Translating a web form](../../web/using/translating-a-web-form.md).

No entanto, em alguns casos (para inserir datas de nascimento, por exemplo), pode ser mais fácil usar listas suspensas.

![](assets/s_ncs_admin_survey_date_list_select.png)

To do this, click the **[!UICONTROL Advanced]** tab and choose the input mode using **[!UICONTROL Drop-down lists]**.

![](assets/s_ncs_admin_survey_date_selection.png)

Você pode então definir limites para os valores oferecidos na lista.

![](assets/s_ncs_admin_survey_date_first_last_y.png)

### Adição de números {#adding-numbers}

Você pode criar campos adequados para a entrada de números.

![](assets/s_ncs_admin_survey_number.png)

Em um campo numérico, o usuário pode inserir somente números. O controle de entrada é aplicado automaticamente quando a página é aprovada.

Dependendo do campo no qual os dados são armazenados no banco de dados, a formatação especial ou certas restrições podem ser aplicadas. Também é possível especificar valores máximos e mínimos. Esse tipo de campo é configurado da seguinte maneira:

![](assets/s_ncs_admin_survey_number_edit.png)

O valor padrão é o valor exibido no campo quando o formulário é publicado. Ele pode ser corrigido pelo usuário.

You can add a prefix and/or suffix to the numeric field via the **[!UICONTROL Advanced]** tab, as shown below:

![](assets/s_ncs_admin_survey_number_ex_conf.png)

No formulário, a renderização será a seguinte:

![](assets/s_ncs_admin_survey_number_ex.png)

## Caixas de seleção de subscrição {#subscription-checkboxes}

Você pode adicionar controles para permitir que os usuários realizaem a subscrição ou unsubscription de um ou mais serviços de informação (boletins informativos, avisos, notificações em tempo real, etc.). Para se subscrever, o usuário marca o serviço correspondente.

Para criar uma caixa de seleção de assinatura, clique em **[!UICONTROL Advanced controls>Subscription]**.

![](assets/s_ncs_admin_survey_subscription_edit.png)

Indicate the label for the checkbox and select the information service concerned using the **[!UICONTROL Service]** drop-down box.

>[!NOTE]
>
>Os serviços de informação são detalhados nesta [página](../../delivery/using/managing-subscriptions.md).

O usuário se subscreve no serviço marcando a opção relevante.

![](assets/s_ncs_admin_survey_subscribe.png)

>[!CAUTION]
>
>Se o usuário já estiver subscrito em um serviço de informação e a caixa vinculada a esse serviço não estiver marcada ao aprovar o formulário, a subscrição será cancelada.

Exemplos de subscrições e referências estão disponíveis [nesta seção](../../web/using/about-surveys.md).

## Inserção de um captcha {#inserting-a-captcha}

O objetivo dos testes de **captcha** é evitar o uso fraudulento dos formulários web.

>[!CAUTION]
>
>Se seu formulário contiver várias páginas, o Captcha deverá sempre ser colocado na última página, logo antes da caixa de armazenamento, para evitar qualquer erro das medidas de segurança.

To insert a Captcha into a form, click the first button on the toolbar and Select **[!UICONTROL Advanced controls>Captcha]**.

![](assets/s_ncs_admin_survey_add_captcha.png)

Insira o rótulo do campo. Esse rótulo será exibido na frente da área de exibição Captcha. You can change the position of this label in the **[!UICONTROL Advanced]** tab.

![](assets/s_ncs_admin_survey_captcha_adv.png)

>[!NOTE]
>
>For **[!UICONTROL captcha]** type controls, there is no need to indicate a storage field or variable.

O Captcha é inserido na página com um campo de entrada posicionado sob o visual. Esses dois elementos são inseparáveis e considerados como um único item para o propósito do layout da página (eles ocupam uma única célula).

![](assets/s_ncs_admin_survey_captcha_sample.png)

Quando a página é confirmada, o campo de entrada é exibido em vermelho se o conteúdo do Captcha não foi inserido corretamente.

![](assets/s_ncs_admin_survey_captcha_error.png)

Você pode criar uma mensagem de erro para exibir. Para fazer isso, use o **[!UICONTROL Personalize the message]** link na **[!UICONTROL General]** guia.

![](assets/s_ncs_admin_survey_captcha_error_msg.png)

>[!NOTE]
>
>Os Captchas têm sempre 8 caracteres. Você não pode modificar esse valor.

## Carregamento de um arquivo {#uploading-a-file}

Você pode adicionar um campo de carregamento a uma página. Essa funcionalidade pode ser útil para o compartilhamento de arquivos da intranet, por exemplo.

![](assets/s_ncs_admin_survey_download_file.png)

To insert an upload field to a form page, select the **[!UICONTROL Advanced controls > File...]** menu in the toolbar of the page editor.

By default, the uploaded files are stored in resource files accessible via the **[!UICONTROL Resources > Online > Public resources]** menu. Você pode usar um script para alterar esse comportamento. Esse script pode usar as funções definidas na [documentação do Campaign JSAPI](http://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html), incluindo as que se referem à manipulação de arquivos.

Você pode armazenar o link para esses arquivos em uma variável local ou em um campo de banco de dados. Por exemplo, você pode estender o schema de recipients para adicionar um link a recursos baseados em arquivo.

>[!CAUTION]
>
>* Esse tipo de arquivo deve ser reservado para formulários com acesso seguro (usando credenciais).
>* O Adobe Campaign não controla o tamanho ou o tipo de recurso carregado: portanto, é altamente recomendável usar campos de carregamento para sites de intranet tipo seguro.
>* Se vários servidores estiverem vinculados à instância (arquitetura de balanceamento de carga), verifique se as chamadas para o formulário da Web chegam ao mesmo servidor.
>* Essas implementações exigem a assistência da equipe de consulta do Adobe Campaign.
>



## Inserir uma constante oculta {#inserting-a-hidden-constant}

Você pode realçar um campo quando o usuário passa em uma das páginas do formulário. Para fazer isso, coloque uma constante na página e especifique o valor e o local de armazenamento.

Este campo não está visível para o usuário, mas pode ser utilizado para enriquecer os dados no perfil de usuário.

No exemplo a seguir, o arquivo de **origem** do perfil do recipient é preenchido automaticamente sempre que um usuário aprova essa página. A constante não é exibida na página.

![](assets/s_ncs_admin_survey_constante.png)

