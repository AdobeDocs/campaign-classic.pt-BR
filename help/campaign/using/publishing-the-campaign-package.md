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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# Publicar o pacote de campanha{#publishing-the-campaign-package}

Central entity operators publish campaigns they wish to offer to local entities in the **[!UICONTROL list of campaign packages]**.

Antes de serem publicados na lista de pacotes de campanha, os pacotes de campanha devem ser aprovados pela entidade central. To do this, you can specify a reviewer or group of reviewers via the **[!UICONTROL Approval parameters]** link in the campaign package.

## Atribuir um revisor {#assigning-a-reviewer}

To select the reviewer, click the **[!UICONTROL Approval parameters]** link from the campaign package and choose the relevant reviewer from the drop-down list.

![](assets/s_advuser_mkg_dist_define_valid.png)

You may then begin the approval process by clicking **[!UICONTROL Submit for approval]**.

![](assets/s_advuser_mkg_dist_valid_process.png)

Uma mensagem de notificação é enviada ao revisor para confirmar a disponibilidade desse pacote de campanha. A mensagem contém um link para aceitar ou rejeitar a aprovação via acesso à Web.

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>No nível da entidade organizacional, você também pode especificar os revisores para aprovar pedidos. For more on this, refer to [Organizational entities](../../campaign/using/about-distributed-marketing.md#organizational-entities).

## Adicionar outros revisores {#adding-other-reviewers}

You can add other reviewers from the **[!UICONTROL Edit...]** link, found in the campaign package&#39;s **[!UICONTROL Approval parameters...]** tab.

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## Períodos de aprovação {#approval-periods}

Por padrão, os revisores recebem três dias a partir da data de envio para processar a aprovação.

Na janela dos revisores de edição, é possível definir lembretes para enviar uma ou várias mensagens se um pacote de campanha não tiver sido aprovado. Para fazer isso, clique no **[!UICONTROL Add reminder]** link e no **[!UICONTROL Add]** botão.

Os lembretes podem ser enviados em uma determinada data e/ou **x** dias após a data de envio. O tipo de lembrete pode ser configurado na primeira coluna da tabela de lembretes. In the example below, the reviewers will receive a reminder message on the on the 29/01/2014, i.e. two days before the date selected in the **[!UICONTROL Date]** column, and a second reminder one day before the end of the approval period, i.e. two days after the submission for approval date.

![](assets/s_advuser_mkg_dist_reminder_planning.png)

Once it is defined and the package has been submitted for approval, the execution schedule is displayed in the **[!UICONTROL Audit]** tab. Ele mostra o prazo de processamento calculado com base na configuração anterior, bem como nas datas de todos os lembretes configurados.

## Aprovar via console do Adobe Campaign {#approving-via-the-adobe-campaign-console}

If no reviewer has been specified or if none of the notified operators have approved the package, the **[!UICONTROL Approve the package]** button lets you proceed directly to the approval from the campaign package **[!UICONTROL Dashboard]** or from the packages overview.

![](assets/s_advuser_mkg_dist_valid_button.png)

Após a aprovação, a campanha é publicada, adicionada à lista e, assim que sua data de disponibilidade é alcançada, as entidades locais podem usá-la. Se as entidades locais foram especificadas ao criar a campanha, uma mensagem é enviada aos operadores no grupo de notificação para saberem que a campanha está disponível. Se nenhuma entidade foi especificada anteriormente, a campanha estará disponível para todas as entidades locais, por padrão. For more on this, refer to [Organizational entities](../../campaign/using/about-distributed-marketing.md#organizational-entities).
