---
title: Canais de comunicação
seo-title: Canais de comunicação
description: Canais de comunicação
seo-description: null
page-status-flag: never-activated
uuid: 42975431-64c9-4ecb-98ed-b1f9b13c157e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 2e2d1134-9b83-4ada-b74f-c3842a0cf044
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 3641e438784d40aa097f8c89ca19bdbb52f4bc7d

---


# Canais de comunicação{#communication-channels}

Com o Adobe Campaign, você pode enviar campanhas multicanal, incluindo emails, SMS, mensagens pelo LINE, notificações por push e mala direta, e medir sua eficácia usando vários [relatórios](../../reporting/using/delivery-reports.md)dedicados. Essas mensagens são projetadas e enviadas por deliveries, além disso podem ser personalizadas para cada recipient.

As funcionalidades principais incluem definição de metas, definição e personalização de mensagens, execução de comunicações e relatórios operacionais associados. O principal ponto de acesso funcional é o assistente de delivery. Esse ponto de acesso leva a vários recursos cobertos pelo Adobe Campaign.

>[!NOTE]
>
>O Adobe Campaign oferece um conjunto de ferramentas para monitorar sua capacidade de delivery e otimizar o envio de emails. Para obter mais informações, consulte a [Introdução à capacidade de delivery](https://docs.adobe.com/content/help/pt-BR/campaign-classic/using/sending-messages/deliverability-management/about-deliverability.html) e [Gerenciamento de capacidade de delivery](../../delivery/using/about-deliverability.md).

O envio de deliveries pode ser automatizado preparando-se um delivery e/ou enviando-o no processo de um workflow. Para obter mais informações sobre atividades do tipo delivery em workflows, consulte [esta seção](../../workflow/using/about-action-activities.md).

O Adobe Campaign oferece os seguintes canais de entrega:

1. **Canal de email**: deliveries de email permitem enviar emails personalizados para a população do target. Consulte [Sobre o canal de email](../../delivery/using/about-email-channel.md).
1. **Canal de mala direta**: deliveries de mala direta permitem gerar um arquivo de extração que contém dados sobre a população do target. Consulte [Sobre o canal de correspondência direta](../../delivery/using/about-direct-mail-channel.md)
1. **Canal móvel**: deliveries em canais móveis permitem enviar mensagens SMS ou por LINE personalizadas para a população do target. Consulte [Canal de SMS](../../delivery/using/sms-channel.md).
1. **Canal de aplicativo móvel**: os deliveries por aplicativo móvel permitem enviar as notificações para sistemas iOs e Android. Consulte o capítulo do [Canal de aplicativo móvel](../../delivery/using/about-mobile-app-channel.md) .

   Outros canais são descritos [nesta página](../../delivery/using/other-channels.md).

   >[!NOTE]
   >
   >O uso de vários canais vai depender do seu pacote. Verifique o contrato de licença.

Os deliveries podem ser realizados **online** (via email, um dos canais móveis e notificações por push) e **offline** (canal de mala direta).

Dependendo do canal, os modos de delivery poderão ser:

* Delivery direta em massa via Adobe Campaign (modo padrão para canal de email).
* Delivery externo por meio de um operador especialista que recebe o arquivo de saída gerado pelo assistente de delivery (modo padrão para o canal de mala direta).

As contas externas são configuradas por meio do nó **[!UICONTROL Administration > Platform > External accounts]**. Essa configuração deve ser executada somente por usuários expert.

## Deliveries de email {#email-deliveries}

O [Canal de email](../../delivery/using/about-email-channel.md) é um dos canais principais do Adobe Campaign, permitindo agendar e enviar emails personalizados para targets específicos.

Você pode enviar diferentes tipos de emails:

* Emails de envio único: emails que você pode enviar uma vez para um target definido. Normalmente, eles são usados para promover um conteúdo específico que seria preparado e enviado apenas uma vez (boletim informativo, email promocional etc.).
* Emails recorrentes: em uma campanha, envie o mesmo email regularmente e agregue cada envio e seus relatórios periodicamente. O mesmo email é enviado, mas geralmente para um target diferente, com base no target qualificado do dia do envio. Um exemplo comum é um email de aniversário. Para obter mais informações, consulte [Deliveires recorrentes](../../workflow/using/recurring-delivery.md).
* Emails transacionais: emails unitários que são acionados com base no comportamento dos clientes. Consulte [Mensagens transacionais](../../message-center/using/about-transactional-messaging.md).

Para saber mais sobre o uso de delivery e recomendações, consulte [Práticas recomendadas de Delivery](https://helpx.adobe.com/br/campaign/kb/delivery-best-practices.html) de campanha .

Para obter mais informações sobre tipos diferentes de entrega, consulte [esta página](../../delivery/using/types-of-deliveries.md).

## Deliveries móveis {#mobile-deliveries}

O Adobe Campaign permite que você faça deliveires de mensagens por [SMS](../../delivery/using/sms-channel.md) e [LINE](../../delivery/using/line-channel.md) em celulares.

Para mensagens SMS, você poderá criar, modificar e personalizar mensagens somente no formato de texto. Você também poderá visualizar suas mensagens SMS antes de enviá-las.

Para mensagens por LINE, você poderá enviar texto ou imagens e links.

Para fazer delivery de mensagens SMS ou LINE a um celular, você vai precisar de:

* Uma conta externa configurada no canal **[!UICONTROL Mobile (SMS)]** ou no canal **[!UICONTROL LINE]**.
* Um template de delivery por SMS ou LINE que esteja vinculado corretamente a essa conta externa.

## Notificações por push {#push-notifications}

O Adobe Campaign permite enviar [notificações por push](../../delivery/using/about-mobile-app-channel.md) personalizadas e segmentadas em dispositivos móveis iOS e Android, por meio de aplicativos dedicados. Depois que as etapas de configuração e integração forem executadas, os deliveries do iOS e do Android poderão ser criados e enviados. Você também poderá criar notificações avançadas com imagens ou vídeos.

## Correspondência direta {#direct-mail}

A [mala direta](../../delivery/using/about-direct-mail-channel.md) é um canal offline que permite personalizar e gerar o arquivo exigido por provedores de mala direta. Ela oferece a possibilidade de misturar canais online e offline nas jornadas do cliente.

Os canais online permitem que você crie mensagens (email, SMS, delivery de aplicativo móvel, etc.) e envie-as para seu público diretamente do Adobe Campaign. Com canais offline, é diferente. Quando você prepara um delivery direto de mala direta, o Adobe Campaign gera um arquivo incluindo todos os perfis do target e as informações de contato escolhidas (endereço postal por exemplo). Você poderá enviar esse arquivo para seu provedor de mala direta que irá cuidar realmente do envio.
