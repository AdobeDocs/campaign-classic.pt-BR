---
product: campaign
title: Arquitetura
description: Os fluxos de trabalho são administrados por um módulo específico, que pode ser iniciado em vários servidores para compartilhar a carga de processamento
feature: Workflows
hide: true
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
source-git-commit: 76f483dcda9f8a5ed93355d68bb1d1a589d55722
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 100%

---

# Arquitetura {#architecture}



Os fluxos de trabalho são manipulados por um módulo específico. Esse módulo pode ser iniciado em vários servidores para compartilhar a carga de processamento.

![](assets/architecture.png)

* O processo &#39;Executor de instância de fluxo de trabalho&#39; (runwf) executa todas as tarefas de uma determinada instância de fluxo de trabalho. Quando não há tarefas a serem executadas no momento, se torna &#39;passivo&#39;, indicando que seu status é salvo no banco de dados e depois é interrompido.
* O módulo &#39;Servidor de fluxo de trabalho&#39; (wfserver) monitora as instâncias de fluxos de trabalho atuais. Quando há uma tarefa para executar, esse módulo cria um processo para ativar (ou reativar) a instância correspondente.
