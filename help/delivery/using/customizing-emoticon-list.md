---
product: campaign
title: Personalizar a lista de emoticons
description: Saiba como personalizar a lista de emoticons ao usar o Adobe Campaign
badge-v8: label="Também se aplica ao v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
feature: Email, Push
role: User, Developer
hide: true
hidefromtoc: true
exl-id: b8642df3-1960-4f2c-8273-c3988a3e85f0
source-git-commit: 17ac1e0d68d2945b01aecc7c45fc5be7e6bd38af
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 100%

---

# Personalizar a lista de emoticons {#customize-emoticons}

A lista de emoticons exibida na janela pop-up é regida por uma enumeração que permite exibir valores em uma lista para restringir as opções que o usuário tem para um determinado campo.
A ordem da lista de emoticons pode ser personalizada. Também é possível adicionar outros emoticons à lista.

Observe que os emoticons só estão disponíveis para email e push. Para mais informações, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=pt-BR#inserting-emoticons){target="_blank"}.


## Adicionar um novo emoticon {#add-new-emoticon}

>[!CAUTION]
>
>A lista de emoticons não pode exibir mais de 81 entradas.

1. Escolha o novo emoticon para adicionar desta [página](https://unicode.org/emoji/charts/full-emoji-list.html). Observe que ele deve ser compatível com as diferentes plataformas, como navegador e SO.

1. Na caixa **[!UICONTROL Explorer]**, selecione **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** e clique na enumeração **[!UICONTROL Emoticon list]** predefinida.

   >[!NOTE]
   >
   >Enumerações predefinidas só podem ser gerenciadas por um administrador do console do Adobe Campaign Classic.

   ![](assets/emoticon_1.png)

1. Clique em **[!UICONTROL Add]**.

1. Preencha os campos:

   * **[!UICONTROL U+]**: Código do novo emoticon. Você pode encontrar a lista dos códigos de emoticons nesta [página](https://unicode.org/emoji/charts/full-emoji-list.html).
Para evitar problemas de compatibilidade, recomendamos que você escolha emoticons compatíveis em navegadores e em todos os sistemas operacionais.

   * **[!UICONTROL Label]**: Rótulo do novo emoticon.

   ![](assets/emoticon_5.png)

1. Clique em **[!UICONTROL Ok]** e **[!UICONTROL Save]** quando a configuração for concluída.
O novo emoticon será colocado automaticamente na loja.

1. Para exibi-lo na janela **[!UICONTROL Insert emoticon]** das entregas, selecione o emoticon recém-criado clicando duas vezes sobre ele.

1. Escolha na lista suspensa **[!UICONTROL Display order]** em que ordem o novo emoticon será exibido. Observe que ao selecionar uma ordem de exibição já atribuída, o emoticon existente será movido automaticamente para a loja.

   <br>Neste exemplo, escolhemos o número de ordem de exibição 61, o que significa que se uma entrada já tiver esse pedido, ela será movida automaticamente para a loja e nossa nova entrada ocupará seu lugar na enumeração.

   ![](assets/emoticon_2.png)

1. O novo emoticon foi adicionado à enumeração predefinida **[!UICONTROL Insert emoticon list]**. Você pode alterar a **[!UICONTROL Display order]** a qualquer momento ou movê-la para a loja se não precisar mais dela.

1. Para que as alterações sejam levadas em conta, desconecte e reconecte novamente o Adobe Campaign Classic. Se o novo emoticon ainda não aparecer na janela pop-up **[!UICONTROL Insert emoticon]**, talvez seja necessário limpar o cache. Para obter mais informações, consulte esta [seção](../../platform/using/faq-campaign-classic-v7.md#how-do-i-clear-console-cache).

1. O novo emoticon agora pode ser encontrado nas entregas na janela pop-up **[!UICONTROL Insert emoticon]** na posição 61, conforme configurado nas etapas anteriores. Para obter mais informações sobre como usar emoticons nas entregas, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=pt-BR#inserting-emoticons){target="_blank"}.

   ![](assets/emoticon_4.png)

1. Se os emoticons a seguir forem exibidos na janela pop-up **[!UICONTROL Insert emoticon]**, significa que eles não foram configurados corretamente. Verifique se o código **[!UICONTROL U+]** ou **[!UICONTROL Display order]** está correto no **[!UICONTROL Emoticon list]**.

   ![](assets/emoticon_6.png)
