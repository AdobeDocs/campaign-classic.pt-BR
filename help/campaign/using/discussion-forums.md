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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# Fóruns de discussão{#discussion-forums}

Os operadores do Adobe Campaign podem usar fóruns de discussão para compartilhar informações. Os elementos a seguir têm seu próprio fórum: planos, programas, campanhas, recursos, simulações, estoques. Cada operador também tem um fórum pessoal. Todas as discussões são públicas, mesmo em fóruns pessoais.

Os operadores podem se inscrever em um fórum para receber um email de notificação sempre que uma mensagem for postada.

## Acessando um fórum {#accessing-a-forum}

To visit the forum of a campaign, an operator, etc., go to its dashboard and click the **[!UICONTROL Forum]** link in the top right-hand corner. Esse link também oferece o número total de mensagens no fórum.

![](assets/mrm_forum_access_link.png)

## Usando um fórum {#using-a-forum}

Mensagens e suas respostas são mostradas em ordem cronológica (da mais nova para a mais antiga).

Para exibir o conteúdo de uma mensagem, clique em seu cabeçalho.

![](assets/mrm_forum_expand_msg.png)

**Iniciar uma nova discussão**

To start a new discussion, click the **[!UICONTROL Add a discussion]** button in the top right-hand corner. A **[!UICONTROL Discussion forum]** caixa aparece (veja abaixo).

![](assets/mrm_forum_new_thread.png)

**Postar uma mensagem em uma discussão existente**

To post a message to an existing discussion, open the message that you want to answer, then click the **[!UICONTROL Reply]** link in the top left-hand corner. A **[!UICONTROL Discussion forum]** caixa aparece (veja abaixo).

![](assets/mrm_forum_answer_msg.png)

Quando responder a uma mensagem, a pessoa que postou a mensagem original receberá uma notificação.

**Escrever uma mensagem**

Na **[!UICONTROL Discussion forum]** caixa:

1. Enter your text in the **[!UICONTROL Message]** field and a discussion title in the **[!UICONTROL Subject]** field.

   ![](assets/mrm_forum_edit_msg.png)

1. Se necessário:

   * If you want someone to take part in the discussion who isn&#39;t subscribed to the forum, use the **[!UICONTROL Operator to notify]** field. O operador receberá um e-mail de notificação para esta mensagem específica (eles não serão inscritos no fórum). Para notificar vários operadores, selecione um grupo de operadores.
   * To add an attachment to the message, click **[!UICONTROL Browse]**. O anexo também será incluído no e-mail de notificação. Os anexos só podem ser enviados individualmente: para enviar vários arquivos, é necessário compactá-los.

1. Clique **[!UICONTROL Create the message]** para postá-lo no fórum.

>[!NOTE]
>
>Uma vez que a mensagem tenha sido postada no fórum, ela não poderá mais ser alterada ou excluída.

## Postando no fórum pessoal de um operador {#posting-to-the-personal-forum-of-an-operator}

Você poderá postar uma mensagem no fórum de um operador se, por exemplo, sua mensagem não disser respeito a uma campanha específica, mas ainda desejar acompanhar a conversa sobre o Adobe Campaign. Os fóruns pessoais são públicos e todos os operadores verão sua mensagem. O operador receberá uma mensagem sempre que alguém postar no seu fórum pessoal.

Para acessar o fórum de um operador:

* If you have the necessary rights to access the **[!UICONTROL Administration > Access management > Operators]** node of the explorer, open the dashboard of the desired operator and click the **[!UICONTROL Forum]** link in the top right-hand corner.
* Caso contrário, localize o nome do operador no Adobe Campaign (por meio de uma mensagem publicada no fórum por este operador, uma tarefa atribuída a ele) e clique nela para acessar seu painel. Você também poderá pedir ao administrador para criar uma visualização da pasta do operador.

## Inscrever-se em um fórum {#subscribing-to-a-forum}

A inscrição de um fórum permite seguir as discussões. Inscritos receberão uma notificação por e-mail sempre que uma mensagem for postada no fórum. Este e-mail conterá o corpo da mensagem e quaisquer anexos. Para responder a uma mensagem, clique no corpo do e-mail e, em seguida, faça login na interface da Web do Adobe Campaign. Quando se inscrever em um fórum, essas informações ficam visíveis para todos.

* To subscribe to a forum, click the **[!UICONTROL Follow discussions]** button in the top right hand section above the list of messages.

   ![](assets/mrm_forum_subscribe.png)

   A seção fica azul e mostra que está inscrito no fórum.

* To unsubscribe from a forum, click the **[!UICONTROL Unsubscribe]** button.

   ![](assets/mrm_forum_unsubscribe.png)

* O painel pessoal lista os fóruns inscritos. Click the **[!UICONTROL Subscription to discussion forums]** link to display the list, then click the item that interests you to access its forum.

   ![](assets/platform_dashboard_operator_subscr_forums.png)

   Para obter mais informações sobre painéis pessoais, consulte [esta seção](../../platform/using/access-management.md#operators).

* To see who is subscribed to a forum, click the **[!UICONTROL List of subscribers to this discussion forum]** link above the list of messages.

   ![](assets/mrm_forum_subscribers.png)

## Verificando o delivery de notificação {#checking-notification-delivery}

Se os operadores inscritos em um fórum não receberem notificações conforme esperado:

* Verifique se os endereços de email estão inseridos nos perfis de operador.
* Vá para o **[!UICONTROL Administration > Production > Technical workflows > Campaign processes]** nó e verifique se o fluxo de **[!UICONTROL Jobs in discussion forums]** trabalho foi iniciado e sem erros.
* Exibir os logs do delivery:

   * Na página inicial do Adobe Campaign, acesse **[!UICONTROL Campaigns > Navigation > Deliveries]** e abra a **[!UICONTROL Discussion forum notification]** entrega.
   * No explorador, vá para **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]** e clique em **[!UICONTROL Discussion forum notifications]**.
   Na **[!UICONTROL Discussion forum notifications]** caixa, os registros de entrega são encontrados na **[!UICONTROL Edit > Delivery]** guia. Você também pode exibir as guias **[!UICONTROL Tracking > Log]** e **[!UICONTROL Exclusion causes]** .

