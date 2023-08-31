---
product: campaign
title: Criar filtros
description: Saiba como criar filtros para uma tabela personalizada
feature: Profiles, Custom Resources
role: Data Engineer, Developer
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
exl-id: 6fad3dac-9af0-4796-adcf-d1de4b255aca
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 18%

---

# Criar filtros{#creating-filters}

Assim como a tabela de recipients integrada fornecida com o Adobe Campaign, a nova tabela de recipients pode receber um lote de filtros predefinidos.

Esses filtros estarão disponíveis na janela de seleção de público alvo com as mesmas funcionalidades que os segmentos para recipients (usando formulários de entrada de parâmetros, pastas etc.).

1. Vá para o nó **[!UICONTROL Administration > Configuration > Predefined filters]**
1. Crie um novo filtro.
1. Insira o **[!UICONTROL Label]** do filtro e, em seguida, selecione o schema que corresponde à tabela do recipient externo no **[!UICONTROL Document type]** campo.
1. Crie seu **[!UICONTROL filtering conditions]** com base nos campos do esquema.
1. Salve o filtro.
