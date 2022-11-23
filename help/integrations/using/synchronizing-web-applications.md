---
product: campaign
title: Sincronizar aplicativos web
description: Saiba como sincronizar aplicativos web com o ACS Connector
feature: ACS Connector
hide: true
hidefromtoc: true
exl-id: 975bdc94-5da4-45ae-a3bd-e8674b447098
source-git-commit: 978da934b483a54509ad806f375d9b2bb0577dac
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Sincronizar aplicativos web{#synchronizing-web-applications}

![](../../assets/v7-only.svg)

Nesse caso de uso, enviaremos uma comunicação usando o Campaign Standard, que inclui um link para uma aplicação Web do Campaign v7. Quando o recipient clica no link do email, a aplicação Web exibe um formulário contendo vários campos pré-carregados com os dados do recipient, bem como um link de assinatura para um boletim informativo. O recipient pode atualizar seus dados e se inscrever no serviço. Seu perfil será atualizado no Campaign v7 e as informações serão replicadas no Campaign Standard.

Se você tiver muitos serviços e aplicações Web no Campaign v7, talvez opte por não recriá-los no Campaign Standard. O Connector ACS permite usar todas as aplicações Web e serviços existentes no Campaign v7 e vinculá-los a um delivery enviado pelo Campaign Standard.

## Pré-requisitos {#prerequisites}

Para isso, é necessário:

* Os recipients armazenados no banco de dados do Campaign v7 e sincronizados com o Campaign Standard. Consulte a seção [Sincronizar perfis](../../integrations/using/synchronizing-profiles.md).
* um serviço e um aplicativo web criado e publicado no Campaign v7.
* o aplicativo web deve conter uma atividade **[!UICONTROL Pre-loading]** usando o método de identificação **[!UICONTROL Adobe Campaign encryption]**.

## Criar o serviço e aplicativo web {#creating-the-web-application-and-service}

No Campaign v7, você pode criar aplicações Web que permitem aos recipients assinar um serviço. Os serviço e aplicação Web foram projetados e armazenados no Campaign v7 e você pode atualizar esse serviço por uma comunicação no Campaign Standard. Para obter mais informações sobre aplicações Web no Campaign v7, consulte [esta seção](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes).

No Campaign v7, os seguintes objetos foram criados:

* um serviço de boletim informativo
* um aplicativo web contendo um atividade **[!UICONTROL Pre-loading]**, **[!UICONTROL Page]** e **[!UICONTROL Storage]**.

1. Vá para **[!UICONTROL Resources > Online > Web applications]** e selecione um aplicativo web existente.

   ![](assets/acs_connect_lp_2.png)

1. Editar a atividade **[!UICONTROL Preloading]**. A caixa **[!UICONTROL Auto-load data referenced in the form]** está marcada e o método de identificação **[!UICONTROL Adobe Campaign encryption]** está selecionado. Isso permitirá que a aplicação Web pré-carregue os campos do formulário com os dados armazenados no banco de dados do Adobe Campaign. Consulte [este documento](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

   ![](assets/acs_connect_lp_4.png)

1. Edite o **[!UICONTROL Page]**. Três campos (Name, Email and Phone) foram incluídos, bem como uma caixa de seleção para convidar o recipient para assinar um boletim informativo (serviço de **[!UICONTROL Newsletter]**).

   ![](assets/acs_connect_lp_3.png)

1. Acesse **[!UICONTROL Profiles and Target > Services and subscriptions]** e abra o serviço **[!UICONTROL Newsletter]**. Esse é o serviço que será atualizado na comunicação do Campaign Standard. Você pode ver que nenhum recipient assinou esse serviço ainda.

   ![](assets/acs_connect_lp_5.png)

1. Acesse **[!UICONTROL Profiles and Targets > Recipient]** e selecione um recipient. É possível ver que esse perfil ainda não assinou o serviço.

   ![](assets/acs_connect_lp_6.png)

## Replicar os dados {#replicating-the-data}

Para replicar os dados necessários entre o Campaign v7 e o Campaign Standard, vários modelos de fluxo de trabalho de replicação estão disponíveis. O workflow **[!UICONTROL Profiles replication]** replica automaticamente todos os recipients do Campaign v7 para o Campaign Standard. Consulte [Workflows técnicos e de replicação](../../integrations/using/acs-connector-principles-and-data-cycle.md#technical-and-replication-workflows). O workflow **[!UICONTROL Landing pages replication]** permite a replicação dos aplicativos web que queremos usar no Campaign Standard.

![](assets/acs_connect_lp_1.png)

Para verificar se os dados foram replicados corretamente, siga essas etapas no Campaign Standard:

1. Na tela inicial, clique em **[!UICONTROL Customer profiles]**.

   ![](assets/acs_connect_lp_7.png)

1. Pesquise pelo recipient do Campaign v7 e verifique se ele aparece no Campaign Standard.

   ![](assets/acs_connect_lp_8.png)

1. Na barra superior, clique em **[!UICONTROL Marketing activities]** e procure pelo aplicativo web do Campaign v7. Ela aparece como uma landing page no Campaign Standard.

   ![](assets/acs_connect_lp_9.png)

1. Clique no logotipo do **[!UICONTROL Adobe Campaign]** no canto superior esquerdo e, em seguida, selecione **Profiles and audiences > Services** e verifique se o serviço de boletim informativo está ali também.

   ![](assets/acs_connect_lp_10.png)

## Criar e enviar o email {#designing-and-sending-the-email}

Nessa parte, veremos como incluir um link, em um email do Campaign Standard, na landing page replicada de uma aplicação Web do Campaign v7.

As etapas para criar, projetar e enviar o email são iguais de um email clássico. Consulte a documentação do [Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/campaign-standard-home.html?lang=pt-BR) .

1. Crie um novo email e escolha um ou mais perfis replicados como o público.
1. Editar seu conteúdo e inserir um **[!UICONTROL Link to a landing page]**.

   ![](assets/acs_connect_lp_12.png)

1. Selecione a landing page que foi replicada da aplicação Web do Campaign v7.

   ![](assets/acs_connect_lp_13.png)

1. Prepare seu e-mail, envie suas provas e envie o email final.
1. Um dos recipients abre o email e clica no link para a assinatura do boletim informativo.

   ![](assets/acs_connect_lp_14.png)

1. Esse recipient adiciona um número de telefone e marca a caixa de seleção da assinatura do boletim informativo.

   ![](assets/acs_connect_lp_15.png)

## Recuperação de informações atualizadas {#retrieving-the-updated-information}

Quando o recipient atualiza seus dados pela aplicação Web, o Adobe Campaign v7 recupera de forma síncrona as informações atualizadas. Ele é replicado do Campaign v7 para o Campaign Standard.

1. No Campaign v7, acesse **[!UICONTROL Profiles and Target > Services and subscriptions]** e abra o serviço **[!UICONTROL Newsletter]**. Você pode ver que o recipient agora aparece na lista de assinantes.

   ![](assets/acs_connect_lp_16.png)

1. Acesse **[!UICONTROL Profiles and Targets > Recipient]** e selecione o recipient. Você pode ver que o número de telefone agora está registrado.

   ![](assets/acs_connect_lp_17.png)

1. Na guia **[!UICONTROL Subscriptions]**, também podemos ver que ele assinou o serviço de boletim informativo.

   ![](assets/acs_connect_lp_18.png)

1. Aguarde alguns minutos para que o workflow de replicação de perfil seja executado.
1. No Campaign Standard, acesse o perfil do recipient para verificar se os dados atualizados foram replicados corretamente do Campaign v7.

   ![](assets/acs_connect_lp_19.png)

1. Edite o perfil. Você pode ver que o número de telefone foi atualizado.

   ![](assets/acs_connect_lp_20.png)

1. Clique na guia **[!UICONTROL Subscriptions]**. O serviço de boletim informativo agora aparece.

   ![](assets/acs_connect_lp_21.png)
