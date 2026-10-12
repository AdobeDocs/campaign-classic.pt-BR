---
product: campaign
title: Introdução a mensagens transacionais
description: Saiba mais sobre o princípio operacional de mensagens transacionais do Adobe Campaign Classic e as principais etapas
feature: Transactional Messaging, Message Center
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
TQID: 'https://experienceleague.adobe.com/n4w2hZkuzHlD3Axc1tUCGfBQ13D28j3Xpmdh07tVr4g'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
source-git-commit: 617db6f51887118c965b8938b2b9f14335293875
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 67%
---
# Introdução a mensagens transacionais {#about-transactional-messaging}



## Visão geral {#overview}

**As mensagens transacionais** (Centro de mensagens) são um módulo do Campaign criado para gerenciar notificações de acionador personalizadas geradas por eventos enviados por um sistema de informações externo.

Como parte da transição do Campaign v7 para o v8, o conjunto de documentações do Campaign Classic foi simplificado e reorganizado. Os recursos comuns agora estão disponíveis apenas no conjunto de documentações do Campaign v8. Para saber mais sobre mensagens transacionais, consulte a [documentação do Campaign v8](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/real-time/transactional){target=_blank}.

[![imagem](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/real-time/transactional){target=_blank}

Esta seção aborda a arquitetura de mensagens transacionais e a configuração das instâncias de controle e execução, específicas para implantações locais e híbridas.

>[!IMPORTANT]
>
>As mensagens transacionais exigem uma licença específica. Verifique o contrato de licença.

<!--Before starting with transactional messaging, make sure you read the corresponding [best practices and limitations]().-->

## Princípio operacional das mensagens transacionais {#transactional-messaging-operating-principle}

O módulo de mensagens transacionais do Adobe Campaign é integrado a um sistema de informações que retorna eventos que serão transformados em mensagens transacionais personalizadas. Essas mensagens podem ser enviadas individualmente ou em lotes por email, SMS ou notificações por push.

Esse recurso depende de uma arquitetura específica, em que a **instância de execução** é separada da **instância de controle**. Essa distribuição garante maior disponibilidade e melhor gerenciamento de carga. Para obter mais informações, consulte [Arquitetura de mensagens transacionais](../../message-center/using/transactional-messaging-architecture.md).

>[!NOTE]
>
>Para criar novos usuários para as instâncias de execução do Centro de mensagens hospedadas na Adobe Cloud, você precisará entrar em contato com o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Os usuários do Centro de mensagens são operadores específicos que exigem permissões dedicadas para acessar pastas de **[!UICONTROL Real time events (nmsRtEvent)]**.

>[!NOTE]
>
>O Adobe Campaign prioriza o processamento das mensagens transacionais antes de qualquer outra entrega.

## Principais etapas {#key-steps}

As principais etapas ao criar e gerenciar mensagens transacionais personalizadas no Adobe Campaign estão resumidas abaixo.

### Etapas para executar na instância de controle

Na **instância de controle**, você deve executar as seguintes ações:

1. [Criar um tipo de evento](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/real-time/transactional){target="_blank"} (documentação do Campaign v8).
1. [Criar o modelo de mensagem](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"} (documentação do Campaign v8). Você deve vincular um evento à sua mensagem durante essa etapa.
1. [Testar a mensagem](../../message-center/using/testing-message-templates.md).
1. [Publicar o modelo de mensagem](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"} (documentação do Campaign v8).

>[!NOTE]
>
>Todas as etapas acima são executadas na **instância de controle**. A publicação do modelo na instância de controle também o publicará em todas as **instâncias de execução**. Para obter mais informações sobre as instâncias de mensagens transacionais, consulte [Arquitetura de mensagens transacionais](../../message-center/using/transactional-messaging-architecture.md).

### Processamento de evento na instância de execução

Depois de criar e publicar o modelo de mensagem transacional, se um evento correspondente for acionado, as principais etapas abaixo serão executadas na **instância de execução**:

1. Quando o evento é gerado pelo sistema de informações externo, os dados relevantes são enviados para o Campaign por meio dos métodos **PushEvent** e **PushEvents**. Consulte [Coleção de eventos](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/real-time/event/event-processing#event-collection){target="_blank"} (documentação do Campaign v8).
1. O evento é vinculado ao modelo de mensagem apropriado. Consulte [Roteamento para um modelo](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/real-time/event/event-processing#event-to-template){target="_blank"} (documentação do Campaign v8).
1. Quando a etapa de enriquecimento estiver concluída, a entrega será enviada. Consulte [Execução da entrega](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"} (documentação do Campaign v8). Cada destinatário direcionado recebe uma mensagem personalizada.

## Tópicos relacionados {#related-topics}

* [Introdução a canais de comunicação](../../delivery/using/communication-channels.md)
* [Etapas principais de criação da entrega](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=pt-BR){target="_blank"}
* [Arquitetura de mensagens transacionais](../../message-center/using/transactional-messaging-architecture.md)
* [Acessar relatórios de mensagens transacionais](https://experienceleague.adobe.com/pt-br/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"} (documentação do Campaign v8)
