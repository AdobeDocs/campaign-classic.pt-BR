---
title: Delivery contínuo
seo-title: Delivery contínuo
description: Delivery contínuo
seo-description: null
page-status-flag: never-activated
uuid: af8b4582-299e-47f9-9819-987b35db94ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 9d80be19-8dde-4278-ab5f-23f364fe422e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Delivery contínuo{#continuous-delivery}

Uma ação do tipo **Delivery contínuo** permite adicionar novos recipients a um delivery existente. Esse tipo de entrega evita que você tenha que criar uma nova entrega toda vez: Este modo é frequentemente mais eficiente, em especial para alertas de baixo volume ou notificações enviadas quando e quando necessário. Em um nível de template de delivery, você pode especificar um script para calcular o rótulo (e a pasta da campanha) do delivery associado. Se o script calcula um delivery que ainda não existe, ele será criado imediatamente.

![](assets/edit_diffusion_fil.png)

The **[!UICONTROL Process errors]** option displays a particular transition which will be activated if an error is generated. Nesse caso, o workflow não entra no modo de erro e continua a execução.

Os erros considerados são erros do sistema de arquivos (o arquivo não pôde ser movido, o diretório não pôde ser acessado etc.).

Essa opção não processa erros relacionados à configuração de atividade, ou seja, valores inválidos.

## Parâmetros de entrada {#input-parameters}

* tableName
* schema

Cada evento de entrada deve especificar um target definido por esses parâmetros.

Somente quando a **[!UICONTROL Specified by the inbound event]** opção é selecionada.

## Parâmetros de output {#output-parameters}

* tableName
* schema
* recCount

Esse conjunto de três valores identifica o target resultante do delivery em tempo real. **[!UICONTROL tableName]** é o nome da tabela que memoriza os identificadores do alvo, **[!UICONTROL schema]** é o esquema da população (normalmente nms:customer) e **[!UICONTROL recCount]** é o número de elementos na tabela.

A transição associada ao complemento tem os mesmos parâmetros.
