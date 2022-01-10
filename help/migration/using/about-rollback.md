---
product: campaign
title: Reverter para a versão anterior
description: Saiba como reverter para a versão anterior
audience: migration
content-type: reference
topic-tags: rollback
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 8610d29a3df1080f1622a2cb3685c0961fb40092
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Reverter para a versão anterior{#about-rollback}

![](../../assets/v7-only.svg)

Após uma migração, em caso de problemas, talvez seja necessário reverter para a versão anterior do Campaign.

O procedimento de reversão depende da sua versão inicial do Campaign.

## Restaurar para o Campaign v6.1

Este é o procedimento para restaurar uma v6.1 de um v7.

1. Recupere o backup do banco de dados e o restaure.
1. Recupere a **Adobe Campaign v6.back** pasta (**nl6.back** no Linux), renomeie-o para **Adobe Campaign v6** (**nl6** no Linux) e restaurá-lo ao seu local original.
1. Reconfigure o IIS atribuindo novamente as portas de escuta para restabelecer a integração do Adobe Campaign v6.1 no nível do Site do IIS.
1. Pare o serviço Adobe Campaign v7.
1. Reinicie o IIS.
1. Reinicie o serviço Adobe Campaign v6.1.

## Restaurar para o Campaign v6.02

Este é o procedimento para restaurar uma v6.02 de um v7.

1. Recupere o backup do banco de dados e o restaure.
1. Recupere a **Neolane v6.back** pasta (**nl6.back** no Linux), renomeie-o para **Neolane v6** (**nl6** no Linux) e restaurá-lo ao seu local original.
1. Reconfigure o IIS atribuindo novamente as portas de escuta para restabelecer a integração do Adobe Campaign v6.02 no nível do Site do IIS.
1. Pare o serviço Adobe Campaign v6.1.
1. Reinicie o IIS.
1. Reinicie o serviço Adobe Campaign v6.02.

## Restaurar para o Campaign v5.11

Este é o procedimento para restaurar um v5.11 de um v7.

1. Recupere o backup do banco de dados e o restaure.
1. Recupere a **Neolane v5.back** pasta (**nl5.back** no Linux), renomeie-o para **Neolane v5** (**nl5** no Linux) e restaurá-lo ao seu local original.
1. Reconfigure o IIS atribuindo novamente as portas de escuta para restabelecer a integração do Neolane v5 no nível do Site do IIS.
1. Pare o serviço Adobe Campaign v7.
1. Reinicie o IIS.
1. Reinicie o serviço Adobe Campaign v5.
