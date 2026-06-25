---
product: campaign
title: Criar SMS com o Campaign
description: Saiba como criar SMS com o Campaign
feature: SMS
role: User
hide: true
exl-id: 94aa4628-d973-433d-b963-b078e2d6672b
TQID: https://experienceleague.adobe.com/ENt9cwc7OjXcMr5tbkg2f3BxpPBNtVytVTw70NQZPyI
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 465
ht-degree: 100%

---

# Criar uma entrega de SMS {#creating-a-sms-delivery}

## Selecionar o canal de entrega {#selecting-the-delivery-channel}

Para criar uma nova entrega de SMS, siga as etapas abaixo:

>[!NOTE]
>
>Os conceitos globais sobre a criação de entregas são apresentados na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=pt-BR){target="_blank"}.

1. Crie uma nova entrega, por exemplo, no painel Entrega.
1. Selecione o modelo da entrega **Sent to mobiles (SMPP)** que você criou anteriormente. Para obter mais informações, consulte a seção [Alterar o modelo da entrega](sms-set-up.md#changing-the-delivery-template).

   ![](assets/s_user_mobile_wizard.png)

1. Identifique a entrega com um rótulo, código e descrição. Para obter mais informações, consulte esta seção na [documentação do Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=pt-BR#create-the-delivery){target="_blank"}.
1. Clique em **[!UICONTROL Continue]** para confirmar essas informações e exibir a janela de configuração de mensagem.

## Definir o conteúdo do SMS {#defining-the-sms-content}

Para criar o conteúdo do SMS, siga as etapas abaixo:

1. Insira o conteúdo da mensagem na seção **[!UICONTROL Text content]** do assistente. Os botões da barra de ferramentas permitem importar, salvar ou pesquisar conteúdo. O último botão é usado para inserir campos de personalização.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   O uso de campos de personalização é apresentado na seção [Sobre a personalização](about-personalization.md).

1. Clique em **[!UICONTROL Preview]** na parte inferior da página para exibir a renderização da mensagem com sua personalização. Para iniciar a visualização, selecione um destinatário usando o botão **[!UICONTROL Test personalization]** na barra de ferramentas. Você pode selecionar um destinatário nos targets definidos ou escolher outro destinatário.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   Você pode aprovar a mensagem SMS. Você também pode exibir o conteúdo do SMS na tela do celular que aparece à direita do editor de conteúdo. Clique na tela e use o mouse para rolar pelo conteúdo.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. Clique no link **[!UICONTROL Data loaded]** para exibir as informações referentes ao destinatário.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >As mensagens SMS são limitadas a um comprimento de 160 caracteres, se a página de código Latin-1 (ISO-8859-1) for usada. Se a mensagem for gravada em Unicode, não deverá exceder 70 caracteres. Alguns caracteres especiais podem afetar o comprimento da mensagem. Para obter mais informações sobre tamanho da mensagem, consulte a seção [Transliteração de caracteres SMS](#about-character-transliteration).
   >
   >Quando campos de personalização ou campos de conteúdo condicional estão presentes, o tamanho da mensagem varia de um destinatário para outro. O comprimento da mensagem deve ser avaliado quando a personalização for realizada.
   >
   >Quando você inicia a análise, o comprimento das mensagens é verificado e um aviso é exibido no caso de excedente.

1. Se você usar o conector NetSize ou um conector SMPP, é possível personalizar o nome do remetente da entrega. Para obter mais informações, consulte a seção [Advanced parameters](#advanced-parameters).

## Selecionar a população de destino {#selecting-the-target-population}

O processo detalhado ao selecionar a população do target de uma entrega é apresentado [nesta seção](steps-defining-the-target-population.md).

Para obter mais informações sobre o uso de campos de personalização, consulte [esta seção](about-personalization.md).

Para obter mais informações sobre a inclusão de uma lista de propagação, consulte [esta página](about-seed-addresses.md).
