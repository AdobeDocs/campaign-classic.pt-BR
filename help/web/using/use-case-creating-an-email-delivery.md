---
product: campaign
title: 'Caso de uso: criar uma entrega por email'
description: 'Caso de uso: criar uma entrega por email'
badge-v8: label="Também se aplica à versão v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Web Apps, Web Forms, Landing Pages, Email Design
exl-id: e2679f12-459b-466d-9c82-60a28363b104
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 99%

---

# Caso de uso: criar uma entrega por email{#use-case-creating-an-email-delivery}



Nesse caso de uso, você aprenderá as etapas para projetar uma entrega de email usando o Adobe Campaign Digital Content Editor (DCE).

Nosso objetivo final é criar uma entrega com um template personalizado que contém:

* Um endereço direto para um destinatário (usando nome e sobrenome)
* Dois tipos de links para uma URL externa
* Uma mirror page
* Um link para uma aplicação web

>[!NOTE]
>
>Antes de começar, você deve ter pelo menos um **template HTML** configurado para hospedar o conteúdo de suas entregas futuras.
>
>No **[!UICONTROL Properties]** da entrega, verifique se **[!UICONTROL Content editing mode]** (na guia **[!UICONTROL Advanced]**) está definido como **[!UICONTROL DCE]**. Para garantir a operação ideal do editor, consulte [Práticas recomendadas de edição de conteúdo](content-editing-best-practices.md).

## Etapa 1 - Criação de uma entrega {#step-1---creating-a-delivery}

Para criar uma nova entrega, coloque o cursor na guia **Campaigns** e clique em **Entregas**. Clique no botão **Criar** acima da lista de entregas existentes. Para obter mais informações sobre criação de entregas, consulte [esta página](../../delivery/using/about-email-channel.md).

![](assets/delivery_step_1.png)

## Etapa 2 - Seleção de um modelo {#step-2---selecting-a-template}

Selecione um template da entrega e nomeie a entrega. Esse nome só será visível para os usuários do console do Adobe Campaign e não por seus destinatários, no entanto, esse título será exibido na lista de entregas. Clique em **[!UICONTROL Continue]**.

![](assets/dce_delivery_model.png)

## Etapa 3 - Seleção de um conteúdo {#step-3---selecting-a-content}

O Editor de conteúdo digital vem com vários modelos prontos para uso com várias estruturas (colunas, áreas de texto, etc.).

Selecione o template de conteúdo que deseja usar e clique no botão **[!UICONTROL Start with the selected content]** para exibir o template na entrega criada.

![](assets/dce_select_model.png)

Você também pode importar um conteúdo HTML criado fora do Adobe Campaign selecionando **[!UICONTROL From a file]**.

![](assets/dce_select_from_file_template.png)

Você pode salvar esse conteúdo como um template para uso futuro. Após criar um template de conteúdo personalizado, é possível pré-visualizá-lo na lista de templates. Para saber mais, consulte [Gerenciamento de template](template-management.md).

>[!CAUTION]
>
>Se estiver usando a **interface da Web do Adobe Campaign**, você deve importar um arquivo .zip com o conteúdo HTML e imagens relacionadas.

## Etapa 4 — design da mensagem {#step-4---designing-the-message}

* Exiba o nome e o sobrenome dos destinatários

  Para inserir o nome e o sobrenome dos destinatários em um campo de texto na entrega, clique no campo de texto escolhido e coloque o cursor onde deseja exibi-los. Clique no primeiro ícone na barra de ferramentas pop-up e, depois, em **[!UICONTROL Personalization block]**. Selecione **[!UICONTROL Greetings]** e clique em **[!UICONTROL OK]**.

  ![](assets/dce_personalizationblock_greetings.png)

* Inserir um link em uma imagem

  Para levar os destinatários da entrega para um endereço externo por meio de uma imagem, clique na imagem relevante para exibir a barra de ferramentas pop-up, coloque o cursor no primeiro ícone e clique em **[!UICONTROL Link to an external URL]**. Para saber mais, consulte [Adição de um link](editing-content.md#adding-a-link).

  ![](assets/dce_externalpage.png)

  Insira a URL do link no campo **URL** usando o seguinte formato **https://www.myURL.com** e, em seguida, confirme.

  O link pode ser alterado a qualquer momento usando a seção à direita da janela.

* Inserir um link no texto

  Para integrar um link externo ao texto na sua entrega, selecione um texto ou um bloco de texto e clique no primeiro ícone na barra de ferramentas pop-up. Clique em **[!UICONTROL Link to an external URL]** e digite o endereço do link no campo **[!UICONTROL URL]**. Para saber mais, consulte [Adição de um link](editing-content.md#adding-a-link).

  O link pode ser alterado a qualquer momento usando a seção à direita da janela.

  >[!CAUTION]
  >
  >O texto inserido no campo **[!UICONTROL Label]** substitui o texto original.

* Adicionar uma mirror page

  Para permitir que os destinatários vejam o conteúdo da entrega em um navegador da Web, você pode integrar um link a uma mirror page na entrega.

  Clique no campo de texto em que você deseja ver o link publicado. Clique no primeiro ícone na barra de ferramentas pop-up, selecione **[!UICONTROL Personalization block]** e, então, **[!UICONTROL Link to Mirror Page (MirrorPage)]**. Clique em **[!UICONTROL Save]** para confirmar.

  ![](assets/dce_mirrorpage.png)

  >[!CAUTION]
  >
  >O rótulo de bloco de personalização substitui automaticamente o texto original na sua entrega.

* Integrar um link a uma aplicação web

  O Editor de conteúdo digital permite integrar links às aplicações web no console do Adobe Campaign, como uma landing page ou uma página de formulário. Para saber mais, consulte [Vincular a uma aplicação web](editing-content.md#link-to-a-web-application).

  Selecione um campo de texto para seu link para uma aplicação web e clique no primeiro ícone. Escolha **[!UICONTROL Link to a Web application]** e selecione a aplicação desejada clicando no ícone no final do campo **Web Application**.

  ![](assets/dce_webapp.png)

  Clique em **Salvar** para confirmar.

  >[!NOTE]
  >
  >Esta etapa exige que você salve pelo menos uma aplicação web anteriormente. Essas aplicações podem ser encontradas na guia **[!UICONTROL Campaigns > Web applications]** do console.

## Etapa 5 - Salvar a entrega {#step-5---saving-the-delivery}

Quando o conteúdo for integrado, salve a entrega clicando em **Salvar**. Agora ele será exibido na lista de entregas, encontrada na guia **[!UICONTROL Campaigns > Deliveries]**.
