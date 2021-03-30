---
solution: Campaign Classic
product: campaign
title: Criar SMS com o Campaign
description: Saiba como criar SMS com o Campaign
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
translation-type: tm+mt
source-git-commit: 5a084ebe5295d19de24cf92c721d4692f0f5deb8
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 84%

---


# Criar um delivery de SMS {#creating-a-sms-delivery}

## Selecione o canal de delivery {#selecting-the-delivery-channel}

Para criar um novo delivery de SMS, siga as etapas abaixo:

>[!NOTE]
>
>Os conceitos globais sobre a criação de delivery são apresentados [nesta seção](../../delivery/using/steps-about-delivery-creation-steps.md).

1. Crie um novo delivery, por exemplo, no painel do Delivery.
1. Selecione o template do delivery **Sent to mobiles (SMPP)** que você criou anteriormente. Para obter mais informações, consulte a seção [Change the delivery template](sms-set-up.md#changing-the-delivery-template) .

   ![](assets/s_user_mobile_wizard.png)

1. Identifique o delivery com um rótulo, código e descrição. Para obter mais informações, consulte [esta seção](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery).
1. Clique em **[!UICONTROL Continue]** para confirmar essas informações e exibir a janela de configuração de mensagem.

## Defina o conteúdo do SMS {#defining-the-sms-content}

Para criar o conteúdo do SMS, siga as etapas abaixo:

1. Insira o conteúdo da mensagem na seção **[!UICONTROL Text content]** do assistente. Os botões da barra de ferramentas permitem importar, salvar ou pesquisar conteúdo. O último botão é usado para inserir campos de personalização.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   O uso de campos de personalização é apresentado na seção [Sobre a personalização](../../delivery/using/about-personalization.md).

1. Clique em **[!UICONTROL Preview]** na parte inferior da página para exibir a renderização da mensagem com sua personalização. Para iniciar a visualização, selecione um recipient usando o botão **[!UICONTROL Test personalization]** na barra de ferramentas. Você pode selecionar um recipient nos targets definidos ou escolher outro recipient.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   Você pode aprovar a mensagem SMS. Você também pode exibir o conteúdo do SMS na tela do celular que aparece à direita do editor de conteúdo. Clique na tela e use o mouse para rolar pelo conteúdo.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. Clique no link **[!UICONTROL Data loaded]** para exibir as informações referentes ao recipient.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >As mensagens SMS são limitadas a um comprimento de 160 caracteres, se a página de código Latin-1 (ISO-8859-1) for usada. Se a mensagem for gravada em Unicode, não deverá exceder 70 caracteres. Alguns caracteres especiais podem afetar o comprimento da mensagem. Para obter mais informações sobre comprimento de mensagem, consulte a seção [Transliteração de caracteres de SMS](#about-character-transliteration) .
   >
   >Quando campos de personalização ou campos de conteúdo condicional estão presentes, o tamanho da mensagem varia de um recipient para outro. O comprimento da mensagem deve ser avaliado quando a personalização for realizada.
   >
   >Quando você inicia a análise, o comprimento das mensagens é verificado e um aviso é exibido no caso de excedente.

1. Se você usar o conector NetSize ou um conector SMPP, é possível personalizar o nome do remetente do delivery. Para obter mais informações, consulte a seção [Advanced parameters](#advanced-parameters).

## Selecione o público alvo {#selecting-the-target-population}

O processo detalhado ao selecionar a população do target de um delivery é apresentado [nesta seção](../../delivery/using/steps-defining-the-target-population.md).

Para obter mais informações sobre o uso de campos de personalização, consulte [esta seção](../../delivery/using/about-personalization.md).

Para obter mais informações sobre a inclusão de uma lista de propagação, consulte [esta página](../../delivery/using/about-seed-addresses.md).

