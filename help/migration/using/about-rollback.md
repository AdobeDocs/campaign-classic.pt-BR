---
product: campaign
title: Reverter para a versão anterior
description: Saiba como reverter para a versão anterior
audience: migration
content-type: reference
topic-tags: rollback
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 2594e4943ba24ae65d1fc005da589dc674aa2b0f
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---

# Reverter para a versão anterior{#about-rollback}

![](../../assets/v7-only.svg)

Após uma migração, em caso de problemas, talvez seja necessário reverter para a versão anterior do Campaign.

O procedimento de reversão depende da sua versão inicial do Campaign.

Este é o procedimento para restaurar uma v6.1 de um v7.

1. Recupere o backup do banco de dados e o restaure.
1. Recupere a **Adobe Campaign v6.back** pasta (**nl6.back** no Linux), renomeie-o para **Adobe Campaign v6** (**nl6** no Linux) e restaurá-lo ao seu local original.
1. Reconfigure o IIS atribuindo novamente as portas de escuta para restabelecer a integração do Adobe Campaign v6.1 no nível do Site do IIS.
1. Pare o serviço Adobe Campaign v7.
1. Reinicie o IIS.
1. Reinicie o serviço Adobe Campaign v6.1.

<!--
	
## Restore to Campaign v6.02

Here is the procedure to restore a v6.02 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v6.back** folder (**nl6.back** in Linux), rename it to **Neolane v6** (**nl6** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Adobe Campaign v6.02 at IIS Website level.
1. Stop the Adobe Campaign v6.1 service.
1. Re-start IIS.
1. Restart the Adobe Campaign v6.02 service.

## Restore to Campaign v5.11

Here is the procedure to restore a v5.11 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v5.back** folder (**nl5.back** in Linux), rename it to **Neolane v5** (**nl5** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Neolane v5 at IIS Website level.
1. Stop the Adobe Campaign v7 service.
1. Re-start IIS.
1. Re-start the Adobe Campaign v5 service.

-->