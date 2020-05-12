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
source-git-commit: 3522f4f50770dde220610cd5f1c4084292d8f1f5
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 91%

---


# Como configurar links rastreados{#how-to-configure-tracked-links}

Para cada entrega, você pode rastrear a recepção das mensagens e a ativação dos links inseridos no conteúdo da mensagem. Isso permite rastrear o comportamento dos destinatários seguindo as ações de entrega que foram direcionadas.

>[!NOTE]
>
>O rastreamento se aplica a mensagens, mas o rastreamento na web permite monitorar como os recipients navegam em um site (páginas visitadas, compras).
>
>A configuração de rastreamento na web é apresentada [nesta seção](../../configuration/using/about-web-tracking.md).

O rastreamento de mensagens é habilitado por padrão. Para personalizar como URLs são rastreados, siga as etapas abaixo:

1. Selecione a opção **[!UICONTROL Display URLs]** na seção inferior do assistente do delivery, no conteúdo da mensagem.

   ![](assets/s_ncs_user_email_del_display_urls.png)

   Ao selecionar um dos URLs rastreados na lista, ele é realçado no conteúdo do delivery, exceto pelo link na página espelhada e no link de cancelamento de subscrição fornecido como padrão.

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. Para cada URL da mensagem, selecione se deseja ativar ou não o rastreamento.

   >[!IMPORTANT]
   >
   >Quando o URL do link é usado como um rótulo, é recomendado desativar o rastreamento para evitar riscos de rejeição devido ao phishing.
   >
   >Por exemplo, se o URL www.adobe.com é inserido na mensagem e o rastreamento está ativado, o conteúdo do link de hipertexto será modificado para https://nlt.adobe.net/r/?id=xxxxxx. Isso significa que ele pode ser considerado como fraudulento por clientes de mensagens destinatárias.

1. Se necessário, altere o rótulo de rastreamento. Clique duas vezes no rótulo e insira um novo.

   >[!NOTE]
   >
   >Os rótulos dos URLs rastreados e os rótulos podem ser modificados para simplificar a leitura de informações ao rastrear os envios. Dois URLs ou rótulos com o mesmo nome são adicionados ao calcular a contagem de cliques.

1. Se necessário, altere o modo de rastreamento. Selecione um novo modo na coluna **[!UICONTROL Tracking]** que corresponde ao link direcionado, conforme abaixo:

   ![](assets/s_ncs_user_select_tracking_mode.png)

   Para cada URL individual, é possível definir o modo de rastreamento para um destes valores:

   * **[!UICONTROL Enabled]**: ativa o rastreamento nesse URL.
   * **[!UICONTROL Not tracked]** : desativa o rastreamento neste URL.
   * **[!UICONTROL Always enabled]** : sempre ativa o rastreamento desse URL. Essas informações são salvas para que na próxima vez, se o URL aparecer novamente em um conteúdo de mensagem futura, o rastreamento será ativado automaticamente.
   * **[!UICONTROL Never tracked]** : nunca ativa o rastreamento deste URL. Essas informações são salvas para que na próxima vez, se o URL aparecer novamente em um conteúdo de mensagem futura, o rastreamento será ativado automaticamente.
   * **[!UICONTROL Opt-out]**: considera esse URL como recusa ou cancelamento de subscrição.
   * **[!UICONTROL Mirror page]** : considera que este URL é um URL de mirror page.

1. Além disso, é possível selecionar uma categoria para cada URL rastreado na lista suspensa da coluna **[!UICONTROL Category]**. These categories can be displayed reports, as for example in **[!UICONTROL URLs and click streams]** (see [this section](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams)). As categorias são definidas em uma lista discriminada específica: **[!UICONTROL urlCategory]** (consulte [Gerenciamento de listas discriminadas](../../platform/using/managing-enumerations.md)).
