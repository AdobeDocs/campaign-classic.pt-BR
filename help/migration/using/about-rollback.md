---
product: campaign
title: Reverter para a versão anterior
description: Saiba como reverter para a versão anterior
audience: migration
content-type: reference
topic-tags: rollback
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Reverter para a versão anterior{#about-rollback}

![](../../assets/v7-only.svg)

Após uma migração, em caso de problemas, talvez seja necessário reverter para a versão anterior do Campaign.

O procedimento de reversão depende da sua versão inicial do Campaign.

## Restauração da v6.1

Este é o procedimento para restaurar uma v6.1 de um v7.

1. Recupere o backup do banco de dados e o restaure.
1. Recupere a pasta **Adobe Campaign v6.back** (**nl6.back** no Linux), renomeie-a para **Adobe Campaign v6** (**nl6** no Linux) e restaure-a no seu local original.
1. Reconfigure o IIS atribuindo novamente as portas de escuta para restabelecer a integração do Adobe Campaign v6.1 no nível do Site do IIS.
1. Pare o serviço Adobe Campaign v7.
1. Reinicie o IIS.
1. Reinicie o serviço Adobe Campaign v6.1.

## Restauração para o Campaign v6.02

Este é o procedimento para restaurar uma v6.02 de um v7.

1. Recupere o backup do banco de dados e o restaure.
1. Recupere a pasta **Neolane v6.back** (**nl6.back** no Linux), renomeie-a para **Neolane v6** (**nl6** no Linux) e restaure-a para seu local original.
1. Reconfigure o IIS atribuindo novamente as portas de escuta para restabelecer a integração do Adobe Campaign v6.02 no nível do Site do IIS.
1. Pare o serviço Adobe Campaign v6.1.
1. Reinicie o IIS.
1. Reinicie o serviço Adobe Campaign v6.02.

## Restauração para o Campaign v5.11

Este é o procedimento para restaurar um v5.11 de um v7.

1. Recupere o backup do banco de dados e o restaure.
1. Recupere a pasta **Neolane v5.back** (**nl5.back** no Linux), renomeie-a para **Neolane v5** (**nl5** no Linux) e restaure-a para seu local original.
1. Reconfigure o IIS atribuindo novamente as portas de escuta para restabelecer a integração do Neolane v5 no nível do Site do IIS.
1. Pare o serviço Adobe Campaign v7.
1. Reinicie o IIS.
1. Reinicie o serviço Adobe Campaign v5.
