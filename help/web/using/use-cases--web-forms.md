---
title: '"Casos de uso: formulários web"'
seo-title: '"Casos de uso: formulários web"'
description: '"Casos de uso: formulários web"'
seo-description: null
page-status-flag: never-activated
uuid: b2c3f171-325e-4913-a188-a791bad0df2e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: cfa22577-0b9e-4eee-900d-214b81256d81
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Casos de uso: formulários web{#use-cases-web-forms}

## Crie um formulário de subscrição com opt in duplo {#create-a-subscription--form-with-double-opt-in}

Quando você oferece serviços de informação, os recipients precisam se subscrever para receber todas as comunicações vinculadas. Para evitar comunicações inadequadas e verificar se o recipient se subscreveu intencionalmente, recomendamos enviar uma solicitação de confirmação da subscrição para criar um opt in duplo. A subscrição só entrará em vigor depois que o usuário clicar no link incluído na mensagem de confirmação.

Este exemplo é baseado no seguinte cenário:

1. Criação de um formulário de subscrição do boletim informativo em um site que contém uma caixa de seleção para subscrição de um serviço temporário. Esse serviço permitirá que você forneça mensagens de confirmação da subscrição.
1. Criação do delivery de confirmação da subscrição com um template do delivery vinculado ao formulário web. Ele contém o link de confirmação que chama o formulário da subscrição do boletim informativo e exibe uma mensagem de aprovação de subscrição.

### Etapa 1 - Criação dos serviços de informação {#step-1---creating-information-services}

1. Crie a subscrição no serviço de boletim informativo a ser oferecido aos recipients. Para obter mais informações sobre como criar um boletim informativo, consulte [esta seção](../../delivery/using/about-services-and-subscriptions.md).

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1.png)

1. Crie um segundo serviço de informação, um serviço temporário vinculado a um template do delivery para enviar mensagens de confirmação da subscrição.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1c.png)

### Etapa 2 - Criação das mensagens de confirmação {#step-2---creating-confirmation-messages}

As mensagens de confirmação são enviadas por um template do delivery dedicado referenciado no nível de serviço temporário.

1. No **[!UICONTROL Explorer]** , selecione **[!UICONTROL Resources > Templates > Delivery templates]**.
1. Crie um template do delivery para enviar as mensagens de confirmação da subscrição.
1. Click the **[!UICONTROL To]** button in the **[!UICONTROL Email parameters]** to associate the delivery template with the Subscriptions target mapping instead of Recipients.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1d.png)

1. Como os recipients desse delivery não confirmaram sua aprovação, eles ainda estão incluídos na blacklist do banco de dados. Para receber essa comunicação, você precisa autorizar os deliveries com base nesse template a fim de direcionar recipients incluídos na blacklist.

   To do this, click the **[!UICONTROL Exclusions]** tab.

1. Clique no **[!UICONTROL Edit...]** link e desmarque a **[!UICONTROL Exclude recipients who no longer want to be contacted (blacklist)]** opção.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_4d.png)

   >[!CAUTION]
   >
   >Essa opção pode ser desabilitada somente nesse tipo de contexto.

1. Personalize o delivery e insira o link de confirmação no conteúdo da mensagem. Esse link permite que você acesse o formulário web para registrar a confirmação da subscrição.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1b.png)

1. Com o DCE, vincule sua URL ao formulário web. Como o formulário web ainda não foi criado, substitua o valor assim que criá-lo.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_3.png)

1. Finalmente, vincule esse template ao serviço temporário criado anteriormente.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_3c.png)

### Etapa 3 – Criação do formulário de subscrição {#step-3---creating-the-subscription-form}

O formulário web habilita a subscrição do recipient e a confirmação da subscrição.

O workflow do formulário web incluirá as seguintes atividades:

![](assets/s_ncs_admin_survey_double-opt-in_sample_4c.png)

Para fazer isso, siga as etapas abaixo:

1. Create a Web form and choose the template **[!UICONTROL Newsletter subscription (subNewsletter)]**.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5a.png)

1. In the **[!UICONTROL Edit]** tab, we need to configure the existing workflow since we want to add a confirmation message to the recipients who want to subscribe.

   To do so, double-click the **[!UICONTROL Preloading]** box and configure it as follows.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5b.png)

   Isso significa que, se o usuário acessar esse formulário por meio do link na mensagem de confirmação, suas informações de perfil serão carregadas. Se ele acessar o formulário web por meio de uma página do site, nenhuma informação será carregada.

1. Add a **[!UICONTROL Test]** activity to your workflow.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6e.png)

   The **[!UICONTROL Test]** activity can concern the recipient email. Nesse caso, configure-a da seguinte maneira:

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6d.png)

1. Add two **[!UICONTROL Script]** activities to your workflow.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6f.png)

   The first **[!UICONTROL Script]** activity will blacklist recipients until they confirmed their subscription to the newsletter. Seu conteúdo deve ser o seguinte:

   ```
   ctx.recipient.@blackList=1
   ```

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6bbis.png)

   The second **[!UICONTROL Script]** activity authorizes deliveries to be send to the users and subscribes them to the newsletter. As duas últimas linhas do script permitirão transferir os recipients da pasta temporária para outra pasta e reconciliar com perfis existentes assim que confirmarem a subscrição.

   ```
   ctx.recipient.@blackList=0
   nms.subscription.Subscribe("INTERNAL_NAME_OF_THE_NEWSLETTER", ctx.recipient, false)
   ctx.recipient.folder = <folder name="nmsRootRecipient"/>
   nms.subscription.Unsubscribe("TEMP", ctx.recipient)
   ```

   >[!NOTE]
   >
   >The **[!UICONTROL Temp]** partition can also be purged on a regular basis using a workflow.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6b.png)

1. Double-click the **[!UICONTROL Subscription]** activity to personalize the subscription form and link a checkbox with the temporary service previously created.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5c.png)

1. Configure the **[!UICONTROL Storage]** activity to save the information entered in the form page.

   Essa atividade permite que você crie perfis de recipients em uma pasta temporária dedicada para separá-los dos perfis no banco de dados, para quem as comunicações podem ser enviadas.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5g.png)

   >[!NOTE]
   >
   >Você não deve definir opções de reconciliação.

1. Add two **[!UICONTROL End]** activities to display a message for the user.

   The second **[!UICONTROL End]** box will display the confirmation message once the subscription is complete.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5h.png)

1. Depois que o formulário web é criado e configurado, você pode referenciá-lo no template do delivery para enviar mensagens de confirmação.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_7b.png)

### Etapa 4 - Publicação e teste do formulário {#step-4---publishing-and-testing-the-form}

Agora você pode publicar o formulário para torná-lo acessível aos usuários.

![](assets/s_ncs_admin_survey_double-opt-in_sample_8b.png)

A subscrição no boletim informativo envolve as seguintes etapas:

1. O usuário do site entra na página de subscrição e aprova o formulário.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8c.png)

   Ele é notificado por meio de uma mensagem em seu navegador de que sua solicitação foi levada em conta.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8d.png)

   The user is added to the Adobe Campaign database in the **[!UICONTROL Temp]** folder, and their profile is blacklisted until they confirm their subscription with the email.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8f.png)

1. Uma mensagem de confirmação que inclui um link para aprovar a subscrição é enviada para o usuário.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8e.png)

1. Ao clicar nesse link, a página de aprovação é exibida no navegador.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8.png)

   No Adobe Campaign, o perfil do usuário é atualizado:

   * eles não estão mais incluídos na blacklist,
   * eles estão subscritos no serviço de informação.

      ![](assets/s_ncs_admin_survey_double-opt-in_sample_9.png)

## Exibição de diferentes opções dependendo dos valores selecionados {#displaying-different-options-depending-on-the-selected-values}

No exemplo a seguir, o usuário é solicitado a selecionar um tipo de veículo. Você pode exibir as categorias de veículo disponíveis de acordo com o tipo selecionado. Isso significa que os itens exibidos na coluna à direita dependem da seleção do usuário:

![](assets/s_ncs_admin_survey_condition_sample0.png)

* Quando o usuário seleciona &quot;veículo privado&quot;, a escolha entre &quot;Compacto&quot; e &quot;Minivan&quot; é oferecida.

   ![](assets/s_ncs_admin_survey_condition_sample2.png)

* Quando o usuário seleciona &quot;veículo comercial&quot;, uma seleção é exibida em uma lista suspensa:

   ![](assets/s_ncs_admin_survey_condition_sample1.png)

Nesse exemplo, o tipo de veículo não é armazenado no banco de dados. A lista suspensa é configurada da seguinte maneira:

![](assets/s_ncs_admin_survey_condition_config1.png)

Essas informações são armazenadas em uma variável local.

A exibição condicional da coluna à direita é configurada nos containers:

![](assets/s_ncs_admin_survey_condition_config1bis.png)

* Visibilidade condicional de campos para um veículo privado:

   ![](assets/s_ncs_admin_survey_condition_config2.png)

* Visibilidade condicional de campos para um veículo comercial:

   ![](assets/s_ncs_admin_survey_condition_config3.png)

