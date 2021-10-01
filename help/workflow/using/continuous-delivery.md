---
product: campaign
title: Delivery contínuo
description: Delivery contínuo
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 9c228cdb-331e-476e-a24c-3c7e23add3bf
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: ht
source-wordcount: '364'
ht-degree: 100%

---

# Delivery contínuo{#continuous-delivery}

![](../../assets/common.svg)

Uma ação do tipo **Delivery contínuo** permite adicionar novos recipients a um delivery existente. Esse tipo de delivery evita que você tenha que criar um novo delivery toda vez: este modo é frequentemente mais eficiente, em especial para alertas de baixo volume ou notificações enviadas quando necessário.

![](assets/do-not-localize/how-to-video.png) [Descubra este recurso no vídeo](#continuous-delivery-video)

Em um nível de template de delivery, você pode especificar um script para calcular o rótulo (e a pasta da campanha) do delivery associado. Se o script calcula um delivery que ainda não existe, ele será criado imediatamente.

![](assets/edit_diffusion_fil.png)

A opção **[!UICONTROL Process errors]** exibe uma transição específica que será ativada se um erro for gerado. Nesse caso, o workflow não entra no modo de erro e continua a execução.

Os erros considerados são erros do sistema de arquivos (o arquivo não pôde ser movido, o diretório não pôde ser acessado etc.).

Essa opção não processa erros relacionados à configuração de atividade, ou seja, valores inválidos.

## Parâmetros de entrada {#input-parameters}

* tableName
* schema

Cada evento de entrada deve especificar um target definido por esses parâmetros.

Apenas quando a opção **[!UICONTROL Specified by the inbound event]** está selecionada.

## Parâmetros de saída {#output-parameters}

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

## Tutorial em vídeo {#continuous-delivery-video}

Este vídeo mostra como configurar um delivery contínuo com um query incremental.

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)

Vídeos extras sobre procedimentos do Campaign Classic estão disponíveis [aqui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=pt-BR).
