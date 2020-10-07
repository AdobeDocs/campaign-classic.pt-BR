---
title: Marketing viral e social
seo-title: Marketing viral e social
description: Marketing viral e social
seo-description: null
page-status-flag: never-activated
uuid: dca3db7e-cc8d-42ca-b1b8-45e9fb739c97
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
discoiquuid: 66f2b229-92d9-4db1-97a4-2d9eb2270446
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 85%

---


# Marketing viral e social{#viral-and-social-marketing}

## Sobre marketing viral {#about-viral-marketing}

O Adobe Campaign permite que você configure ferramentas para incentivar o marketing viral.

Isso permite que os recipients de delivery ou os visitantes do site compartilhem informações com a rede: desde adicionar um link ao seu perfil do Facebook ou do Twitter até enviar uma mensagem para um amigo.

![](assets/s_ncs_user_viral_icons.png)

>[!CAUTION]
>
>Para que os links adicionados funcionem corretamente, a página de espelho correspondente deve estar disponível. Para fazer isso, inclua o link para a página espelho no delivery.

## Redes sociais: compartilhando um link {#social-networks--sharing-a-link}

Para permitir que os recipients de entrega compartilhem o conteúdo das mensagens com membros de sua rede, você precisa incluir o bloco de personalização correspondente.

![](assets/s_ncs_user_viral_add_link.png)

>[!NOTE]
>
>Por padrão, esse link não é oferecido na lista de blocos. You can access it by clicking **[!UICONTROL Other...]**, and selecting the **[!UICONTROL Social network sharing links]** block.

![](assets/s_ncs_user_viral_add_link_via_others.png)

A renderização será da seguinte forma:

![](assets/s_ncs_user_viral_add_link_rendering.png)

Quando o recipient clicar no ícone de uma das redes sociais exibidas, ele será automaticamente redirecionado para sua conta e poderá compartilhar o conteúdo da mensagem por meio de um link. Isso permitirá aos membros de sua rede acessarem a comunicação.

>[!NOTE]
>
>Este bloco de personalização contém todos os links (para envio e compartilhamento de mensagens com todas as redes sociais). Ele poderá ser alterado para atender às suas necessidades. No entanto, a configuração é reservada para usuários avançados. To edit the matching personalization block, go to the **[!UICONTROL Resources > Campaign management > Personalization blocks]** node of the Adobe Campaign tree.

## Marketing viral: encaminhar para um amigo {#viral-marketing--forward-to-a-friend}

Um serviço viral permite que ações do tipo por-indicação sejam executadas: essas ações permitem que você encaminhe uma mensagem para um amigo. O perfil do(s) indicado(s) é armazenado temporariamente no banco de dados (em uma tabela dedicada). As mensagens encaminhadas incluem um link para o indicado assinar: caso assine, ele será adicionado ao banco de dados do Adobe Campaign.

O encaminhamento de mensagens é baseado nos mesmos princípios que os links de rede social.

Aplique as seguintes etapas:

1. Add the **[!UICONTROL Social network sharing links]** personalization block into the body of the original message.
1. O recipient da mensagem pode clicar no ícone de **[!UICONTROL Email]** para enviar esta mensagem para um ou mais amigos.

   ![](assets/s_ncs_user_viral_email_link.png)

   Um formulário de referência permite inserir os endereços de email dos indicados.

   ![](assets/s_ncs_user_viral_email_msg.png)

   A mensagem é enviada a eles quando o recipient principal clicar no botão **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >O conteúdo dessa mensagem pode ser personalizado para atender às suas necessidades. It is created based on the **[!UICONTROL Transfer of original message]** template, which is stored in the **[!UICONTROL Administration > Campaign management > Technical delivery templates]** node.
   >
   >Também é possível alterar o formulário de encaminhamento de mensagens disponibilizado para o referenciador. Para fazer isso, é necessário alterar o aplicativo web **Viral form** armazenado no nó **[!UICONTROL Resources > Online > Web applications]**.

1. Na mensagem encaminhada, um link permite que o indicado salve o perfil no banco de dados. Um formulário de entrada é fornecido para essa finalidade.

   ![](assets/s_ncs_user_viral_create_account_form.png)

   >[!NOTE]
   >
   >Essa configuração pode ser adaptada. To do this, you need to modify the **Recipient subscription** Web application stored in the **[!UICONTROL Resources > Online > Web applications]** node.
   >
   >Para obter mais informações sobre aplicativos web, consulte [esta seção](../../web/using/about-web-applications.md).

   Depois de validar, uma mensagem de confirmação será enviada para ele: só será registrado para sempre uma vez que ativar o link na mensagem de confirmação. This message is created based on the **[!UICONTROL Registration confirmation]** template, which is stored in the **[!UICONTROL Administration > Campaign management > Technical delivery templates]** node.

   O indicado é adicionado à pasta **Recipients** do banco de dados e é inscrito (por padrão) ao serviço de informação do **Boletim informativo**.

## Rastreamento de compartilhamento em rede social {#tracking-social-network-sharing}

O compartilhamento e o acesso a informações compartilhadas são rastreados. Essas informações coletadas pelo Adobe Campaign podem ser acessadas em dois lugares:

* na guia **[!UICONTROL Tracking]** do delivery (ou individualmente para cada recipient):

   ![](assets/s_ncs_user_network_del_tracking_tab.png)

* in a dedicated **[!UICONTROL Sharing to social networks]** report:

   ![](assets/s_ncs_user_viral_report.png)

