---
solution: Campaign Classic
product: campaign
title: Criar tipos de evento
description: Saiba como criar tipos de evento que corresponderão às mensagens transacionais que você deseja enviar no Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: d39b15b0efc6cbd6ab24e074713be6f8fc90e5fc
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 16%

---

# Criar tipos de evento {#creating-event-types}

Para garantir que cada evento possa ser alterado em uma mensagem personalizada, primeiro é necessário criar **event types**.

Ao [criar um template de mensagem](../../message-center/using/creating-the-message-template.md), você selecionará o tipo de evento que corresponde à mensagem que deseja enviar.

>[!IMPORTANT]
>
>Você deve criar tipos de evento antes de poder usá-los em templates de mensagem.

Para criar tipos de evento que serão processados pelo Adobe Campaign, siga as etapas abaixo:

1. Faça logon na **instância de controle**.

1. Vá para a pasta **[!UICONTROL Administration > Platform > Enumerations]** da árvore.

1. Selecione **[!UICONTROL Event type]** na lista.

1. Clique em **[!UICONTROL Add]** para criar um valor de enumeração. Pode ser uma confirmação do pedido, alteração da senha, alteração do pedido do delivery etc.

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >Cada tipo de evento deve corresponder a um valor na enumeração **[!UICONTROL Event type]** .

1. Após a criação dos valores da lista discriminada, faça logoff e volte na sua instância para que a criação seja efetiva.

>[!NOTE]
>
>Saiba mais sobre listas discriminadas em [Enumeration management](../../platform/using/managing-enumerations.md).


