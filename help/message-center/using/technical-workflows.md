---
solution: Campaign Classic
product: campaign
title: Fluxos de trabalho técnicos
description: Fluxos de trabalho técnicos
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 100%

---


# Fluxos de trabalho técnicos{#technical-workflows}

Você deve garantir que os workflows técnicos na instância de controle e as diferentes instâncias de execução tenham sido criados e iniciados realmente antes de implantar qualquer template de mensagem transacional.

Os vários workflows técnicos relacionados a mensagens transacionais (Centro de Mensagens) são divididos entre a instância de controle e a(s) instância(s) de execução.

## Workflows da instância de controle {#control-instance-workflows}

Na instância de controle, caso tenha uma ou várias instâncias de execução registradas, é necessário criar um fluxo de trabalho de arquivamento para cada conta externa **[!UICONTROL Message Center execution instance]**. Clique no botão **[!UICONTROL Create the archiving workflow]** para criar e iniciar o workflow.

![](assets/messagecenter_archiving_002.png)

Os workflows de arquivamento podem ser acessados na pasta **Administration > Production > Message Center**. Depois de criados, os workflows de arquivamento são iniciados automaticamente.

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

## Workflows da instância de execução {#execution-instance-workflows}

Na(s) instância(s) de execução, os workflows técnicos de mensagens transacionais podem ser acessados na pasta **Administration > Production > Message Center.** Você só precisa iniciá-los. Os workflows na lista são:

* **[!UICONTROL Processing batch events]** (internal name: **[!UICONTROL batchEventsProcessing]** ): esse fluxo de trabalho permite dividir eventos em lote em uma fila antes que eles sejam vinculados a um template de mensagem.
* **[!UICONTROL Processing real time events]** (internal name: **[!UICONTROL rtEventsProcessing]** ): esse workflow permite dividir eventos em tempo real em uma fila antes que eles sejam vinculados a um template de mensagem.
* **[!UICONTROL Update event status]** (internal name: **[!UICONTROL updateEventStatus]** ): esse workflow permite que você atribua um status ao evento.

   Os seguintes status de evento estão disponíveis:

   * **[!UICONTROL Pending]**: o evento está na fila. Nenhum template de mensagem foi atribuído a ele.
   * **[!UICONTROL Pending delivery]**: o evento está na fila, um template de mensagem foi atribuído a ele e está sendo processado pelo delivery.
   * **[!UICONTROL Sent]**: esse status é copiado dos logs do delivery. Significa que o delivery foi enviado.
   * **[!UICONTROL Ignored by the delivery]**: esse status é copiado dos logs do delivery. Ele significa que o delivery foi ignorado.
   * **[!UICONTROL Delivery failed]**: esse status é copiado dos logs do delivery. Ele significa que o delivery falhou.
   * **[!UICONTROL Event not taken into account]**: o evento não pôde ser vinculado a um template de mensagem. O evento não será processado.

