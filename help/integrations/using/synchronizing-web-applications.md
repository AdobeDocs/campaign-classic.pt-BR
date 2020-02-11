---
title: Sincronização de aplicações Web
seo-title: Sincronização de aplicações Web
description: Sincronização de aplicações Web
seo-description: null
page-status-flag: never-activated
uuid: da74e4d3-e439-454a-8a43-6784e4789d1b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: df68ab11-7a8b-4e89-8cc4-8764e8a859b2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Sincronização de aplicações Web{#synchronizing-web-applications}

Nesse caso de uso, enviaremos uma comunicação usando o Campaign Standard, que inclui um link para uma aplicação Web do Campaign v7. Quando o recipient clica no link do email, a aplicação Web exibe um formulário contendo vários campos pré-carregados com os dados do recipient, bem como um link de assinatura para um boletim informativo. O recipient pode atualizar seus dados e se inscrever no serviço. Seu perfil será atualizado no Campaign v7 e as informações serão replicadas no Campaign Standard.

Se você tiver muitos serviços e aplicações Web no Campaign v7, talvez opte por não recriá-los no Campaign Standard. O Connector ACS permite usar todas as aplicações Web e serviços existentes no Campaign v7 e vinculá-los a um delivery enviado pelo Campaign Standard.

## Pré-requisitos {#prerequisites}

Para isso, é necessário:

* Os recipients armazenados no banco de dados do Campaign v7 e sincronizados com o Campaign Standard. Consulte a seção Perfis [de](../../integrations/using/synchronizing-profiles.md) sincronização.
* um serviço e uma aplicação Web criado e publicado no Campaign v7.
* the web application must contain a **[!UICONTROL Pre-loading]** activity using the **[!UICONTROL Adobe Campaign encryption]** identification method.

## Criação do serviço e aplicação Web {#creating-the-web-application-and-service}

No Campaign v7, você pode criar aplicações Web que permitem aos recipients assinar um serviço. Os serviço e aplicação Web foram projetados e armazenados no Campaign v7 e você pode atualizar esse serviço por uma comunicação no Campaign Standard. Para obter mais informações sobre aplicações Web no Campaign v7, consulte [esta seção](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes).

No Campaign v7, os seguintes objetos foram criados:

* um serviço de boletim informativo
* um aplicativo da Web que contém uma **[!UICONTROL Pre-loading]**, uma **[!UICONTROL Page]** e uma **[!UICONTROL Storage]** atividade.

1. Go to **[!UICONTROL Resources > Online > Web applications]** and select an existing web application.

   ![](assets/acs_connect_lp_2.png)

1. Edite a **[!UICONTROL Preloading]** atividade. A **[!UICONTROL Auto-load data referenced in the form]** **[!UICONTROL Adobe Campaign encryption]** caixa é marcada e o método de identificação é selecionado. Isso permitirá que a aplicação Web pré-carregue os campos do formulário com os dados armazenados no banco de dados do Adobe Campaign. Consulte [este documento](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

   ![](assets/acs_connect_lp_4.png)

1. Edite o **[!UICONTROL Page]**. Three fields (Name, Email and Phone) have been included, as well as a check box to invite the recipient to subscribe to a newsletter (**[!UICONTROL Newsletter]** service).

   ![](assets/acs_connect_lp_3.png)

1. Vá até **[!UICONTROL Profiles and Target > Services and subscriptions]** e abra o **[!UICONTROL Newsletter]** serviço. Esse é o serviço que será atualizado na comunicação do Campaign Standard. Você pode ver que nenhum recipient assinou esse serviço ainda.

   ![](assets/acs_connect_lp_5.png)

1. Vá para **[!UICONTROL Profiles and Targets > Recipient]** e selecione um destinatário. Você pode ver que ele não assinou o serviço ainda.

   ![](assets/acs_connect_lp_6.png)

## Replicação de dados {#replicating-the-data}

Para replicar os dados necessários entre o Campaign v7 e o Campaign Standard, vários templates de workflow de replicação estão disponíveis. The **[!UICONTROL Profiles replication]** workflow automatically replicates all the Campaign v7 recipients to Campaign Standard. See [Technical and replication workflows](../../integrations/using/acs-connector-principles-and-data-cycle.md#technical-and-replication-workflows). The **[!UICONTROL Landing pages replication]** workflow enables the replication of the web applications we want to use in Campaign Standard.

![](assets/acs_connect_lp_1.png)

Para verificar se os dados foram replicados corretamente, siga essas etapas no Campaign Standard:

1. From the home screen, click on **[!UICONTROL Customer profiles]**.

   ![](assets/acs_connect_lp_7.png)

1. Pesquise o recipient no Campaign v7 e verifique se ele aparece no Campaign Standard.

   ![](assets/acs_connect_lp_8.png)

1. From the top bar, click on **[!UICONTROL Marketing activities]**, and search for the Campaign v7 web application. Ela aparece como uma landing page no Campaign Standard.

   ![](assets/acs_connect_lp_9.png)

1. Click the **[!UICONTROL Adobe Campaign]** logo, in the top left corner, then select **Profiles &amp; audiences > Services** and check that the newsletter service is there as well.

   ![](assets/acs_connect_lp_10.png)

## Design e envio de email {#designing-and-sending-the-email}

Nessa parte, veremos como incluir um link, em um email do Campaign Standard, na landing page replicada de uma aplicação Web do Campaign v7.

As etapas para criar, projetar e enviar o email são iguais de um email clássico. Consulte a documentação do [Adobe Campaign Standard](https://helpx.adobe.com/support/campaign/standard.html) .

1. Crie um novo email e escolha um ou mais perfis replicados como o público.
1. Edite seu conteúdo e insira um **[!UICONTROL Link to a landing page]**.

   ![](assets/acs_connect_lp_12.png)

1. Selecione a landing page que foi replicada da aplicação Web do Campaign v7.

   ![](assets/acs_connect_lp_13.png)

1. Prepare seu e-mail, envie suas provas e envie o email final.
1. Um dos recipients abre o email e clica no link para a assinatura do boletim informativo.

   ![](assets/acs_connect_lp_14.png)

1. Ele adiciona um número de telefone e marca a caixa de seleção da assinatura do boletim informativo.

   ![](assets/acs_connect_lp_15.png)

## Recuperação de informações atualizadas {#retrieving-the-updated-information}

Quando o recipient atualiza seus dados pela aplicação Web, o Adobe Campaign v7 recupera de forma síncrona as informações atualizadas. Ele é replicado do Campaign v7 para o Campaign Standard.

1. No Campaign v7, acesse **[!UICONTROL Profiles and Target > Services and subscriptions]** e abra o **[!UICONTROL Newsletter]** serviço. Você pode ver que o recipient agora aparece na lista de assinantes.

   ![](assets/acs_connect_lp_16.png)

1. Vá até **[!UICONTROL Profiles and Targets > Recipient]** e selecione o destinatário. Você pode ver que o número de telefone agora está registrado.

   ![](assets/acs_connect_lp_17.png)

1. In the **[!UICONTROL Subscriptions]** tab, we can also see that he has subscribed to the newsletter service.

   ![](assets/acs_connect_lp_18.png)

1. Aguarde alguns minutos para que o workflow de replicação de perfil seja executado.
1. No Campaign Standard, acesse o perfil do recipient para verificar se os dados atualizados foram replicados corretamente do Campaign v7.

   ![](assets/acs_connect_lp_19.png)

1. Edite o perfil. Você pode ver que o número de telefone foi atualizado.

   ![](assets/acs_connect_lp_20.png)

1. Click on the **[!UICONTROL Subscriptions]** tab. O serviço de boletim informativo agora aparece.

   ![](assets/acs_connect_lp_21.png)

