---
product: campaign
title: Criar tipos de evento
description: Saiba como criar tipos de evento que corresponderão às mensagens transacionais que você deseja enviar no Adobe Campaign Classic
feature: Transactional Messaging, Message Center
badge-v7-only: label="v7" type="Informative" tooltip="Aplica-se somente ao Campaign Classic v7"
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '176'
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

1. Clique em **[!UICONTROL Add]** para criar um valor de lista discriminada. Pode ser uma confirmação de pedido, uma alteração de senha, uma alteração de entrega de pedido etc.

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >Cada tipo de evento deve corresponder a um valor na lista discriminada **[!UICONTROL Event type]**.

1. Após a criação dos valores da lista discriminada, faça logoff e logon novamente na instância para que a criação seja efetivada.

>[!NOTE]
>
>Saiba mais sobre listas detalhadas em [Gerenciamento de lista discriminada](../../platform/using/managing-enumerations.md).


