---
title: Como configurar links rastreados
seo-title: Como configurar links rastreados
description: Como configurar links rastreados
seo-description: null
page-status-flag: never-activated
uuid: 0fb41a43-8a84-4a61-bf93-97e1d448a5ec
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: tracking-messages
discoiquuid: 9cae3861-88eb-447a-aa23-9d1de0710eec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Como configurar links rastreados{#how-to-configure-tracked-links}

Para cada entrega, você pode rastrear a recepção das mensagens e a ativação dos links inseridos no conteúdo da mensagem. Isso permite rastrear o comportamento dos destinatários seguindo as ações de entrega que foram direcionadas.

>[!NOTE]
>
>O rastreamento se aplica a mensagens, mas o rastreamento na web permite monitorar como os recipients navegam em um site (páginas visitadas, compras).
>
>A configuração de rastreamento na web é apresentada [nesta seção](../../configuration/using/about-web-tracking.md).

O rastreamento de mensagens é habilitado por padrão. Para personalizar como URLs são rastreados, siga as etapas abaixo:

1. Select the **[!UICONTROL Display URLs]** option in the lower section of the delivery wizard, under the message content.

   ![](assets/s_ncs_user_email_del_display_urls.png)

   Ao selecionar um dos URLs rastreados na lista, ele é realçado no conteúdo do delivery, exceto pelo link na página espelhada e no link de cancelamento de subscrição fornecido como padrão.

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. Para cada URL da mensagem, selecione se deseja ativar ou não o rastreamento.

   >[!CAUTION]
   >
   >Quando o URL do link é usado como um rótulo, é recomendado desativar o rastreamento para evitar riscos de rejeição devido ao phishing.
   >
   >Por exemplo, se o URL www.adobe.com é inserido na mensagem e o rastreamento está ativado, o conteúdo do link de hipertexto será modificado para https://nlt.adobe.net/r/?id=xxxxxx. Isso significa que ele pode ser considerado como fraudulento por clientes de mensagens destinatárias.

1. Se necessário, altere o rótulo de rastreamento. Clique duas vezes no rótulo e insira um novo.

   >[!NOTE]
   >
   >Os rótulos dos URLs rastreados e os rótulos podem ser modificados para simplificar a leitura de informações ao rastrear os envios. Dois URLs ou rótulos com o mesmo nome são adicionados ao calcular a contagem de cliques.

1. If needed, change the tracking mode, select a new mode in the **[!UICONTROL Tracking]** column which matches the targeted link, as shown below:

   ![](assets/s_ncs_user_select_tracking_mode.png)

   Para cada URL individual, é possível definir o modo de rastreamento para um destes valores:

   * **[!UICONTROL Enabled]** : ativa o rastreamento neste URL.
   * **[!UICONTROL Not tracked]** : desativa o rastreamento neste URL.
   * **[!UICONTROL Always enabled]** : sempre ativa o rastreamento desse URL. Essas informações são salvas para que na próxima vez, se o URL aparecer novamente em um conteúdo de mensagem futura, o rastreamento será ativado automaticamente.
   * **[!UICONTROL Never tracked]** : nunca ativa o rastreamento deste URL. Essas informações são salvas para que na próxima vez, se o URL aparecer novamente em um conteúdo de mensagem futura, o rastreamento será ativado automaticamente.
   * **[!UICONTROL Opt-out]** : considera este URL como um URL de não participação ou de cancelamento de assinatura.
   * **[!UICONTROL Mirror page]** : considera que este URL é um URL de página espelhada.

1. In addition, you can select a category for each tracked URL in the drop-down list of the **[!UICONTROL Category]** column. These categories can be displayed reports, as for example in **[!UICONTROL URLs and click streams]** (see [this section](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams)). As categorias são definidas em uma enumeração específica: **[!UICONTROL urlCategory]** (consulte [Gerenciamento de enumerações](../../platform/using/managing-enumerations.md)).
