---
product: campaign
title: Introdução a mensagens transacionais
description: 'Saiba mais sobre o princípio operacional de mensagens transacionais do Adobe Campaign Classic e as principais etapas. '
feature: Transactional Messaging
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: ht
source-wordcount: '644'
ht-degree: 100%

---


# Introdução a mensagens transacionais {#about-transactional-messaging}

![](../../assets/v7-only.svg)

## Visão geral {#overview}

**As mensagens transacionais** (Centro de mensagens) são um módulo do Campaign criado para gerenciar notificações de acionador personalizadas geradas por eventos enviados por um sistema de informações externo.

Uma mensagem transacional é uma comunicação individual e única enviada em tempo real a um usuário por um provedor, como um site. É particularmente esperado, pois contém informações importantes que o recipient deseja verificar ou confirmar.

Os recursos de mensagens transacionais foram projetados para oferecer suporte à escalabilidade e disponibilizar um serviço 24 horas por dia, 7 dias por semana.

* **Quando a entrega é feita?** Como essa mensagem contém informações importantes, o usuário espera que ela seja enviada em tempo real. Portanto, o atraso entre o evento acionado e a mensagem recebida deve ser muito curto.

* **Por que é importante?** Geralmente, uma mensagem transacional tem altas taxas de abertura. Potanto, ela deve ser criada cuidadosamente, uma vez que pode ter um forte impacto no comportamento dos clientes porque define a relação com o cliente.

* **Por exemplo?** Pode ser uma mensagem de boas-vindas após criar uma conta, uma confirmação de que um pedido foi enviado, uma fatura, uma mensagem confirmando uma alteração de senha, uma notificação depois que um cliente navegou em seu site, uma comunicação de indisponibilidade de produto, um extrato de conta etc.

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

O processo geral de mensagens transacionais pode ser descrito da seguinte maneira:

![](assets/transactional-msg-overview.png)

Por exemplo, imagine que você é uma empresa com um site onde os clientes podem comprar produtos.

O Adobe Campaign permite enviar um email de notificação para clientes que adicionaram produtos ao carrinho. Quando um deles sai do site sem concluir a compra (evento externo que aciona um evento do Campaign), um email de abandono de carrinho é enviado automaticamente a eles (entrega de mensagem transacional).

As principais etapas para colocar isso em prática são detalhadas abaixo [nesta seção](#key-steps).

>[!NOTE]
>
>O Adobe Campaign prioriza o processamento das mensagens transacionais antes de qualquer outra entrega.

## Principais etapas {#key-steps}

As principais etapas ao criar e gerenciar mensagens transacionais personalizadas no Adobe Campaign estão resumidas abaixo.

### Etapas para executar na instância de controle

Na **instância de controle**, você deve executar as seguintes ações:

1. [Crie um tipo de evento](../../message-center/using/creating-event-types.md).
1. [Criar o modelo de mensagem](../../message-center/using/creating-the-message-template.md). Você deve vincular um evento à sua mensagem durante essa etapa.
1. [Testar a mensagem](../../message-center/using/testing-message-templates.md).
1. [Publicar o modelo da mensagem](../../message-center/using/publishing-message-templates.md).

>[!NOTE]
>
>Todas as etapas acima são executadas na **instância de controle**. A publicação do modelo na instância de controle também o publicará em todas as **instâncias de execução**. Para obter mais informações sobre as instâncias de mensagens transacionais, consulte [Arquitetura de mensagens transacionais](../../message-center/using/transactional-messaging-architecture.md).

### Processamento de evento na instância de execução

Depois de criar e publicar o modelo de mensagem transacional, se um evento correspondente for acionado, as principais etapas abaixo serão executadas na **instância de execução**:

1. Quando o evento é gerado pelo sistema de informações externo, os dados relevantes são enviados para o Campaign por meio dos métodos **PushEvent** e **PushEvents**. Consulte [Coleção de eventos](../../message-center/using/about-event-processing.md#event-collection).
1. O evento é vinculado ao modelo de mensagem apropriado. Consulte [Roteamento para um modelo](../../message-center/using/about-event-processing.md#routing-towards-a-template).
1. Quando a etapa de enriquecimento estiver concluída, a entrega será enviada. Consulte [Execução da entrega](../../message-center/using/delivery-execution.md). Cada recipient direcionado recebe uma mensagem personalizada.

## Tópicos relacionados {#related-topics}

* [Introdução a canais de comunicação](../../delivery/using/communication-channels.md)
* [Etapas principais de criação da entrega](../../delivery/using/steps-about-delivery-creation-steps.md)
* [Arquitetura de mensagens transacionais](../../message-center/using/transactional-messaging-architecture.md)
* [Acessar relatórios de mensagens transacionais](../../message-center/using/about-transactional-messaging-reports.md)
