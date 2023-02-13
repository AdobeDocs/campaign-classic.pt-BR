---
product: campaign
title: Sobre os acionadores da Adobe Experience Cloud
description: Introdução à implementação dos acionadores da Adobe Experience Cloud
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 0a59b0dbdbe70cf8993ce7153b8f3c049c1f1108
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 100%

---

# Trabalhar com acionadores do Campaign e da Experience Cloud{#about-adobe-experience-triggers}

![](../../assets/common.svg)

[!DNL Triggers] é uma integração entre o Adobe Campaign e o Adobe Analytics usando o pipeline. O pipeline recupera as ações ou acionadores dos usuários do seu site. O abandono do carrinho é um exemplo de acionador. Os acionadores são processados no Adobe Campaign para enviar emails em tempo quase real.

>[!CAUTION]
>
>Esse recurso não está disponível para uso imediato como parte do produto. Para esta implementação, primeiro você precisa abrir um tíquete com o Suporte da Adobe. Em seguida, você poderá seguir as etapas detalhadas nesta [página](../../integrations/using/configuring-pipeline.md#prerequisites).

O [!DNL Triggers] executa ações de marketing em um curto intervalo de tempo após a ação de um usuário. O tempo médio de resposta é de menos de uma hora.

Ele permite integrações mais ágeis, pois a configuração é mínima e não há envolvimento de terceiros.
Também aceita grandes volumes de tráfego sem afetar o desempenho das atividades de marketing. Como exemplo, a integração pode processar um milhão de acionadores por hora.

## Arquitetura de [!DNL Triggers] {#triggers-architecture}

O processo [!DNL pipelined] está sempre em execução no servidor de marketing do Adobe Campaign. Ele se conecta ao pipeline, recupera os eventos e os processa imediatamente.

![](assets/triggers_2.png)

O processo [!DNL pipelined] faz logon na Experience Cloud usando um serviço de autenticação e envia uma chave privada. O serviço de autenticação retorna um token. O token é usado para a autenticação ao recuperar os eventos.

Para obter mais informações sobre autenticação, consulte esta [página](../../integrations/using/configuring-adobe-io.md).
