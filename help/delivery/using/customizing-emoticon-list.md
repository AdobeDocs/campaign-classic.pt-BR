---
title: Personalização da lista de emoticon
description: Saiba como personalizar a lista de emoticon ao usar o Adobe Campaign Classic.
page-status-flag: never-activated
uuid: ddcc2e3b-e251-4a7a-a22a-28701522839f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 2ea2747f-957f-41a9-a03f-20c03fa99116
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3beb62d0264cfcb03486c291ce79cc7ff582e9c7
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 2%

---


# Personalização da lista de emoticon {#customize-emoticons}

A lista de emoticon exibida no pop-up é regida por uma lista discriminada que permite exibir valores em uma lista para restringir as opções que o usuário tem para um determinado campo.
A ordem de lista do emoticon pode ser personalizada; você também pode adicionar outros emoticons à sua lista.
Os emoticons estão disponíveis para email e push para mais informações, consulte esta [página](../../delivery/using/defining-the-email-content.md#inserting-emoticons).

## Adicionar um novo emoticon {#add-new-emoticon}

>[!CAUTION]
>
>A lista de emoticon não pode exibir mais de 81 entradas.

1. Escolha seu novo emoticon para adicionar desta [página](https://unicode.org/emoji/charts/full-emoji-list.html). Observe que ele deve ser compatível com as diferentes plataformas, como navegador e SO.

1. Na caixa **[!UICONTROL Explorer]**, selecione **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** e clique na lista discriminada **[!UICONTROL Emoticon list]** predefinida.

   >[!NOTE]
   >
   >listas discriminadas predefinidas só podem ser gerenciadas por um administrador do console do Adobe Campaign Classic.

   ![](assets/emoticon_1.png)

1. Clique em **[!UICONTROL Add]**.

1. Preencha os campos:

   * **[!UICONTROL U+]**: Código do seu novo emoticon. Você pode encontrar a lista dos códigos de emoticons nesta [página](https://unicode.org/emoji/charts/full-emoji-list.html).
Para evitar problemas de compatibilidade, recomendamos que você escolha emoticons compatíveis em navegadores e em todos os sistemas operacionais.

   * **[!UICONTROL Label]**: Etiqueta do seu novo emoticon.
   ![](assets/emoticon_5.png)

1. Clique em **[!UICONTROL Ok]** e **[!UICONTROL Save]** quando a configuração for concluída.
Seu novo emoticon será colocado automaticamente na loja.

1. Para exibi-la na janela **[!UICONTROL Insert emoticon]** dos seus delivery, selecione seu emoticon recém-criado clicando nele com o duplo.

1. Escolha na lista **[!UICONTROL Display order]** suspensa em que ordem seu novo emoticon será exibido. Observe que ao selecionar uma ordem de exibição já atribuída, o emoticon existente será movido automaticamente para a loja.

   <br>Neste exemplo, escolhemos o número de ordem de exibição 61, o que significa que se uma entrada já tivesse esse pedido, ela será movida automaticamente para a loja e nossa nova entrada ocupará seu lugar na lista da lista discriminada.

   ![](assets/emoticon_2.png)

1. Seu novo emoticon foi adicionado à lista discriminada **[!UICONTROL Insert emoticon list]** predefinida. Você pode alterar a sua configuração a qualquer **[!UICONTROL Display order]** momento ou movê-la para a loja se não precisar mais dela.

1. Para que suas alterações sejam levadas em conta, desconecte-se e reconecte-se do Adobe Campaign Classic. Se seu novo emoticon ainda não aparecer na janela pop-up, talvez seja necessário limpar o cache. **[!UICONTROL Insert emoticon]** Para obter mais informações, consulte esta [seção](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).

1. Seu novo emoticon agora pode ser encontrado em seus delivery na janela pop-up na **[!UICONTROL Insert emoticon]** posição 61, conforme configurado nas etapas anteriores. Para obter mais informações sobre como usar emoticons em seus delivery, consulte esta [página](../../delivery/using/defining-the-email-content.md#inserting-emoticons).

   ![](assets/emoticon_4.png)

1. Se os emoticons a seguir forem exibidos na janela **[!UICONTROL Insert emoticon]** pop-up, isso significa que eles não foram configurados corretamente. Verifique se o seu **[!UICONTROL U+]** código ou **[!UICONTROL Display order]** está correto no **[!UICONTROL Emoticon list]**.

   ![](assets/emoticon_6.png)
