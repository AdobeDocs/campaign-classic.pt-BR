---
title: Publicação no Facebook
seo-title: Publicação no Facebook
description: Publicação no Facebook
seo-description: null
page-status-flag: never-activated
uuid: f15170fa-0e7d-4913-81d6-0072c1ece482
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
discoiquuid: 335cf2de-1874-4e48-9538-f0937641cf96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2e18121e4094bc4cb215e5471091810df56b3ef5

---


# Publicação no Facebook{#publishing-on-facebook}

Quando a configuração estiver concluída, o Social Marketing permite que você poste publicações nas paredes de suas páginas do Facebook.

## Limitações {#limitations}

As limitações a seguir são inerentes ao Facebook.

* As mensagens não podem exceder 1.000 caracteres.
* HTML não é suportado.

## Criação de delivery {#creating-the-delivery}

Crie uma nova entrega usando o modelo de **[!UICONTROL Publish to a brand page]** entrega.

![](assets/social_facebook_delivery_001.png)

## Seleção do target principal {#selecting-the-main-target}

É necessário selecionar as páginas nas quais deseja publicar sua publicação.

1. Clique no **[!UICONTROL To]** link.

   ![](assets/social_facebook_delivery_010.png)

1. Clique no botão **[!UICONTROL Add]**.

   ![](assets/social_facebook_delivery_011.png)

1. Select **[!UICONTROL A Facebook page]**.

   ![](assets/social_facebook_delivery_012.png)

1. No **[!UICONTROL Folder]** campo, selecione a pasta de serviço que contém a página do Facebook. Por padrão, as páginas são armazenadas na raiz da pasta de **[!UICONTROL Facebook]** serviço. Em seguida, selecione a página do Facebook na qual deseja postar.

   ![](assets/social_facebook_delivery_013.png)

## Seleção do target da prova {#selecting-the-proof-target}

A **[!UICONTROL Target of the proofs]** guia permite que você defina a página do Facebook que deseja usar para testar as entregas antes de enviá-las para fora. Recomendamos a criação de uma página privada dedicada do Facebook para esse fim. Para obter mais informações sobre como criar uma página privada do Facebook, consulte [Criação de uma página](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page)de teste do Facebook. Para selecionar o destino de prova, aplique as mesmas etapas do destino principal: [Selecionando a meta](#selecting-the-main-target)principal.

![](assets/social_facebook_delivery_004.png)

>[!NOTE]
>
>Se você estiver usando a mesma página de teste do Facebook para todas as entregas, poderá salvar a meta de prova no modelo de **[!UICONTROL Publish to a brand page]** entrega, que é acessada pelo **[!UICONTROL Resources > Templates > Delivery templates]** nó. O destino da prova será inserido por padrão para cada nova entrega.

## Definição do público-alvo {#defining-the-audience}

Se você quiser usar segmentos locais para refinar o tipo de público autorizado a exibir a publicação, recomendamos que você crie uma página do Facebook por segmento (por exemplo: Adobe Campaign Paris, Adobe Campaign London, etc.).

No entanto, também é possível usar os filtros de público-alvo usados pelo Facebook. A **[!UICONTROL Audience]** guia do **[!UICONTROL Select target window]** oferece quatro filtros:

* **[!UICONTROL Country]**
* **[!UICONTROL Regions]**
* **[!UICONTROL Cities]**
* **[!UICONTROL Languages]**

>[!IMPORTANT]
>
>Use essa função com cuidado. Nos relatórios de entrega, o **[!UICONTROL Number of fans]** indicador não levará em conta esses filtros do Facebook.
>
>O Facebook pode alterar a lista de filtros de público-alvo, bem como seus valores.

## Definição do conteúdo da mensagem {#defining-message-content}

Selecione o tipo de publicação usando o menu **[!UICONTROL Content type]** suspenso.

![](assets/social_facebook_delivery_006.png)

Os seguintes tipos de entregas estão disponíveis:

* a **[!UICONTROL Status]**
* a **[!UICONTROL Status with a link]**
* a **[!UICONTROL Status with a YouTube link]**
* a **[!UICONTROL Photo album]**

### Publicar um status {#publishing-a-status}

Uma entrega de tipo de status pode conter apenas texto, como no exemplo abaixo:

![](assets/social_create_facebook_wall_post_004.png)

Insira o status da publicação na zona de entrada.

![](assets/social_facebook_delivery_015.png)

### Publicar um status com um link {#publishing-a-status-with-a-link}

Uma entrega do tipo de status com um link pode conter texto, imagens e um link. A seção a seguir detalha a simetria entre os campos da tela de edição de entrega e a publicação final no Facebook:

![](assets/social_facebook_delivery_007.png)

Insira os vários campos:

>[!IMPORTANT]
>
>Todos os URLs devem começar com **&quot;http://&quot;** ou **&quot;https://&quot;**.

1. No **[!UICONTROL Status]** campo, insira o texto que será exibido sob o nome da página.
1. No **[!UICONTROL Name]** campo, insira o título da publicação.
1. No **[!UICONTROL Link]** campo, insira o URL para o qual a publicação aponta.

   >[!NOTE]
   >
   >Se você quiser adicionar o **[!UICONTROL Link]** campo ao URL de um aplicativo do Facebook para promovê-lo, recomendamos que você o adapte aos critérios de exibição do smartphone:
   >
   >1. Selecione o aplicativo do Facebook [https://developers.facebook.com/apps](https://developers.facebook.com/apps)e selecione a **[!UICONTROL Settings > Basic]** guia.
   >1. Insira o **[!UICONTROL Namespace]** campo.
   >1. Digite o **[!UICONTROL Mobile Site URL]** campo: quando um usuário clica no link da publicação em seu smartphone, ele será automaticamente redirecionado pelo Facebook para o URL definido neste campo.
   >1. Crie seu aplicativo da Web para que a exibição do Facebook seja personalizada como função do dispositivo usado (smartphone ou PC).
   >1. Vá para o **[!UICONTROL Link]** campo da publicação por meio do console do Adobe Campaign e insira o URL do **[!UICONTROL Canvas page]** campo.


1. No **[!UICONTROL Image]** campo, insira o URL da imagem que será exibida à esquerda da publicação.

   >[!IMPORTANT]
   >
   >A imagem deve ser hospedada em um site público da internet para que o Facebook possa carregá-la.

1. No **[!UICONTROL Caption]** campo, insira o texto que será exibido no final da publicação.
1. Vá para o **[!UICONTROL Description]** campo e insira o texto a ser exibido sob o título.

![](assets/social_facebook_delivery_005.png)

### Publicar um status com um link do YouTube {#publishing-a-status-with-a-youtube-link}

Esse tipo de conteúdo permite que você publique um link em um vídeo do YouTube. Assim como um status com um link regular, você pode definir um status, um nome, uma legenda, uma descrição e um link adicional. A imagem é adicionada automaticamente pelo Facebook. As Symmetrix entre os campos da tela de edição de entrega e a publicação final no Facebook estão detalhadas abaixo:

![](assets/social_facebook_delivery_youtube_1.png)

Insira os vários campos:

>[!CAUTION]
>
>Todos os URLs devem começar com **&quot;http://&quot;** ou **&quot;https://&quot;**.

1. No **[!UICONTROL Status]** campo, insira o texto que será exibido sob o nome da página.
1. No **[!UICONTROL Name]** campo, insira o título da publicação.
1. No **[!UICONTROL Video code]** campo, digite o código do vídeo do YouTube. Por exemplo, para o link &#39;http://www.youtube.com/watch?v=abc123456&#39;, o código de vídeo será &#39;abc123456&#39;.
1. No **[!UICONTROL Caption]** campo, insira o texto que será exibido no final da publicação.
1. Vá para o **[!UICONTROL Description]** campo e insira o texto a ser exibido sob o título.

![](assets/social_facebook_delivery_youtube.png)

### Publicar um álbum de fotos {#publishing-a-photo-album}

Esse tipo de conteúdo permite que você publique um álbum de fotos. Você pode adicionar um nome e uma descrição para o álbum, bem como uma legenda para cada foto. As Symmetrix entre os campos da tela de edição de entrega e a publicação final no Facebook estão detalhadas abaixo:

![](assets/social_facebook_delivery_photos_1.png)

Insira os vários campos:

1. Comece inserindo o **[!UICONTROL Album name]**.
1. Em seguida, insira o arquivo a ser exibido acima **[!UICONTROL Description]** das fotos.
1. Para adicionar uma foto, clique no **[!UICONTROL Add]** botão, selecione a foto e clique em **[!UICONTROL Open]**.
1. Uma legenda pode ser adicionada a cada foto.

![](assets/social_facebook_delivery_photos.png)

## Visualização {#previewing}

A **[!UICONTROL Preview]** guia permite exibir a renderização da publicação.

1.  Clique na **[!UICONTROL Preview]** guia.
1. Clique no menu **[!UICONTROL Test personalization]** suspenso e selecione **[!UICONTROL Service]**.
1. No **[!UICONTROL Folder]** campo, selecione a pasta de serviço que contém suas páginas do Facebook. Por padrão, as páginas são armazenadas na raiz da pasta de **[!UICONTROL Facebook]** serviço.
1. Selecione a página do Facebook na qual você deseja testar a visualização.

![](assets/social_facebook_delivery_008.png)

>[!NOTE]
>
>A visualização pode diferir ligeiramente da publicação final do Facebook. Recomendamos enviar uma prova antes da entrega final para uma renderização exata da publicação. Consulte [Envio da prova](#sending-the-proof).

## Configuração do rastreamento {#configuring-tracking}

O rastreamento pode ser visualizado nos relatórios de entrega e na **[!UICONTROL Edit > Tracking]** guia da entrega e do serviço.

Os cliques no URL contido na entrega são medidos pelo Adobe Campaign. O número de cliques no **[!UICONTROL Like]** botão, o número de comentários e o número de fãs são medidos pelo Facebook.

A configuração de rastreamento é a mesma de uma entrega de email. Para obter mais informações, consulte [esta seção](../../delivery/using/monitoring-a-delivery.md).

>[!NOTE]
>
>No modelo de **[!UICONTROL Publish to a brand page]** entrega, o rastreamento é ativado por padrão.

## Envio da prova {#sending-the-proof}

Recomendamos enviar uma prova de sua publicação antes da entrega final para exibir a renderização exata da publicação em uma página de teste privada do Facebook. Para obter mais informações sobre como criar uma página de teste privada do Facebook, consulte [Criação de uma página](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page)de teste do Facebook. As etapas para selecionar a prova de destino são detalhadas em [Selecionar a meta](#selecting-the-proof-target)de prova.

A entrega da prova é idêntica às entregas por email. Consulte [esta seção](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Envio da mensagem {#sending-the-message}

1. Depois que o conteúdo for aprovado, clique no **[!UICONTROL Send]** botão.
1. Selecione **[!UICONTROL Deliver as soon as possible]** e clique no **[!UICONTROL Analyze]** botão.

   >[!NOTE]
   >
   >A **[!UICONTROL Postpone the delivery]** opção permite adiar a entrega para uma data posterior.

   ![](assets/social_facebook_delivery_009.png)

1. Quando a análise estiver concluída, verifique o resultado.
1. Clique em **[!UICONTROL Confirm delivery]** e em **[!UICONTROL Yes]**.

   ![](assets/social_facebook_delivery_016.png)

