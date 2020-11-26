---
solution: Campaign Classic
product: campaign
title: Delivery recorrente
description: Saiba mais sobre a atividade de workflow de delivery recorrente
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 100%

---


# Delivery recorrente{#recurring-delivery}

Uma atividade **[!UICONTROL Recurring delivery]** permite configurar uma ocorrência de template de delivery específico para uma campanha.

Essa atividade só está disponível na guia **[!UICONTROL Targeting and workflows]** localizada em uma campanha.

Para fazer isso:

1. Selecione o template delivery no qual a atividade será baseada.

   ![](assets/recurring_delivery_001.png)

1. Configure o template de delivery.

O processo de configuração dessa atividade é semelhante ao da criação de um template de delivery em termos das opções disponíveis. Para obter mais informações, consulte esta [seção](../../delivery/using/about-templates.md).

Para obter um exemplo de uso dessa atividade, consulte esta [seção](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Como configurar um delivery recorrente

Um **delivery recorrente** criará uma nova instância de delivery toda vez que for executado. Por exemplo, se o workflow estiver programado para ser executado uma vez por semana, o resultado será 52 deliveries em um ano. Também significa que o log abrangente e os logs de rastreamento serão separados por cada instância do delivery.

![Delivery recorrente](assets/delivery_recurring.jpg)

Este vídeo explica como configurar um delivery recorrente e uma atividade de scheduler.

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

>[!NOTE]
>
>Não é possível enviar uma prova de uma atividade do tipo **[!UICONTROL Recurring delivery]**.\
>Para criar um delivery diretamente por meio de um workflow da campanha, use as atividades específicas predefinidas do canal (por exemplo **[!UICONTROL Email delivery]**).
