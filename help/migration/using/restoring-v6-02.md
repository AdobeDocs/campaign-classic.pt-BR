---
title: Restauração da v6.02
seo-title: Restauração da v6.02
description: Restauração da v6.02
seo-description: null
page-status-flag: never-activated
uuid: df21209b-4825-42fa-a303-f383f872abb5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: 4f65ba19-e9f0-4425-b640-f27c61394859
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# Restauração da v6.02{#restoring-v}

Este é o procedimento para restaurar uma v6.02 de uma v7.

1. Recupere o backup do banco de dados e restaure-o.
1. Recupere a pasta **Neolane v6.back** (**nl6.back** no Linux), renomeie-a para **Neolane v6** (**nl6** no Linux) e restaure-a para seu local original.
1. Reconfigure o IIS atribuindo novamente as portas de escuta para restabelecer a integração do Adobe Campaign v6.02 no nível do site do IIS.
1. Pare o serviço Adobe Campaign v6.1.
1. Reinicie o IIS.
1. Reinicie o serviço Adobe Campaign v6.02.

