---
solution: Campaign Classic
product: campaign
title: Sobre os acionadores da Adobe Experience Cloud
description: Introdução à implementação do Adobe Experience Cloud Triggers
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 93%

---


# Introdução ao Adobe Experience Cloud Triggers{#about-adobe-experience-triggers}

[!DNL Triggers] é uma integração entre o Adobe Campaign e o Adobe Analytics usando o pipeline. O pipeline recupera as ações ou acionadores dos usuários do seu site. O abandono do carrinho é um exemplo de acionador. Os acionadores são processados no Adobe Campaign para enviar emails em tempo quase real.

>[!CAUTION]
>
>Esse recurso não está disponível para uso imediato como parte do produto. A implementação exige o engajamento da Adobe Consulting. Entre em contato com seu representante da Adobe para obter mais detalhes

O [!DNL Triggers] executa ações de marketing em um curto intervalo de tempo após a ação de um usuário. O tempo médio de resposta é de menos de uma hora.

Ele permite integrações mais ágeis, pois a configuração é mínima e não há envolvimento de terceiros.
Também aceita grandes volumes de tráfego sem afetar o desempenho das atividades de marketing. Como exemplo, a integração pode processar um milhão de acionadores por hora.

## [!DNL Triggers] arquitetura {#triggers-architecture}

O processo [!DNL pipelined] está sempre em execução no servidor de marketing do Adobe Campaign. Ele se conecta ao pipeline, recupera os eventos e os processa imediatamente.

![](assets/triggers_2.png)

O processo [!DNL pipelined] faz logon na Experience Cloud usando um serviço de autenticação e envia uma chave privada. O serviço de autenticação retorna um token. O token é usado para a autenticação ao recuperar os eventos.

Para obter mais informações sobre autenticação, consulte esta [página](../../integrations/using/configuring-adobe-io.md).
