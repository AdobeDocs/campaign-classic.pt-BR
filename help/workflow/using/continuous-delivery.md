---
product: campaign
title: Entrega contínua
description: Entrega contínua
feature: Workflows, Channels Activity
exl-id: 9c228cdb-331e-476e-a24c-3c7e23add3bf
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: ht
source-wordcount: '359'
ht-degree: 100%

---

# Entrega contínua{#continuous-delivery}



Uma ação do tipo **Entrega contínua** permite adicionar novos destinatários a uma entrega existente. Esse tipo de entrega evita que você tenha que criar uma nova entrega toda vez: este modo é frequentemente mais eficiente, em especial para alertas de baixo volume ou notificações enviadas quando necessário.

![](assets/do-not-localize/how-to-video.png) [Descubra este recurso no vídeo](#continuous-delivery-video)

Em um nível de template de entrega, você pode especificar um script para calcular o rótulo (e a pasta da campanha) da entrega associada. Se o script calcula uma entrega que ainda não existe, ele será criado imediatamente.

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

Esse conjunto de três valores identifica o target resultante da entrega em tempo real. **[!UICONTROL tableName]** é o nome da tabela que memoriza os identificadores do público-alvo, **[!UICONTROL schema]** é o esquema do público (geralmente nms:recipient) e **[!UICONTROL recCount]** é o número de elementos na tabela.

A transição associada ao complemento tem os mesmos parâmetros.

## Como configurar uma entrega contínua

Esta seção explica como configurar uma entrega contínua.

A **entrega contínua** permite adicionar novos destinatários a uma entrega existente, o que evita a criação de uma nova entrega cada vez que um novo destinatário for adicionado. Você pode atualizar o criativo diretamente no workflow da campanha e ele atualizará o modelo na pasta Recursos do template da entrega.

Uma entrega contínua criará uma ÚNICA entrega. Logs da entrega (broadLog) e logs de rastreamento que fazem referência a uma entrega serão adicionados a cada execução.

![Delivery contínuo](assets/delivery_continuous.jpg)

## Tutorial em vídeo {#continuous-delivery-video}

Este vídeo mostra como configurar uma entrega contínua com um query incremental.

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)

Vídeos extras sobre procedimentos do Campaign Classic estão disponíveis [aqui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=pt-BR).
