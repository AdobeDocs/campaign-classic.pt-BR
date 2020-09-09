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
source-git-commit: 3566f42b92cc1b7280bf9b6e9e0b4da7a54f61db
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 100%

---


# Delivery contínuo{#continuous-delivery}

Uma ação do tipo **Delivery contínuo** permite adicionar novos recipients a um delivery existente. Esse tipo de delivery evita que você tenha que criar um novo delivery toda vez: este modo é frequentemente mais eficiente, em especial para alertas de baixo volume ou notificações enviadas quando necessário. Em um nível de template de delivery, você pode especificar um script para calcular o rótulo (e a pasta da campanha) do delivery associado. Se o script calcula um delivery que ainda não existe, ele será criado imediatamente.

![](assets/edit_diffusion_fil.png)

A opção **[!UICONTROL Process errors]** exibe uma transição específica que será ativada se um erro for gerado. Nesse caso, o workflow não entra no modo de erro e continua a execução.

Os erros considerados são erros do sistema de arquivos (o arquivo não pôde ser movido, o diretório não pôde ser acessado etc.).

Essa opção não processa erros relacionados à configuração de atividade, ou seja, valores inválidos.

## Parâmetros de entrada {#input-parameters}

* tableName
* schema

Cada evento de entrada deve especificar um target definido por esses parâmetros.

Apenas quando a opção **[!UICONTROL Specified by the inbound event]** está selecionada.

## Parâmetros de output {#output-parameters}

* tableName
* schema
* recCount

Esse conjunto de três valores identifica o target resultante do delivery em tempo real. **[!UICONTROL tableName]** é o nome da tabela que memoriza os identificadores do público-alvo, **[!UICONTROL schema]** é o esquema do público (geralmente nms:recipient) e **[!UICONTROL recCount]** é o número de elementos na tabela.

A transição associada ao complemento tem os mesmos parâmetros.

## Como configurar um delivery contínuo

Esta seção explica como configurar um delivery contínuo.

O **delivery contínuo** permite adicionar novos recipients a um delivery existente, o que evita a criação de um novo delivery cada vez que um novo recipient for adicionado. Você pode atualizar o criativo diretamente no workflow da campanha e ele atualizará o modelo na pasta Recursos do template do delivery.

Um delivery contínuo criará um ÚNICO delivery. Logs do delivery (broadLog) e logs de rastreamento que fazem referência a um delivery serão adicionados a cada execução.

![Delivery contínuo](assets/delivery_continuous.jpg)

Este vídeo mostra como configurar um delivery contínuo com um query incremental.

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)
