---
product: campaign
title: Sobre os acionadores da Adobe Experience Cloud
description: Introdução à implementação dos acionadores da Adobe Experience Cloud
feature: Triggers
badge-v7: label="v7" type="Informative" tooltip="Aplicável ao Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Também se aplica ao Campaign v8"
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '269'
ht-degree: 100%

---

# Trabalhar com acionadores do Campaign e da Experience Cloud{#about-adobe-experience-triggers}

[!DNL Triggers] é uma integração entre o Adobe Campaign e o Adobe Analytics usando o pipeline. O pipeline recupera as ações ou acionadores dos usuários do seu site. O abandono do carrinho é um exemplo de acionador. Os acionadores são processados no Adobe Campaign para enviar emails em tempo quase real.

>[!CAUTION]
>
>Esse recurso não está disponível para uso imediato como parte do produto. Para esta implementação, primeiro você precisa abrir um tíquete com o Suporte da Adobe. Em seguida, você poderá seguir as etapas detalhadas nesta [página](../../integrations/using/configuring-pipeline.md#prerequisites).

O [!DNL Triggers] executa ações de marketing em um curto intervalo de tempo após a ação de um usuário. O tempo médio de resposta é de menos de uma hora.

Ele permite integrações mais ágeis, pois a configuração é mínima e não há envolvimento de terceiros.
Também aceita grandes volumes de tráfego sem afetar o desempenho das atividades de marketing. Como exemplo, a integração pode processar um milhão de acionadores por hora.

![](assets/do-not-localize/book.png) Saiba como [criar um acionador da Experience Cloud](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html?lang=pt-BR) e identificar, definir e monitorar comportamentos críticos de consumidores.

## Arquitetura de [!DNL Triggers] {#triggers-architecture}

O processo [!DNL pipelined] está sempre em execução no servidor de marketing do Adobe Campaign. Ele se conecta ao pipeline, recupera os eventos e os processa imediatamente.

![](assets/triggers_2.png)

O processo [!DNL pipelined] faz logon na Experience Cloud usando um serviço de autenticação e envia uma chave privada. O serviço de autenticação retorna um token. O token é usado para a autenticação ao recuperar os eventos.

Para obter mais informações sobre autenticação, consulte esta [página](../../integrations/using/configuring-adobe-io.md).
