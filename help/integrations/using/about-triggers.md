---
title: Sobre o Adobe Experience Manager
seo-title: Sobre o Adobe Experience Manager
description: Sobre o Adobe Experience Manager
seo-description: null
page-status-flag: never-activated
uuid: c523822f-8178-4989-bd88-ab402470e540
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 0d617f1c-0d0b-489f-9027-a92b1f1eee37
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0112d5bd052ad66169225073276d1da4f3c245d8
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 3%

---


# Sobre os acionadores da Adobe Experience Cloud{#about-adobe-experience-triggers}

[!DNL Triggers] é uma integração entre o Adobe Campaign e o Adobe Analytics usando o pipeline. O pipeline recupera as ações ou acionadores dos usuários do seu site. O abandono do carrinho é um exemplo de disparo. Os acionadores são processados em Adobe Campaign para enviar emails em tempo quase real.

[!DNL Triggers] execute ações de marketing dentro de um curto intervalo de tempo após a ação de um usuário. O tempo de resposta típico é menos de uma hora.

Ele permite integrações mais ágeis, pois a configuração é mínima e um terceiro não está envolvido.
Ele também suporta grandes volumes de tráfego sem afetar o desempenho das atividades de marketing. Como exemplo, a integração pode processar um milhão de acionadores por hora.

## [!DNL Triggers] arquitetura {#triggers-architecture}

### O que é o Pipeline? {#pipeline-explanation}

>[!CAUTION]
>
>Somente as soluções da Adobe Cloud podem produzir e consumir eventos dos serviços de Pipeline da Adobe. Os sistemas externos à Adobe não podem.

Pipeline é um sistema de mensagens hospedado no Experience Cloud que usa o [Apache Kafka](http://kafka.apache.org/). É uma maneira de transmitir dados facilmente entre soluções. Além disso, o Pipeline é uma fila de mensagens em vez de um banco de dados. Os produtores empurram eventos no gasoduto e os consumidores escutam o fluxo e fazem o que querem com o evento. Eventos são guardados por alguns dias, mas não mais. O objetivo é ouvir 24 horas por dia, 7 dias por semana e processar eventos imediatamente.

![](assets/triggers_1.png)

### Como funciona o Pipeline? {#how-pipeline-work}

O [!DNL pipelined] processo está sempre em execução no servidor de marketing do Adobe Campaign. Ele se conecta ao pipeline, recupera os eventos e os processa imediatamente.

![](assets/triggers_2.png)

O [!DNL pipelined] processo faz logon no Experience Cloud usando um serviço de autenticação e envia uma chave privada. O serviço de autenticação retorna um token. O token é usado para autenticação ao recuperar os eventos. [!DNL Triggers] são recuperados de um serviço Web REST usando uma simples solicitação GET. A resposta é o formato JSON. Os parâmetros para a solicitação incluem o nome do acionador e um ponteiro que indica a última mensagem recuperada. O [!DNL pipelined] processo lida com ele automaticamente.

## Usar a integração do Adobe Experience Cloud Triggers com o Adobe Campaign Classic

Estas são algumas das [!DNL Triggers] práticas recomendadas:

* Os [!DNL Trigger] dados precisam ser armazenados à medida que chegam à Campanha. Ele não deve ser processado diretamente, pois criaria latência.
* O carimbo de data e hora deve ser verificado da mensagem e não da base de dados.
* Use TriggerTimestamp e a ID do acionador para remover duplicados.

>[!CAUTION]
>
>O exemplo abaixo não é fornecido prontamente. Este é um exemplo específico de várias implementações possíveis.

Os eventos de pipeline são baixados automaticamente. Esses eventos podem ser monitorados usando um formulário.

![](assets/triggers_3.png)

O nó do Evento Pipeline não está integrado e precisa ser adicionado, assim como o formulário relacionado precisa ser criado na Campanha. Essas operações são restritas somente a usuários especialistas. Para obter mais informações, consulte estas seções: [Hierarquia](../../configuration/using/about-navigation-hierarchy.md) de navegação e [edição de formulários](../../configuration/using/editing-forms.md).

query de fluxo de trabalho de campanha recorrentes em acionadores e, se corresponderem aos critérios de marketing, start um delivery.

![](assets/triggers_4.png)
