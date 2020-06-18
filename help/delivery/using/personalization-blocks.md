---
title: Blocos de personalização
seo-title: Blocos de personalização
description: Blocos de personalização
seo-description: null
page-status-flag: never-activated
uuid: f9867f8d-f6ce-4a5f-b6b4-fd8056d28576
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: e68d1435-70e6-479e-a347-9ff9f9f11b92
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fa9e4ddc716809b96e259acd1137a0c24ef68fee
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 72%

---


# Blocos de personalização{#personalization-blocks}

Os blocos de personalização são dinâmicos, personalizados e contêm uma renderização específica que pode ser inserida em seus deliveries. Por exemplo, você pode adicionar um logotipo, uma mensagem de saudação ou um link para uma mirror page. Consulte [Inserção de blocos de personalização](#inserting-personalization-blocks).

>[!NOTE]
>
>Personalization blocks are also available from the **[!UICONTROL Digital Content Editor (DCE)]** . Para obter mais informações, consulte [esta página](../../web/using/editing-content.md#inserting-a-personalization-block).

Personalization blocks are accessed via the **[!UICONTROL Resources > Campaign Management > Personalization blocks]** node of the Adobe Campaign explorer. Vários blocos estão disponíveis por padrão (consulte [Blocos de personalização prontos para uso](#out-of-the-box-personalization-blocks)).

Você pode definir novos blocos que permitem otimizar a personalização dos deliveries. Para saber mais, consulte [Definição de blocos de personalização customizado](#defining-custom-personalization-blocks).

## Inserir blocos de personalização {#inserting-personalization-blocks}

Para inserir um bloco de personalização em uma mensagem, siga as etapas abaixo:

1. No editor de conteúdo do assistente de delivery, clique no ícone do campo de personalização e selecione o menu **[!UICONTROL Include]**.
1. Select a personalization block from the list (the list displays the 10 last used blocks), or click the **[!UICONTROL Other...]** menu to access the full list.

   ![](assets/s_ncs_user_personalized_block01.png)

1. The **[!UICONTROL Other...]** menu gives access to all the out-of-the-box and custom personalization blocks (see [Out-of-the-box personalization blocks](#out-of-the-box-personalization-blocks) and [Defining custom personalization blocks](#defining-custom-personalization-blocks)).

   ![](assets/s_ncs_user_personalized_block02.png)

1. O bloco de personalização é então inserido como um script. Ele é adaptado automaticamente ao perfil do recipient quando a personalização é gerada.

   ![](assets/s_ncs_user_personalized_block03.png)

1. Clique na guia **[!UICONTROL Preview]** e selecione um destinatário para exibir a personalização.

   ![](assets/s_ncs_user_personalized_block04.png)

Você pode incluir o código-fonte de um bloco de personalização no conteúdo do delivery. Para fazer isso, selecione **[!UICONTROL Include the HTML source code of the block]** ao selecioná-lo.

![](assets/s_ncs_user_personalized_block05.png)

O código-fonte HTML é inserido no conteúdo de delivery. Por exemplo, o bloco de personalização **[!UICONTROL Greetings]** é exibido conforme mostrado abaixo:

![](assets/s_ncs_user_personalized_block06.png)

## Exemplo de blocos de personalização {#personalization-blocks-example}

Neste exemplo, criamos um email no qual usamos blocos de personalização para permitir que o recipient exiba a mirror page, compartilhe o boletim informativo em redes sociais e cancele a assinatura de deliveries futuros.

Para fazer isso, precisamos inserir os seguintes blocos de personalização:

* **[!UICONTROL Link to mirror page]** .
* **[!UICONTROL Social network sharing links]** .
* **[!UICONTROL Unsubscription link]** .

>[!NOTE]
>
>Para saber mais sobre a geração da mirror page, consulte [Geração da mirror page](../../delivery/using/sending-messages.md#generating-the-mirror-page).

1. Criar um novo delivery ou abrir um tipo de delivery de email existente.
1. No assistente de delivery, clique em **[!UICONTROL Subject]** para editar e inserir o assunto da mensagem.
1. Insira os blocos de personalização no corpo da mensagem. Para fazer isso, clique no conteúdo da mensagem, clique no ícone de campo personalizado e selecione o menu **[!UICONTROL Include]**.
1. Selecione o primeiro bloco a ser inserido. Renove o procedimento para incluir os dois outros blocos.

   ![](assets/s_ncs_user_personalized_block_example.png)

1. Clique na guia **[!UICONTROL Preview]** para exibir o resultado personalizado. Você deve selecionar um recipient para exibir a mensagem dele.

   ![](assets/s_ncs_user_personalized_block_example2.png)

1. Confirme se o conteúdo do bloco é exibido corretamente.

## Blocos de personalização integrados {#out-of-the-box-personalization-blocks}

Uma lista de blocos de personalização está disponível por padrão para ajudar na personalização do conteúdo da sua mensagem.

>[!NOTE]
>
>A lista de blocos de personalização depende dos módulos e das opções que foram instaladas na sua instância.

![](assets/s_ncs_user_personalized_block_list.png)

* **[!UICONTROL Greetings]**: insere saudações com o nome do destinatário. Exemplo: &quot;Olá, John Doe&quot;.
* **[!UICONTROL Insert logo]**: insere um logotipo pronto para uso que foi definido ao configurar a instância.
* **[!UICONTROL Powered by Adobe Campaign]** : insere o logotipo &quot;Powered by Adobe Campaign&quot;.
* **[!UICONTROL Mirror page URL]** : insere o URL do mirror page, permitindo que os designers do Delivery verifiquem o link.

   >[!NOTE]
   >
   >Para saber mais sobre a geração da mirror page, consulte [Geração da mirror page](../../delivery/using/sending-messages.md#generating-the-mirror-page).

* **[!UICONTROL Link to mirror page]**: insere um link para a mirror page (&quot;Se você não conseguir visualizar esta mensagem corretamente, clique aqui&quot;).
* **[!UICONTROL Unsubscription link]** : insere um link que permite cancelar a inscrição de todos os delivery (lista de blocos).
* **[!UICONTROL Formatting function for proper nouns]** : gera a função **[!UICONTROL toSmartCase]** Javascript, que altera a primeira letra de cada palavra para maiúscula. Este bloco deve ser inserido no código-fonte do delivery, nas tags **`<script>...</script>`**.

   No exemplo abaixo, a função é usada para substituir o elemento &quot;My header&quot; por &quot;My new header&quot; com letras maiúsculas em cada palavra:

   ```
   <h1 id="sample">My header</h1>
   <script><%@ include view='toSmartCase'%>;
   document.getElementById("sample").innerHTML = toSmartCase("My new header");
   </script>
   ```

   ![](assets/s_ncs_user_personalized_block_uppercasefunction.png)

* **[!UICONTROL Registration page URL]** : insere um URL de subscrição (consulte [Sobre serviços e subscrição](../../delivery/using/about-services-and-subscriptions.md)).
* **[!UICONTROL Registration link]** : insere um link de subscrição. que foi definido ao configurar a instância.
* **[!UICONTROL Registration link (with referrer)]** : insere um link de subscrição, permitindo identificar o visitante e o delivery. O link foi definido ao configurar a instância.

   >[!NOTE]
   >
   >Este bloco pode ser usado em deliveries somente para visitantes.

* **[!UICONTROL Registration confirmation]** : insere um link que permite confirmar a subscrição.
* **[!UICONTROL Social network sharing links]**:  : insere botões que permitem que o destinatário compartilhe um link para o conteúdo da mirror page no cliente de email, Facebook, Twitter, Google+ e LinkedIn (consulte [Marketing viral: encaminhar para um amigo](../../delivery/using/viral-and-social-marketing.md#viral-marketing--forward-to-a-friend)).
* **[!UICONTROL Style of content emails]** e **[!UICONTROL Notification style]** : gere um código que formate um email com estilos HTML predefinidos. These blocks must be inserted in the source code of the delivery, in the **[!UICONTROL ...]** section, into **`<style>...</style>`** tags.
* **[!UICONTROL Offer acceptance URL in unitary mode]** : insere um URL que permite definir uma oferta de interação como **[!UICONTROL Accepted]** (consulte [esta seção](../../interaction/using/offer-analysis-report.md)).

## Definição de blocos de personalização personalizados {#defining-custom-personalization-blocks}

You can define new personalization fields to be inserted from the personalized field icon via the **[!UICONTROL Include...]** menu. Esses campos são definidos em blocos de personalização.

Para criar um bloco de personalização, vá para o explorador e siga as seguintes etapas:

1. Clique no **[!UICONTROL Resources > Campaign Management > Personalization blocks]** nó.
1. Clique com o botão direito do mouse na lista de blocos e selecione **[!UICONTROL New]**.
1. Preencha as configurações do bloco de personalização:

   ![](assets/s_ncs_user_personalized_block.png)

   * Insira o rótulo do bloco. Esse rótulo será exibido na janela de inserção do campo de personalização.
   * Select **[!UICONTROL Visible in the customization menus]** to make this block accessible from the personalization field insertion icon.
   * If necessary, select **[!UICONTROL The content of the personalization block depends upon the format]** to define two separate blocks for emails in HTML format and those in text format.

      Duas guias são exibidas na seção inferior desse editor (conteúdo HTML e conteúdo de texto) para definir o conteúdo correspondente.

      ![](assets/s_ncs_user_personalized_block_b.png)

   * Insira o conteúdo (em HTML, texto, JavaScript, etc.) do(s) bloco(s) de personalização e clique em **[!UICONTROL Save]**.
