---
product: campaign
title: Atualização da lista trimestral usando um query incremental
description: Neste caso de uso, um query incremental é usado para atualizar automaticamente uma lista de recipients.
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 0d3e7046-313a-42a6-9155-3365e8d60bac
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 100%

---

# Atualização da lista trimestral usando um query incremental {#quarterly-list-update}

![](../../assets/common.svg)

No exemplo a seguir, um [query incremental](incremental-query.md) é usado para atualizar automaticamente uma lista de recipients. Esses recipients são alvos como parte das campanhas de marketing sazonais.

Como essas campanhas são iniciadas no início de cada temporada para oferecer atividades esportivas relevantes, essas listas são atualizadas a cada trimestre. No entanto, um recipient só deve ser alvo dessa campanha uma vez a cada 9 meses. Isso permite espaçar a frequência de elegibilidade do recipient e oferecer atividades para diferentes estações ao longo dos anos.

![](assets/incremental_query_example.png)

1. Adicione um query incremental, bem como uma atividade de atualização da lista em um novo workflow.
1. Configure a guia **[!UICONTROL Incremental query]** da atividade, conforme especificado em [Criação de query](query.md#creating-a-query).
1. Selecione a guia **[!UICONTROL Scheduling & History]** e especifique um histórico de 270 dias. Um recipient que já foi direcionado não será direcionado novamente por um período de 270 dias ou aproximadamente 9 meses.

   Clique no botão **[!UICONTROL Change...]**

1. Para garantir que a lista seja atualizada antes do início de cada estação, selecione **[!UICONTROL Monthly]**.
1. Na próxima tela, selecione março, junho, setembro e dezembro. Escolha o dia 20 do mês e escolha o horário que deseja iniciar o workflow.
1. Em seguida, selecione o período de validade do query. Por exemplo, se você quiser que essa atividade fique ativa permanentemente, selecione **[!UICONTROL Permanent validity]**.

   ![](assets/incremental_query_example_2.png)

1. Após a aprovação do query incremental, configure a atividade de atualização da lista como explicado em [List update](list-update.md).

O workflow será iniciado automaticamente e imediatamente antes do início de cada estação. A lista será atualizada com os novos recipients qualificados para receber as ofertas.
