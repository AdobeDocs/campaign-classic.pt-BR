---
product: campaign
title: Entrega recorrente
description: Saiba mais sobre a atividade de fluxo de trabalho de entrega recorrente
feature: Workflows
hide: true
exl-id: efd2cdfb-2e5f-4672-8be8-a424481b11ed
TQID: https://experienceleague.adobe.com/a33apxZWE9H0Y3ukmFMQMrep1aY95iswu40y-ZjOd0U
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 289
ht-degree: 100%

---

# Entrega recorrente{#recurring-delivery}

Uma atividade **[!UICONTROL Recurring delivery]** permite configurar uma ocorrência de modelo de entrega específico para uma campanha.

![](assets/do-not-localize/how-to-video.png) [Conheça este recurso no vídeo](#recurring-delivery-video)

Essa atividade só está disponível na guia **[!UICONTROL Targeting and workflows]** localizada em uma campanha.

Para fazer isso:

1. Selecione o modelo de entrega no qual a atividade será baseada.

   ![](assets/recurring_delivery_001.png)

1. Configure o modelo de entrega.

O processo de configuração dessa atividade é semelhante ao da criação de um modelo de entrega em termos das opções disponíveis. Para obter mais informações, consulte esta [seção](../../delivery/using/about-templates.md).

>[!CAUTION]
>
>As entregas recorrentes não oferecem suporte à visualização de conteúdo ou ao envio de provas, incluindo elementos de personalização de [dados de público-alvo](../../workflow/using/data-life-cycle.md#target-data).

Para obter um exemplo de uso dessa atividade, consulte esta [seção](sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Como configurar uma entrega recorrente {#set-up-recurring-delivery}

Uma **entrega recorrente** criará uma nova instância de entrega toda vez que for executada. Por exemplo, se o fluxo de trabalho estiver programado para ser executado uma vez por semana, o resultado será 52 entregas em um ano. Também significa que o log abrangente e os logs de rastreamento serão separados por cada instância da entrega.

![Entrega recorrente](assets/delivery_recurring.jpg)

Se desejar impedir a execução de uma entrega recorrente, cancele completamente a campanha ou interrompa a execução do fluxo de trabalho. Parar a entrega no painel do Campaign só interromperá a ocorrência da entrega: as próximas instâncias da entrega recorrente continuarão sendo criadas em cada execução de fluxo de trabalho.

>[!NOTE]
>
>Não é possível enviar uma prova de uma atividade do tipo **[!UICONTROL Recurring delivery]**.
> 
>Para criar uma entrega diretamente por meio de um fluxo de trabalho da campanha, use as atividades específicas predefinidas do canal (por exemplo **[!UICONTROL Recurring delivery]**).

## Tutorial em vídeo {#recurring-delivery-video}

Este vídeo explica como configurar uma entrega recorrente e uma atividade de scheduler.

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

Vídeos extras sobre procedimentos do Campaign Classic estão disponíveis [aqui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=pt-BR).
