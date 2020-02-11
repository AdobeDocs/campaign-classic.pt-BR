---
title: Restauração da v6.1
seo-title: Restauração da v6.1
description: Restauração da v6.1
seo-description: null
page-status-flag: never-activated
uuid: 3fb71b6f-4d70-4814-a885-4d414a542eca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: e510482c-a56d-4254-90f8-19bd5c545e30
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# Restauração da v6.1{#restoring-v}

Este é o procedimento para restaurar uma v6.1 de uma v7.

1. Recupere o backup do banco de dados e restaure-o.
1. Recupere a pasta **Adobe Campaign v6.back** (**nl6.back** no Linux), renomeie-a para **Adobe Campaign v6** (**nl6** no Linux) e restaure-a para seu local original.
1. Reconfigure o IIS atribuindo novamente as portas de escuta para restabelecer a integração do Adobe Campaign v6.1 no nível do site do IIS.
1. Pare o serviço Adobe Campaign v7.
1. Reinicie o IIS.
1. Reinicie o serviço Adobe Campaign v6.1.

