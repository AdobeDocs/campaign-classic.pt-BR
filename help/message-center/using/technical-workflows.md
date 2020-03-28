---
title: Fluxos de trabalho técnicos
seo-title: Fluxos de trabalho técnicos
description: Fluxos de trabalho técnicos
seo-description: null
page-status-flag: never-activated
uuid: dfd1b180-86b5-4740-9bad-a0e210f433c5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 2e648e63-06d2-4e8f-9934-066a41d18eac
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Fluxos de trabalho técnicos{#technical-workflows}

Você deve garantir que os workflows técnicos na instância de controle e as diferentes instâncias de execução tenham sido criados e iniciados realmente antes de implantar qualquer template de mensagem transacional.

Os vários workflows técnicos relacionados a mensagens transacionais (Centro de Mensagens) são divididos entre a instância de controle e a(s) instância(s) de execução.

## Workflows da instância de controle {#control-instance-workflows}

Na instância de controle, deve ser criado um workflow de arquivamento por instância de execução. Os workflows de arquivamento podem ser acessados na pasta **Administration > Production > Message Center.** Após criado, os workflows de arquivamento são iniciados automaticamente.

**Arquitetura distribuída**

Se houver uma ou várias instâncias de execução registradas, na instância de controle, deve ser criado um workflow de arquivamento para cada conta externa de **[!UICONTROL Message Center execution instance]**. Clique no botão **[!UICONTROL Create the archiving workflow]** para criar e iniciar o workflow.

![](assets/messagecenter_archiving_002.png)

**Arquitetura mínima**

Depois que os módulos de controle e execução forem instalados na mesma instância, você deve criar o workflow de arquivamento usando o assistente de implantação. Clique no botão **[!UICONTROL Create the archiving workflow]** para criar e iniciar o workflow.

![](assets/messagecenter_archiving_001.png)

## Workflows da instância de execução {#execution-instance-workflows}

Na(s) instância(s) de execução, os workflows técnicos de mensagens transacionais podem ser acessados na pasta **Administration > Production > Message Center.** Você só precisa iniciá-los. Os workflows na lista são:

* **[!UICONTROL Processing batch events]** (internal name: **[!UICONTROL batchEventsProcessing]** ): esse fluxo de trabalho permite dividir eventos em lote em uma fila antes que eles sejam vinculados a um template de mensagem.
* **[!UICONTROL Processing real time events]** (internal name: **[!UICONTROL rtEventsProcessing]** ): esse workflow permite dividir eventos em tempo real em uma fila antes que eles sejam vinculados a um template de mensagem.
* **[!UICONTROL Update event status]** (internal name: **[!UICONTROL updateEventStatus]** ): esse workflow permite que você atribua um status ao evento.

   Os seguintes status de evento estão disponíveis:

   * **[!UICONTROL Pending]**: o evento está na fila. Nenhum template de mensagem foi atribuído a ele.
   * **[!UICONTROL Pending delivery]**: o evento está na fila, um template de mensagem foi atribuído a ele e está sendo processado pelo delivery.
   * **[!UICONTROL Enviado]**: esse status é copiado dos logs de delivery. Significa que o delivery foi enviado.
   * **[!UICONTROL Ignorado pelo delivery]**: esse status é copiado dos logs de delivery. Significa que o delivery foi ignorado.
   * **[!UICONTROL Delivery failed]**: esse status é copiado dos logs do delivery. Significa que o delivery falhou.
   * **[!UICONTROL Event not taken into account]**: o evento não pôde ser vinculado a um template de mensagem. O evento não será processado.

