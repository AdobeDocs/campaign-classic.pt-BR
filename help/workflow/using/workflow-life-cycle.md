---
title: Ciclo de vida do workflow
description: Saiba mais sobre o ciclo de vida de um fluxo de trabalho.
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 96%

---


# Ciclo de vida do workflow {#workflow-life-cycle}

O ciclo do workflow tem três etapas principais.

* **Em edição**

   Esta é a fase inicial de design: quando o novo workflow é criado, seu status é &quot;Being edited&quot;. O workflow ainda não foi processado pelo servidor e pode ser modificado sem risco.

* **Iniciado**

   Quando a fase inicial de design for concluída, o workflow poderá ser iniciado. Nesta fase, a instância é tratada pelo servidor e as tarefas individuais são executadas. O workflow ainda pode ser modificado com determinadas precauções.

* **Concluído**

   Um workflow é &#39;Concluído&#39; quando não há mais nenhuma tarefa em andamento ou quando um operador tiver interrompido explicitamente a instância.

Por exemplo, as atividades de **Start** e de **Delivery** são destacadas enquanto a atividade de **Aprovação** pisca no workflow abaixo.

![](assets/new-workflow-6.png)

Isso significa que as duas primeiras atividades foram executadas com êxito e que a aprovação está em andamento, ou seja, foi criada, mas ainda não foi concluída.

Os caracteres **574 -Ok** exibidos acima da transição após a atividade de **Delivery** significam que a preparação do delivery teve 574 recipients como alvo e que a operação foi concluída com êxito. Essas informações, que são adicionadas às transições quando são executadas, são calculadas pelas atividades que processam dados.

O workflow é iniciado e aguarda um operador pertencente ao grupo especificado na atividade de **Aprovação** para tomar uma decisão. Os operadores pertencentes ao grupo e que têm um endereço de email ou número de telefone celular são notificados.

A gestão de operador é apresentada nesta [seção](../../platform/using/access-management.md).

Para obter mais informações sobre como monitorar o workflow, consulte [esta seção](../../workflow/using/monitoring-workflow-execution.md).
