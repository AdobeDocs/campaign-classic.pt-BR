---
solution: Campaign Classic
product: campaign
title: Execução do delivery
description: Execução do delivery
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 100%

---


# Execução do delivery{#delivery-execution}

>[!NOTE]
>
>O MTA prioriza o processamento das mensagens transacionais ante qualquer outro delivery.

Na instância de execução, uma vez que os estágios de enriquecimento estejam completos e um template do delivery esteja vinculado ao evento, o delivery será enviado. Todos os deliveries são agrupados na pasta **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]**.

![](assets/messagecenter_deliveries_execinstances_001.png)

Por padrão, eles são classificados em subpastas por mês de delivery.

Essa classificação poderá ser alterada nas propriedades do template de mensagem conforme mostrado abaixo.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>Para instalações hospedadas ou híbridas, se você tiver atualizado para o MTA aprimorado, todas as mensagens transacionais também poderão ser enviadas com o MTA aprimorado do Adobe Campaign para melhorar a capacidade de entrega, a taxa de transferência e o tratamento de rejeição. Todos os impactos são os mesmos das mensagens de marketing padrão e são detalhados no documento [MTA aprimorado do Adobe Campaign](https://helpx.adobe.com/br/campaign/kb/acc-campaign-enhanced-mta.html).