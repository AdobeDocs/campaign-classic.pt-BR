---
title: Criação do conteúdo da mensagem
seo-title: Criação do conteúdo da mensagem
description: Criação do conteúdo da mensagem
seo-description: null
page-status-flag: never-activated
uuid: 4ee013fc-fba2-4120-b796-dd4008000ea9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 1f420652-c9af-4a49-8d5c-a640e960aced
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 2c0d4054fbc15a88ea0370269b62c7d647aea033

---


# Criação do conteúdo da mensagem{#creating-message-content}

A definição do conteúdo da mensagem transacional é a mesma para deliveries comuns no Adobe Campaign. Por exemplo, para um delivery de email, você pode criar conteúdo em formato HTML ou texto, adicionar anexos ou personalizar o objeto do delivery. Para obter mais informações, consulte o capítulo sobre [Delivery de email](../../delivery/using/about-email-channel.md).

>[!CAUTION]
>
>As imagens incluídas na mensagem devem ser acessíveis publicamente. O Adobe Campaign não fornece nenhum mecanismo de carregamento de imagem para mensagens transacionais.\
>Ao contrário do JSSP ou webApp, `<%=`não tem nenhum escape padrão.
>
>Nesse caso, você precisa escapar cada dado que vem do evento corretamente. Este escape depende da forma como esse campo é usado. Por exemplo, dentro de uma URL, use encodeURIComponent. Para ser exibido no HTML, você pode usar escapeXMLString.

Após definir o conteúdo da mensagem, você pode integrar as informações do evento no corpo da mensagem e personalizá-lo. As informações do evento são inseridas no corpo do texto graças às tags de personalização.

![](assets/messagecenter_create_content_001.png)

* Todos os campos de personalização vêm da carga.
* É possível referenciar um ou vários blocos de personalização em uma mensagem transacional. O conteúdo do bloco será adicionado ao conteúdo de delivery durante a publicação para a instância de execução.

Para inserir tags de personalização no corpo de uma mensagem de email, siga as etapas abaixo:

1. No template de mensagem, clique na guia que corresponde ao formato do email (HTML ou texto).
1. Insira o corpo da mensagem.
1. No corpo do texto, insira a tag usando os menus **[!UICONTROL Real time events>Event XML]**.

   ![](assets/messagecenter_create_custo_002.png)

1. Preencha a tag usando a seguinte sintaxe: **element name**.@**attribute name** como mostrado abaixo.

   ![](assets/messagecenter_create_custo_003.png)

