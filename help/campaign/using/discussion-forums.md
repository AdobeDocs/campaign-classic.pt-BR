---
title: Fóruns de discussão
seo-title: Fóruns de discussão
description: Fóruns de discussão
seo-description: null
page-status-flag: never-activated
uuid: 6253bb32-c71d-45ac-bc03-027131ae95a5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
discoiquuid: 88eb17b6-5206-4064-9cd9-b4645a85c609
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 87%

---


# Fóruns de discussão{#discussion-forums}

Os operadores do Adobe Campaign podem usar fóruns de discussão para compartilhar informações. Os elementos a seguir têm seu próprio fórum: planos, programas, campanhas, recursos, simulações, estoques. Cada operador também tem um fórum pessoal. Todas as discussões são públicas, mesmo em fóruns pessoais.

Os operadores podem se inscrever em um fórum para receber um email de notificação sempre que uma mensagem for postada.

## Acessando um fórum {#accessing-a-forum}

Para visitar o fórum de uma campanha, operador etc., vá para o painel e clique no link **[!UICONTROL Forum]** no canto superior direito. Esse link também oferece o número total de mensagens no fórum.

![](assets/mrm_forum_access_link.png)

## Usando um fórum {#using-a-forum}

Mensagens e suas respostas são mostradas em ordem cronológica (da mais nova para a mais antiga).

Para exibir o conteúdo de uma mensagem, clique em seu cabeçalho.

![](assets/mrm_forum_expand_msg.png)

**Iniciar uma nova discussão**

Para iniciar uma nova discussão, clique no botão **[!UICONTROL Add a discussion]** no canto superior direito. The **[!UICONTROL Discussion forum]** box comes up (see below).

![](assets/mrm_forum_new_thread.png)

**Postar uma mensagem em uma discussão existente**

Para postar uma mensagem em uma discussão existente, abra a mensagem que deseja responder e clique no link **[!UICONTROL Reply]** no canto superior esquerdo. The **[!UICONTROL Discussion forum]** box comes up (see below).

![](assets/mrm_forum_answer_msg.png)

Quando responder a uma mensagem, a pessoa que postou a mensagem original receberá uma notificação.

**Escrever uma mensagem**

Na **[!UICONTROL Discussion forum]** caixa:

1. Insira o texto no campo **[!UICONTROL Message]** e um título de discussão no campo **[!UICONTROL Subject]**.

   ![](assets/mrm_forum_edit_msg.png)

1. Se necessário:

   * Se desejar que alguém que não se inscreveu no fórum participe da discussão, use o campo **[!UICONTROL Operator to notify]**. O operador receberá um e-mail de notificação para esta mensagem específica (eles não serão inscritos no fórum). Para notificar vários operadores, selecione um grupo de operadores.
   * Para adicionar um anexo à mensagem, clique em **[!UICONTROL Browse]**. O anexo também será incluído no e-mail de notificação. Os anexos só podem ser enviados individualmente: para enviar vários arquivos, é necessário compactá-los.

1. Click **[!UICONTROL Create the message]** to post it to the forum.

>[!NOTE]
>
>Uma vez que a mensagem tenha sido postada no fórum, ela não poderá mais ser alterada ou excluída.

## Postando no fórum pessoal de um operador {#posting-to-the-personal-forum-of-an-operator}

Você poderá postar uma mensagem no fórum de um operador se, por exemplo, sua mensagem não disser respeito a uma campanha específica, mas ainda desejar acompanhar a conversa sobre o Adobe Campaign. Os fóruns pessoais são públicos e todos os operadores verão sua mensagem. O operador receberá uma mensagem sempre que alguém postar no seu fórum pessoal.

Para acessar o fórum de um operador:

* Se você tiver os direitos necessários para acessar o nó do explorador **[!UICONTROL Administration > Access management > Operators]**, abra o painel do operador desejado e clique no link **[!UICONTROL Forum]** no canto superior direito.
* Caso contrário, localize o nome do operador no Adobe Campaign (por meio de uma mensagem publicada no fórum por este operador, uma tarefa atribuída a ele) e clique nela para acessar seu painel. Você também poderá pedir ao administrador para criar uma visualização da pasta do operador.

## Inscrever-se em um fórum {#subscribing-to-a-forum}

A inscrição de um fórum permite seguir as discussões. Inscritos receberão uma notificação por e-mail sempre que uma mensagem for postada no fórum. Este e-mail conterá o corpo da mensagem e quaisquer anexos. Para responder a uma mensagem, clique no corpo do e-mail e, em seguida, faça login na interface da Web do Adobe Campaign. Quando se inscrever em um fórum, essas informações ficam visíveis para todos.

* Para se inscrever em um fórum, clique no botão **[!UICONTROL Follow discussions]** na seção superior direita acima da lista de mensagens.

   ![](assets/mrm_forum_subscribe.png)

   A seção fica azul e mostra que está inscrito no fórum.

* Para cancelar a inscrição de um fórum, clique no botão **[!UICONTROL Unsubscribe]**.

   ![](assets/mrm_forum_unsubscribe.png)

* O painel pessoal lista os fóruns inscritos. Clique no link **[!UICONTROL Subscription to discussion forums]** para exibir a lista e, em seguida, clique no item que lhe interessa para acessar seu fórum.

   ![](assets/platform_dashboard_operator_subscr_forums.png)

   Para obter mais informações sobre painéis pessoais, consulte [esta seção](../../platform/using/access-management.md#operators).

* To see who is subscribed to a forum, click the **[!UICONTROL List of subscribers to this discussion forum]** link above the list of messages.

   ![](assets/mrm_forum_subscribers.png)

## Verificando o delivery de notificação {#checking-notification-delivery}

Se os operadores inscritos em um fórum não receberem notificações conforme esperado:

* Verifique se os endereços de email estão inseridos nos perfis de operador.
* Go to the **[!UICONTROL Administration > Production > Technical workflows > Campaign processes]** node and check that the **[!UICONTROL Jobs in discussion forums]** workflow is started and free of errors.
* Exibir os logs do delivery:

   * On the Adobe Campaign home page, go to **[!UICONTROL Campaigns > Navigation > Deliveries]**, then open the **[!UICONTROL Discussion forum notification]** delivery.
   * No explorador, vá para **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]**, em seguida, clique em **[!UICONTROL Discussion forum notifications]**.

   In the **[!UICONTROL Discussion forum notifications]** box, the delivery logs are found in the **[!UICONTROL Edit > Delivery]** tab. You can also view the **[!UICONTROL Tracking > Log]** and the **[!UICONTROL Exclusion causes]** tabs.

