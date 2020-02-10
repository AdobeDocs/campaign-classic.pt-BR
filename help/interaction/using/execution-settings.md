---
title: Configurações de execução
seo-title: Configurações de execução
description: Configurações de execução
seo-description: null
page-status-flag: never-activated
uuid: a6549091-0c33-4fe1-adde-de3b285dd456
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: simulating-offers
discoiquuid: 52b5d5a9-10dc-4601-8fe4-962a2334322b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Configurações de execução{#execution-settings}

Ao criar uma simulação, é possível especificar as configurações de execução, se necessário. Essas configurações permitem executar a simulação durante um período de pouca atividade, dependendo da prioridade, ou registrar queries SQL no log. Esta etapa é opcional.

These settings can be changed later in the **[!UICONTROL General]** tab of the simulation window.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** : permite agendar a simulação com base na prioridade escolhida (Baixa, Média ou Alta) para otimizar o desempenho do Adobe Campaign.
* **[!UICONTROL Priority]** : este é o nível aplicado à simulação para agendá-la. When the **[!UICONTROL Schedule execution for a time of low activity]** option is checked, the campaign processing workflow selects a time of low activity to start the campaign.
* **[!UICONTROL Log SQL queries in the journal]** : essa funcionalidade é apenas para usuários especialistas. Ela permite adicionar uma guia ao log exibindo queries SQL para detectar possíveis defeitos se a simulação terminar com erros.

