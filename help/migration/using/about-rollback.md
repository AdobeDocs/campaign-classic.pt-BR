---
solution: Campaign Classic
product: campaign
title: Reverter para a versão anterior
description: Saiba como reverter para a versão anterior
audience: migration
content-type: reference
topic-tags: rollback
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
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
1. Recupere a pasta **Adobe Campaign v6.back** (**nl6.back** no Linux), renomeie-a para **Adobe Campaign v6** (**nl6** no Linux) e restaure-a para a localização original.
1. Reconfigure o IIS atribuindo novamente as portas de escuta para restabelecer a integração do Adobe Campaign v6.1 no nível do site do IIS.
1. Pare o serviço Adobe Campaign v7.
1. Start IIS.
1. Reinicie o serviço Adobe Campaign v6.1.

## Restauração para a Campanha v6.02

Este é o procedimento para restaurar uma v6.02 de uma v7.

1. Recupere o backup do banco de dados e restaure-o.
1. Recupere a pasta **Neolane v6.back** (**nl6.back** no Linux), renomeie-a para **Neolane v6** (**nl6** no Linux) e restaure-a à localização original.
1. Reconfigure o IIS atribuindo novamente as portas de escuta para restabelecer a integração do Adobe Campaign v6.02 no nível do site do IIS.
1. Pare o serviço Adobe Campaign v6.1.
1. Start IIS.
1. Reinicie o serviço Adobe Campaign v6.02.

## Restauração para a Campanha v5.11

Este é o procedimento para restaurar uma v5.11 de uma v7.

1. Recupere o backup do banco de dados e restaure-o.
1. Recupere a pasta **Neolane v5.back** (**nl5.back** no Linux), renomeie-a para **Neolane v5** (**nl5** no Linux) e restaure-a para a localização original.
1. Reconfigure o IIS atribuindo novamente as portas de escuta para restabelecer a integração do Neolane v5 no nível do site do IIS.
1. Pare o serviço Adobe Campaign v7.
1. Start IIS.
1. Restart o serviço Adobe Campaign v5.
