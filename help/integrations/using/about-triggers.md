---
product: campaign
title: Sobre os acionadores da Adobe Experience Cloud
description: Introdução à implementação dos acionadores da Adobe Experience Cloud
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: af40fe822c69979a478604595790d4deefd6d5b0
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Trabalhar com acionadores do Campaign e da Experience Cloud{#about-adobe-experience-triggers}

![](../../assets/common.svg)

[!DNL Triggers] é uma integração entre o Adobe Campaign e o Adobe Analytics usando o pipeline. O pipeline recupera as ações ou acionadores dos usuários do seu site. O abandono do carrinho é um exemplo de acionador. Os acionadores são processados no Adobe Campaign para enviar emails em tempo quase real.

>[!CAUTION]
>
>Esse recurso não está disponível para uso imediato como parte do produto. A implementação exige o engajamento da Adobe Consulting. Entre em contato com seu representante da Adobe para obter mais detalhes

O [!DNL Triggers] executa ações de marketing em um curto intervalo de tempo após a ação de um usuário. O tempo médio de resposta é de menos de uma hora.

Ele permite integrações mais ágeis, pois a configuração é mínima e não há envolvimento de terceiros.
Também aceita grandes volumes de tráfego sem afetar o desempenho das atividades de marketing. Como exemplo, a integração pode processar um milhão de acionadores por hora.

## Arquitetura de [!DNL Triggers] {#triggers-architecture}

O processo [!DNL pipelined] está sempre em execução no servidor de marketing do Adobe Campaign. Ele se conecta ao pipeline, recupera os eventos e os processa imediatamente.

![](assets/triggers_2.png)

O processo [!DNL pipelined] faz logon na Experience Cloud usando um serviço de autenticação e envia uma chave privada. O serviço de autenticação retorna um token. O token é usado para a autenticação ao recuperar os eventos.

Para obter mais informações sobre autenticação, consulte esta [página](../../integrations/using/configuring-adobe-io.md).
