---
title: Publicar o pacote de campanha
seo-title: Publicar o pacote de campanha
description: Publicar o pacote de campanha
seo-description: null
page-status-flag: never-activated
uuid: f2d35a8d-191f-4c53-8682-7ccce2a94257
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 8653d4fc-e47f-451a-95f2-c9209a252664
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 90%

---


# Publicar o pacote de campanha{#publishing-the-campaign-package}

Central entity operators publish campaigns they wish to offer to local entities in the **[!UICONTROL list of campaign packages]**.

Antes de serem publicados na lista de pacotes de campanha, os pacotes de campanha devem ser aprovados pela entidade central. Para fazer isso, é possível especificar um revisor ou grupo de revisores por meio do link **[!UICONTROL Approval parameters]** no pacote de campanha.

## Atribuir um revisor {#assigning-a-reviewer}

Para selecionar o revisor, clique no link **[!UICONTROL Approval parameters]** do pacote de campanha e escolha o revisor relevante na lista suspensa.

![](assets/s_advuser_mkg_dist_define_valid.png)

You may then begin the approval process by clicking **[!UICONTROL Submit for approval]**.

![](assets/s_advuser_mkg_dist_valid_process.png)

Uma mensagem de notificação é enviada ao revisor para confirmar a disponibilidade desse pacote de campanha. A mensagem contém um link para aceitar ou rejeitar a aprovação via acesso à Web.

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>No nível da entidade organizacional, você também pode especificar os revisores para aprovar pedidos. Para obter mais informações, consulte [Entidades organizacionais](../../campaign/using/about-distributed-marketing.md#organizational-entities).

## Adicionar outros revisores {#adding-other-reviewers}

You can add other reviewers from the **[!UICONTROL Edit...]** link, found in the campaign package&#39;s **[!UICONTROL Approval parameters...]** tab.

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## Períodos de aprovação {#approval-periods}

Por padrão, os revisores recebem três dias a partir da data de envio para processar a aprovação.

Na janela dos revisores de edição, é possível definir lembretes para enviar uma ou várias mensagens se um pacote de campanha não tiver sido aprovado. To do this, click the **[!UICONTROL Add reminder]** link, then the **[!UICONTROL Add]** button.

Os lembretes podem ser enviados em uma determinada data e/ou **x** dias após a data de envio. O tipo de lembrete pode ser configurado na primeira coluna da tabela de lembretes. No exemplo abaixo, os revisores receberão uma mensagem de lembrete em 29/01/2014, ou seja, dois dias antes da data selecionada na coluna **[!UICONTROL Date]**, e um segundo lembrete um dia antes do final do período de aprovação, ou seja, dois dias após a data de envio para aprovação.

![](assets/s_advuser_mkg_dist_reminder_planning.png)

Depois que estiver definido e o pacote for enviado para aprovação, o cronograma de execução é exibido na guia **[!UICONTROL Audit]**. Ele mostra o prazo de processamento calculado com base na configuração anterior, bem como nas datas de todos os lembretes configurados.

## Aprovar via console do Adobe Campaign {#approving-via-the-adobe-campaign-console}

Se nenhum revisor tiver sido especificado ou se nenhum dos operadores notificados tiver aprovado o pacote, o botão **[!UICONTROL Approve the package]** permitirá prosseguir diretamente para a aprovação no **[!UICONTROL Dashboard]** do pacote da campanha ou da visão geral dos pacotes.

![](assets/s_advuser_mkg_dist_valid_button.png)

Após a aprovação, a campanha é publicada, adicionada à lista e, assim que sua data de disponibilidade é alcançada, as entidades locais podem usá-la. Se as entidades locais foram especificadas ao criar a campanha, uma mensagem é enviada aos operadores no grupo de notificação para saberem que a campanha está disponível. Se nenhuma entidade foi especificada anteriormente, a campanha estará disponível para todas as entidades locais, por padrão. Para obter mais informações, consulte [Entidades organizacionais](../../campaign/using/about-distributed-marketing.md#organizational-entities).
