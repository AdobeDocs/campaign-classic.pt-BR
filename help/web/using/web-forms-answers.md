---
title: Respostas dos formulários web
seo-title: Respostas dos formulários web
description: Respostas dos formulários web
seo-description: null
page-status-flag: never-activated
uuid: 374df070-8969-4bf6-bd24-0b827d38593f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: c89926b6-488e-4c72-8f67-b6af388bade3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Respostas dos formulários web{#web-forms-answers}

## Campos de armazenamento de resposta {#response-storage-fields}

As respostas a formulários podem ser salvas em um campo do banco de dados ou temporariamente em uma variável local. O modo de armazenamento para respostas é escolhido durante a criação do campo. It can be edited via the **[!UICONTROL Edit storage...]** link.

Para cada campo de entrada em um formulário, as seguintes opções de armazenamento estão disponíveis:

![](assets/s_ncs_admin_survey_select_storage.png)

* **[!UICONTROL Edit a recipient]**

   Você pode selecionar um campo do banco de dados: as respostas dos usuários serão armazenadas nesse campo. Para cada usuário, somente o último valor inserido é salvo: é adicionado ao perfil: Consulte [Armazenamento de dados no banco de dados](#storing-data-in-the-database).

* **[!UICONTROL Variable]**

   Se não quiser armazenar informações no banco de dados, você poderá usar uma variável. As variáveis locais podem ser declaradas como upstream. Consulte [Armazenamento de dados em uma variável](#storing-data-in-a-local-variable)local.

### Storing data in the database {#storing-data-in-the-database}

To save the data in an existing field of the database, click the **[!UICONTROL Edit expression]** icon and select it from the list of available fields.

![](assets/s_ncs_admin_survey_storage_type1.png)

>[!NOTE]
>
>O documento de referência padrão é o schema **nms:recipient.** To view it or to choose a new one, select the form from the list, and click the **[!UICONTROL Properties]** button.

### Armazenamento de dados em uma variável local {#storing-data-in-a-local-variable}

Você pode usar variáveis locais de modo que, mesmo que os dados não sejam armazenados no banco de dados, ele pode ser reutilizado na página ou nas outras páginas, por exemplo, para colocar condições na exibição de um campo ou para personalizar uma mensagem.

Isso significa que você pode utilizar o valor de um campo não salvo para autorizar a visualização de um grupo de opções na página. Na página abaixo, o tipo de veículo não está armazenado no banco de dados:

![](assets/s_ncs_admin_survey_no_storage_variable.png)

It is stored in a variable which must be selected when the drop-down box is created, or via the **[!UICONTROL Edit storage...]** link.

![](assets/s_ncs_admin_survey_no_storage_variable2.png)

You can display existing variables and create new ones via the **[!UICONTROL Edit variables...]** link. Click the **[!UICONTROL Add]** button to create a new variable.

![](assets/s_ncs_admin_survey_add_a_variable.png)

A variável adicionada estará disponível na lista de variáveis locais quando os campos de entrada da página forem criados.

>[!NOTE]
>
>Para cada formulário, você pode criar variáveis upstream. To do this, select the form and click the **[!UICONTROL Properties]** button. The **[!UICONTROL Variables]** tab contains the local variables for the form.

**Exemplo de armazenamento local com condições**

In the above example, the container that includes data concerning private vehicles is displayed only if the **[!UICONTROL Private]** option is selected from the drop-down list, as indicated in the visibility condition:

![](assets/s_ncs_admin_survey_add_a_condition.png)

Se o usuário selecionar um veículo privado, o formulário web oferecerá as seguintes opções:

![](assets/s_ncs_admin_survey_no_storage_conda.png)

O container que mantém os dados relativos aos veículos comerciais será exibido se a opção Profissional estiver selecionada, conforme expresso na condição de visibilidade:

![](assets/s_ncs_admin_survey_view_a_condition.png)

Isso significa que, se o usuário selecionar um veículo comercial, o formulário oferece as seguintes opções:

![](assets/s_ncs_admin_survey_no_storage_condb.png)

## Uso das informações coletadas {#using-collected-information}

Para cada formulário, as respostas fornecidas podem ser reutilizadas nos campos ou nos rótulos. As seguintes sintaxes devem ser usadas:

* Para um conteúdo armazenado em um campo do banco de dados:

   ```
   <%=ctx.recipient.@field name%
   ```

* Para um conteúdo armazenado em uma variável local:

   ```
   <%= ctx.vars.variable name %
   ```

* Para um conteúdo armazenado em um campo de texto HTML:

   ```
   <%== HTML field name %
   ```

   >[!NOTE]
   >
   >Unlike the other fields for which `<%=` characters are replaced with escape characters, the HTML content is saved as is by using the `<%==` syntax.

## Salvamento das respostas dos formulários web {#saving-web-forms-answers}

Para salvar as informações coletadas nas páginas de um formulário, você precisa colocar uma caixa de armazenamento no diagrama.

![](assets/s_ncs_admin_survey_save_box.png)

Há duas maneiras de usar essa caixa:

* If the Web form is accessed via a link sent in an email, and if the user accessing the application is already in the database, you can check the **[!UICONTROL Update the preloaded record]** option. Para obter mais informações, consulte [Entrega de um formulário por email](../../web/using/publishing-a-web-form.md#delivering-a-form-via-email).

   Nesse caso, o Adobe Campaign usa a chave primária criptografada do perfil do usuário, um identificador exclusivo atribuído a cada perfil pelo Adobe Campaign. Você precisa configurar as informações para pré-carregar a caixa de pré-carregamento. Para obter mais informações, consulte [Pré-carregamento dos dados](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data)do formulário.

   >[!CAUTION]
   >
   >Essa opção substitui os dados do usuário, incluindo o endereço de email, se houver um campo no qual ele será inserido. Ela não pode ser usada para criar novos perfis e requer o uso de uma caixa de pré-carregamento no formulário.

* Para enriquecer os dados dos recipients no banco de dados, edite a caixa de armazenamento e selecione a chave de reconciliação. Para uso interno (normalmente um sistema de intranet) ou para um formulário usado para criar novos perfis por exemplo, você pode selecionar o(s) campo(s) de reconciliação. A caixa oferece todos os campos do banco de dados usados nas várias páginas da aplicação web:

   ![](assets/s_ncs_admin_survey_save_box_edit.png)

By default, the data is imported into the database by an **[!UICONTROL Update or insertion]** operation: if it exists in the database, the element is updated (for example, the selected newsletter or the e-mail address entered). Se não existir, as informações serão adicionadas.

Você pode, entretanto, alterar esse comportamento. Para fazer isso, selecione a raiz do elemento e selecione a operação a ser executada na lista suspensa:

![](assets/s_ncs_admin_survey_save_operation.png)

Você pode selecionar uma pasta de pesquisa para a reconciliação e a pasta de criação para novos perfis. Se esses campos estiverem vazios, os perfis serão procurados e criados na pasta padrão do operador.

>[!NOTE]
>
>As possíveis operações são: **[!UICONTROL Simple reconciliation]**, **[!UICONTROL Update or insertion]**, **[!UICONTROL Insertion]**, **[!UICONTROL Update]**, **[!UICONTROL Deletion]**.\
>A pasta padrão de um operador é a primeira pasta a que o operador tem permissão de gravação.\
>Consulte [esta seção](../../platform/using/access-management.md).

