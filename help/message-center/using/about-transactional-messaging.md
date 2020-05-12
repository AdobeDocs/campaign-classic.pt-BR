---
title: Sobre mensagens transacionais
seo-title: Sobre mensagens transacionais
description: Sobre mensagens transacionais
seo-description: null
page-status-flag: never-activated
uuid: c854daac-8756-44f3-a4e2-be31177ab9d1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: 97df4bd5-a8e3-48f4-87c8-fa090ea3f771
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f4ecdab4c17a6ba8deb3b98079f57bb7a9adf4a0
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 100%

---


# Sobre mensagens transacionais{#about-transactional-messaging}

O envio de mensagens transacionais (Centro de mensagens) é um módulo do Campaign criado para gerenciar mensagens por disparo. Essas mensagens são geradas por eventos disparados dos sistemas de informações e podem ser: fatura, confirmação de pedidos, confirmação de remessa, alteração de senha, notificação de indisponibilidade de produto, extrato de conta ou criação de conta de site, por exemplo.

>[!IMPORTANT]
>
>As mensagens transacionais exigem uma licença específica. Verifique o contrato de licença.

O módulo Centro de mensagens do Adobe Campaign é integrado em um sistema de informações que retorna eventos a serem alterados para mensagens transacionais personalizadas. Essas mensagens podem ser enviadas individualmente ou em batches por email, SMS ou notificações por push.

Nesta arquitetura específica, a célula de execução é separada da instância de controle, o que garante maior disponibilidade e melhor gerenciamento de carga.

>[!NOTE]
>
>Para criar novos usuários para as instâncias de execução do Centro de mensagens hospedadas na Adobe Cloud, você precisará entrar em contato com o Atendimento ao cliente da Adobe. Os usuários do Centro de mensagens são operadores específicos que exigem permissões dedicadas para acessar pastas de &#39;eventos em tempo real&#39; (nmsRtEvent).
