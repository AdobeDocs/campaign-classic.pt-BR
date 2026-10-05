---
product: campaign
title: Criar tipos de evento
description: Saiba como criar tipos de evento que corresponderão às mensagens transacionais que você deseja enviar no Adobe Campaign Classic
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
TQID: 'https://experienceleague.adobe.com/WfR-CUGmR3XeEQgBwd22RZPpSMF0Gja-7GewIIIxWug'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 100%
---
# Criar tipos de evento {#creating-event-types}



Para garantir que cada evento possa ser alterado em uma mensagem personalizada, primeiro é necessário criar **tipos de evento**.

Ao [criar um modelo de mensagem](../../message-center/using/creating-the-message-template.md), você selecionará o tipo de evento que corresponde à mensagem que deseja enviar.

>[!IMPORTANT]
>
>Você deve criar tipos de evento antes de poder usá-los em modelos de mensagem.

Para criar tipos de evento que serão processados pelo Adobe Campaign, siga as etapas abaixo:

1. Faça logon na **instância de controle**.

1. Vá até a pasta **[!UICONTROL Administration > Platform > Enumerations]** da árvore.

1. Selecione **[!UICONTROL Event type]** na lista.

1. Clique em **[!UICONTROL Add]** para criar um valor enumeração. Pode ser uma confirmação de pedido, uma alteração de senha, uma alteração de entrega de pedido etc.

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >Cada tipo de evento deve corresponder a um valor na enumeração **[!UICONTROL Event type]**.

1. Após a criação dos valores da lista discriminada, faça logoff e logon novamente na instância para que a criação seja efetivada.

>[!NOTE]
>
>Saiba mais sobre como **trabalhar com enumerações** na [documentação do Adobe Campaign v8 (console)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}.



