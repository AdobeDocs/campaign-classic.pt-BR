---
product: campaign
title: Configurações de execução
description: Configurações de execução
feature: Interaction, Offers
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: e2dea4a0-9ed8-47b6-a16b-eeee653d2290
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 93%

---

# Configurações de execução{#execution-settings}



Ao criar uma simulação, é possível especificar as configurações de execução, se necessário. Essas configurações permitem executar a simulação durante um período de pouca atividade, dependendo da prioridade, ou registrar queries SQL no log. Esta etapa é opcional.

Essas configurações podem ser alteradas posteriormente na guia **[!UICONTROL General]** da janela de simulação.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]**: permite agendar a simulação com base na prioridade escolhida (baixa, média ou alta) para otimizar os desempenhos do Adobe Campaign.
* **[!UICONTROL Priority]**: este é o nível aplicado à simulação para o agendá-la. Quando a opção **[!UICONTROL Schedule execution for a time of low activity]** é marcada, o fluxo de trabalho de processamento de campanha seleciona um momento de baixa atividade para iniciar a campanha.
* **[!UICONTROL Log SQL queries in the journal]**: essa funcionalidade destina-se somente a usuários especializados. Ela permite adicionar uma guia ao log exibindo queries SQL para detectar possíveis defeitos se a simulação terminar com erros.
