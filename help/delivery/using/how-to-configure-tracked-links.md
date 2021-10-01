---
product: campaign
title: Como configurar links rastreados
description: Como configurar links rastreados
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: ed88e1d6-c0d5-4a85-9f3e-be670f4bcc10
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: ht
source-wordcount: '582'
ht-degree: 100%

---

# Como configurar links rastreados{#how-to-configure-tracked-links}

![](../../assets/common.svg)

Para cada entrega, você pode rastrear a recepção das mensagens e a ativação dos links inseridos no conteúdo da mensagem. Isso permite rastrear o comportamento dos destinatários seguindo as ações de entrega que foram direcionadas.

O rastreamento se aplica a mensagens, mas o rastreamento web permite monitorar como os recipients navegam em um site (páginas visitadas, compras). A configuração de rastreamento web é apresentada [nesta seção](../../configuration/using/about-web-tracking.md).

>[!NOTE]
>
>Os links no conteúdo de email que contêm personalização precisam de sintaxe específica para serem rastreados. Para obter mais informações sobre como adicionar links a emails que podem ser personalizados e que oferecem suporte ao rastreamento, consulte [esta seção](tracking-personalized-links.md).

É altamente recomendável colocar URLs em delimitadores na guia **[!UICONTROL Text content]** antes de aplicar a fórmula de rastreamento. Os delimitadores de URL inseridos nessa guia são usados pelo Adobe Campaign para identificar URLs em cadeias de caracteres. Você pode usar estes pares de delimitadores:
* Parênteses ( )
* Colchetes [ ]
* Chaves { }

Neste exemplo, o URL https://www.adobe.com é seguido por um ponto e vírgula. O ponto e vírgula pode ser interpretado pelos clientes de email do recipient como parte do URL. Isso pode quebrar o link. Para evitar esse problema, é possível colocar o URL em delimitadores de uma destas maneiras:
* (https://www.adobe.com);
* [https://www.adobe.com];
* {https://www.adobe.com};

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
   * **[!UICONTROL Not tracked]**: desativa o rastreamento nesse URL.
   * **[!UICONTROL Always enabled]**: sempre ativa o rastreamento desse URL. Essas informações são salvas para que na próxima vez, se o URL aparecer novamente em um conteúdo de mensagem futura, o rastreamento será ativado automaticamente.
   * **[!UICONTROL Never tracked]**: nunca ativa o rastreamento desse URL. Essas informações são salvas para que na próxima vez, se o URL aparecer novamente em um uma mensagem futura, o rastreamento será desativado automaticamente.
   * **[!UICONTROL Opt-out]**: considera esse URL como recusa ou cancelamento de subscrição.
   * **[!UICONTROL Mirror page]**: considera esse URL como sendo de mirror page.

1. Além disso, é possível selecionar uma categoria para cada URL rastreado na lista suspensa da coluna **[!UICONTROL Category]**. Essas categorias podem ser relatórios, como em **[!UICONTROL URLs and click streams]** (consulte [esta seção](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams)). As categorias são definidas em uma lista discriminada específica: **[!UICONTROL urlCategory]** (consulte [Gerenciamento de listas discriminadas](../../platform/using/managing-enumerations.md)).
