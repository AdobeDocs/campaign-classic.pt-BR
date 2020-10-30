---
title: Personalização da lista de emoticons
description: Saiba como personalizar a lista de emoticons ao usar o Adobe Campaign Classic.
page-status-flag: never-activated
uuid: ddcc2e3b-e251-4a7a-a22a-28701522839f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 2ea2747f-957f-41a9-a03f-20c03fa99116
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '443'
ht-degree: 100%

---


# Personalização da lista de emoticons {#customize-emoticons}

A lista de emoticons exibida na janela pop-up é regida por uma lista discriminada que permite exibir valores em uma lista para restringir as opções que o usuário tem para um determinado campo.
A ordem da lista de emoticons pode ser personalizada; você também pode adicionar outros emoticons à lista.
Os emoticons estão disponíveis para email e push. Para obter mais informações, consulte esta [página](../../delivery/using/defining-the-email-content.md#inserting-emoticons).

## Adicionar um novo emoticon {#add-new-emoticon}

>[!CAUTION]
>
>A lista de emoticons não pode exibir mais de 81 entradas.

1. Escolha o novo emoticon para adicionar desta [página](https://unicode.org/emoji/charts/full-emoji-list.html). Observe que ele deve ser compatível com as diferentes plataformas, como navegador e SO.

1. Na caixa **[!UICONTROL Explorer]**, selecione **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** e clique na lista discriminada **[!UICONTROL Emoticon list]** predefinida.

   >[!NOTE]
   >
   >Listas discriminadas predefinidas só podem ser gerenciadas por um administrador do console do Adobe Campaign Classic.

   ![](assets/emoticon_1.png)

1. Clique em **[!UICONTROL Add]**.

1. Preencha os campos:

   * **[!UICONTROL U+]**: Código do novo emoticon. Você pode encontrar a lista dos códigos de emoticons nesta [página](https://unicode.org/emoji/charts/full-emoji-list.html).
Para evitar problemas de compatibilidade, recomendamos que você escolha emoticons compatíveis em navegadores e em todos os sistemas operacionais.

   * **[!UICONTROL Label]**: Rótulo do novo emoticon.

   ![](assets/emoticon_5.png)

1. Clique em **[!UICONTROL Ok]** e **[!UICONTROL Save]** quando a configuração for concluída.
O novo emoticon será colocado automaticamente na loja.

1. Para exibi-lo na janela **[!UICONTROL Insert emoticon]** dos deliveries, selecione o emoticon recém-criado clicando duas vezes sobre ele.

1. Escolha na lista suspensa **[!UICONTROL Display order]** em que ordem o novo emoticon será exibido. Observe que ao selecionar uma ordem de exibição já atribuída, o emoticon existente será movido automaticamente para a loja.

   <br>Neste exemplo, escolhemos o número de ordem de exibição 61, o que significa que se uma entrada já tiver esse pedido, ela será movida automaticamente para a loja e nossa nova entrada ocupará seu lugar na lista discriminada.

   ![](assets/emoticon_2.png)

1. O novo emoticon foi adicionado à lista discriminada **[!UICONTROL Insert emoticon list]** predefinida. Você pode alterar a **[!UICONTROL Display order]** a qualquer momento ou movê-la para a loja se não precisar mais dela.

1. Para que as alterações sejam levadas em conta, desconecte e reconecte novamente o Adobe Campaign Classic. Se o novo emoticon ainda não aparecer na janela pop-up **[!UICONTROL Insert emoticon]**, talvez seja necessário limpar o cache. Para obter mais informações, consulte esta [seção](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).

1. O novo emoticon agora pode ser encontrado nos deliveries na janela pop-up **[!UICONTROL Insert emoticon]** na posição 61, conforme configurado nas etapas anteriores. Para obter mais informações sobre como usar emoticons nos deliveries, consulte esta [página](../../delivery/using/defining-the-email-content.md#inserting-emoticons).

   ![](assets/emoticon_4.png)

1. Se os emoticons a seguir forem exibidos na janela pop-up **[!UICONTROL Insert emoticon]**, significa que eles não foram configurados corretamente. Verifique se o código **[!UICONTROL U+]** ou **[!UICONTROL Display order]** está correto no **[!UICONTROL Emoticon list]**.

   ![](assets/emoticon_6.png)
