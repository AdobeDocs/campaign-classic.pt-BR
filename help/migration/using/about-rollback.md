---
title: Reverter para a versão anterior
description: Saiba como reverter para a versão anterior
page-status-flag: never-activated
uuid: 9d404ca5-e38c-48ba-b5e0-8e70a40482c2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: 0e17abea-5e86-43b5-8bca-ee39d9b24c90
translation-type: tm+mt
source-git-commit: 7a3cdf40da579fc3c4c7fc26b10c160543cc45d7
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---


# Reverter para a versão anterior{#about-rollback}

Após uma migração, em caso de problemas, talvez seja necessário reverter para a versão anterior da Campanha.

O procedimento de reversão depende da sua versão inicial da Campanha.

## Restauração da v6.1

Este é o procedimento para restaurar uma v6.1 de uma v7.

1. Recupere o backup do banco de dados e restaure-o.
1. Recupere a pasta **Adobe Campaign v6.back** (**nl6.back** no Linux), renomeie-a para **Adobe Campaign v6** (**nl6** no Linux) e restaure-a para seu local original.
1. Reconfigure o IIS atribuindo novamente as portas de escuta para restabelecer a integração do Adobe Campaign v6.1 no nível do site do IIS.
1. Pare o serviço Adobe Campaign v7.
1. Start IIS.
1. Reinicie o serviço Adobe Campaign v6.1.

## Restauração para a Campanha v6.02

Este é o procedimento para restaurar uma v6.02 de uma v7.

1. Recupere o backup do banco de dados e restaure-o.
1. Recupere a pasta **Neolane v6.back** (**nl6.back** no Linux), renomeie-a para **Neolane v6** (**nl6** no Linux) e restaure-a para seu local original.
1. Reconfigure o IIS atribuindo novamente as portas de escuta para restabelecer a integração do Adobe Campaign v6.02 no nível do site do IIS.
1. Pare o serviço Adobe Campaign v6.1.
1. Start IIS.
1. Reinicie o serviço Adobe Campaign v6.02.

## Restauração para a Campanha v5.11

Este é o procedimento para restaurar uma v5.11 de uma v7.

1. Recupere o backup do banco de dados e restaure-o.
1. Recupere a pasta **Neolane v5.back** (**nl5.back** no Linux), renomeie-a para **Neolane v5** (**nl5** no Linux) e restaure-a para seu local original.
1. Reconfigure o IIS atribuindo novamente as portas de escuta para restabelecer a integração do Neolane v5 no nível do site do IIS.
1. Pare o serviço Adobe Campaign v7.
1. Start IIS.
1. Restart o serviço Adobe Campaign v5.
