---
product: campaign
title: Criar e identificar a entrega
description: Criar e identificar a entrega
feature: Channel Configuration
role: User
hide: true
exl-id: 6e37bc14-b1a9-42af-8c28-ae4b5bcaa055
TQID: https://experienceleague.adobe.com/-Vr-ox-BTkhYDI3ccBGML5CCkPGz-rSakyXPhgz1Isg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 277
ht-degree: 100%

---

# Criar e identificar a entrega {#create-and-identify-the-delivery}

## Criar a entrega {#creating-the-delivery}

Você poderá criar uma entrega usando a visão geral ou o menu **[!UICONTROL Create > Delivery]**.


Para criar uma entrega, clique em **[!UICONTROL Create]** acima da lista de entregas. Ao criar uma nova entrega, você deverá indicar o canal de entrega usado. Para fazer isso, selecione o modelo de entrega apropriado na lista suspensa no campo **[!UICONTROL Delivery template]**.

![](assets/s_ncs_user_wizard_email01_1.png)

Um modelo padrão é fornecido para cada canal instalado: correspondência direta, email, fax, telefone, canal móvel (SMS), Facebook, X (anteriormente conhecido como Twitter) etc.

>[!NOTE]
>
>Os canais oferecidos na lista dependem do contrato de licença.

Você poderá criar novos modelos de entrega para pré-configurar parâmetros específicos de acordo com suas necessidades. Para obter mais informações, consulte [esta seção](about-templates.md).

## Identificar a entrega {#identifying-the-delivery}

Você precisa concluir os parâmetros para identificar a entrega. Para fazer isso:

1. Insira um nome para a entrega no campo **[!UICONTROL Label]**.

   Um código de entrega também poderá ser atribuído. O nome da entrega e seu código aparecerão na lista de entregas, mas não poderão ser vistos pelos destinatários.

1. Adicione uma descrição no campo **[!UICONTROL Description]**.
1. Selecione a natureza da entrega no campo relevante. Essas informações são úteis para o rastreamento da entrega: você poderá filtrar com base nesse critério na lista de entrega ou criar consultas usando esse critério de seleção.

   ![](assets/s_ncs_user_email_del_nature.png)

1. Clique em **[!UICONTROL Continue]** para confirmar essas informações e exibir a janela de configuração de mensagem.

O conteúdo da entrega está pronto para ser configurado. A definição do conteúdo da entrega é específica para cada canal. Para obter mais informações, consulte a seção dedicada:

* [Definir o conteúdo do email](defining-the-email-content.md)
* [Definir o conteúdo do SMS](sms-create.md#defining-the-sms-content)
* [Definir o conteúdo da correspondência direta](defining-the-direct-mail-content.md)
* [Notificações por push](about-mobile-app-channel.md)
