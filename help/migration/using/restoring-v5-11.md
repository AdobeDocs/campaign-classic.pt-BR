---
title: Restauração da v5.11
seo-title: Restauração da v5.11
description: Restauração da v5.11
seo-description: null
page-status-flag: never-activated
uuid: 4480c97c-5845-483c-a17b-644f05783b4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: ef778333-8e50-402b-9a69-78ac94497c67
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 9%

---


# Restauração da v5.11{#restoring-v}

Este é o procedimento para restaurar uma v5.11 de uma v7.

1. Recupere o backup do banco de dados e restaure-o.
1. Recupere a pasta **Neolane v5.back** (**nl5.back** no Linux), renomeie-a para **Neolane v5** (**nl5** no Linux) e restaure-a para seu local original.
1. Reconfigure o IIS atribuindo novamente as portas de escuta para restabelecer a integração do Neolane v5 no nível do site do IIS.
1. Pare o serviço Adobe Campaign v7.
1. Start IIS.
1. Restart o serviço Adobe Campaign v5.

