---
title: Publicação de um formulário web
seo-title: Publicação de um formulário web
description: Publicação de um formulário web
seo-description: null
page-status-flag: never-activated
uuid: 37222829-1d56-438c-a4ca-878925debcb5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: f4322902-c72d-4443-9c30-09add4c615a3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Publicação de um formulário web{#publishing-a-web-form}

## Pré-carregamento dos dados do formulário {#pre-loading-the-form-data}

Se quiser atualizar os perfis armazenados no banco de dados por meio de um formulário web, use uma caixa de pré-carregamento. A caixa de pré-carregamento permite indicar como localizar o registro a ser atualizado no banco de dados.

Os seguintes métodos de identificação são possíveis:

* **[!UICONTROL Adobe Campaign Encryption]**

   Esse método de criptografia usa o identificador (ID) criptografado do Adobe Campaign. Esse método só é aplicável em um objeto do Adobe Campaign e a ID criptografada só pode ser gerada pela plataforma Adobe Campaign.

   When using this method, you need to adapt the URL of the form to deliver to the email address by adding the **`<%=escapeUrl(recipient.cryptedId) %>`** parameter. Para obter mais informações, consulte [Entrega de um formulário por email](#delivering-a-form-via-email).

* **[!UICONTROL DES encryption]**

   ![](assets/s_ncs_admin_survey_preload_methods_001.png)

   Esse método de criptografia usa um identificador (ID) fornecido externamente, vinculado a uma chave compartilhada pela Adobe Campaign e pelo provedor externo. The **[!UICONTROL Des key]** field lets you enter this encryption key.

* **[!UICONTROL List of fields]**

   Essa opção permite escolher entre os campos no contexto atual do formulário, aquelas que serão usadas para localizar o perfil correspondente no banco de dados.

   ![](assets/s_ncs_admin_survey_preload_methods_002.png)

   Fields can be added to the form properties via the **[!UICONTROL Parameters]** tab (refer to [Adding parameters](../../web/using/defining-web-forms-properties.md#adding-parameters)). Eles são colocados na URL do formulário ou nas zonas de entrada.

   >[!CAUTION]
   >
   >Os dados nos campos selecionados não estão criptografados. It must not be provided in an encrypted form because Adobe Campaign will not be able to decrypt it if the **[!UICONTROL Field list]** option is selected.

   No exemplo a seguir, o pré-carregamento de perfis é baseado no endereço de email.

   A URL pode incluir o endereço de email não criptografado, nesse caso, os usuários têm acesso direto às páginas referentes.

   ![](assets/s_ncs_admin_survey_preload_methods_003.png)

   Caso contrário, eles serão solicitados a fornecer sua senha.

   ![](assets/s_ncs_admin_survey_preload_methods_004.png)

   >[!CAUTION]
   >
   >Se vários campos forem especificados na lista, os dados de **TODOS OS CAMPOS** deverão corresponder aos dados armazenados no banco de dados para que o perfil seja atualizado. Caso contrário, um novo perfil será criado.
   > 
   >Essa função é particularmente útil para aplicações web, mas não recomendada para formulários públicos. A opção de controle de acesso selecionado deve ser &quot;Habilitar controle de acesso&quot;.

The **[!UICONTROL Skip preloading if identification is empty]** option must be selected if you do not wish to update profiles. Nesse caso, cada perfil inserido será adicionado ao banco de dados após a aprovação do formulário. Essa opção é usada, por exemplo, quando o formulário é postado em um site.

The **[!UICONTROL Auto-load data referenced in the form]** option lets you automatically preload the data that matches input and merge fields in the form. No entanto, os dados referenciados nas **[!UICONTROL Script]** atividades e nas **[!UICONTROL Test]** atividades não são afetados. If this option isn&#39;t selected, you need to define the fields using the **[!UICONTROL Load additional data]** option.

The **[!UICONTROL Load additional data]** option lets you add information which is not used in the pages of the form, but will nonetheless be preloaded.

Você pode, por exemplo, pré-carregar o gênero do recipient e direcionar automaticamente para a página apropriada através de uma caixa de teste.

![](assets/s_ncs_admin_survey_preload_ex.png)

## Gerenciamento do delivery e do rastreamento de formulários web {#managing-web-forms-delivery-and-tracking}

Depois que o formulário tiver sido criado, configurado e publicado, você poderá entregar e controlar as respostas do usuário.

### Ciclo de vida de um formulário {#life-cycle-of-a-form}

Há três estágios no ciclo de vida de um formulário:

1. **Formulário sendo editado**

   Esta é a fase de design inicial. Quando um novo formulário é criado, ele está na fase de edição. Access to the form, for testing purposes only, then requires the parameter **[!UICONTROL __uuid]** to be used in its URL. This URL is accessible in the **[!UICONTROL Preview]** sub-tab. Consulte Parâmetros [do URL do](../../web/using/defining-web-forms-properties.md#form-url-parameters)formulário.

   >[!CAUTION]
   >
   >Desde que o formulário esteja sendo editado, sua URL de acesso é uma URL especial.

1. **Formulário Online**

   Quando a fase de design é concluída, o formulário pode ser entregue. Primeiro, precisa ser publicado. For more on this, refer to [Publishing a form](#publishing-a-form).

   The form will be **[!UICONTROL Live]** until it expires.

   >[!CAUTION]
   >
   >To be delivered, the URL of the survey must not contain the **[!UICONTROL __uuid]** parameter.

1. **Formulário indisponível**

   Depois que o formulário for fechado, a fase de delivery será finalizada e o formulário ficará indisponível: ele não estará mais acessível aos usuários.

   A data de expiração pode ser definida na janela de propriedades do formulário. Para obter mais informações, consulte [Disponibilizar um formulário online](#making-a-form-available-online)

O status da publicação de um formulário é exibido na lista de formulários.

![](assets/s_ncs_admin_survey_status.png)

### Publicação de um formulário {#publishing-a-form}

Para alterar o estado de um formulário, você precisa publicá-lo. To do this, click the **[!UICONTROL Publication]** button above the list of Web forms and select the state in the drop-down box.

![](assets/webapp_publish_webform.png)

### Disponibilização de um formulário online {#making-a-form-available-online}

Para ser acessado por usuários, o formulário deve estar em produção e iniciado, ou seja, dentro de seu período de validade. The validity dates are entered via the **[!UICONTROL Properties]** link of the form.

* Use the fields in the **[!UICONTROL Project]** section to enter start and end dates for the form.

   ![](assets/webapp_availability_date.png)

* Click the **[!UICONTROL Personalize the message displayed if the form is closed...]** link to define the error message to display if the user tries to access the form while it isn&#39;t valid.

   See [Accessibility of the form](../../web/using/defining-web-forms-properties.md#accessibility-of-the-form).

### Delivery de um formulário por email {#delivering-a-form-via-email}

When you deliver an invitation via email, you can use the **[!UICONTROL Adobe Campaign Encryption]** option for data reconciliation. Para fazer isso, vá para o assistente do delivery e adapte o link ao formulário adicionando o seguinte parâmetro:

```
<a href="https://server/webApp/APP264?&id=<%=escapeUrl(recipient.cryptedId) %>">
```

Nesse caso, a chave de reconciliação para o armazenamento de dados deve ser o identificador criptografado do recipient. Para obter mais informações, consulte [Pré-carregamento dos dados](#pre-loading-the-form-data)do formulário.

In this case, you need to check the **[!UICONTROL Update the preloaded record]** option in the record box. Para obter mais informações, consulte [Salvar respostas](../../web/using/web-forms-answers.md#saving-web-forms-answers)a formulários da Web.

![](assets/s_ncs_admin_survey_save_box_option.png)

### Registrar respostas {#log-responses}

O rastreamento de resposta pode ser ativado em uma guia dedicada para monitorar o impacto do seu formulário web. To do this, click the **[!UICONTROL Advanced parameters...]** link in the form properties window and select the **[!UICONTROL Log responses]** option.

![](assets/s_ncs_admin_survey_trace.png)

The **[!UICONTROL Responses]** tab appears to let you view the identity of respondents.

![](assets/s_ncs_admin_survey_trace_tab.png)

Select a recipient and click the **[!UICONTROL Detail...]** button to view the responses provided.

![](assets/s_ncs_admin_survey_trace_edit.png)

Você pode processar os logs de resposta fornecidos em queries, por exemplo, para direcionar somente aqueles que não responderam ao enviar lembretes ou oferecer comunicações específicas apenas aos que responderam.

>[!NOTE]
>
>Para obter um rastreamento completo das respostas fornecidas, exporte as respostas e exiba ou crie relatórios dedicados, use o módulo opcional de **Pesquisa.** Para obter mais informações, consulte [esta seção](../../web/using/about-surveys.md).

